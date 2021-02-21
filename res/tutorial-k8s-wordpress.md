# Tutorial de Wordpress copn Kubernetes

Para ver el tutorial introductorio y que instalar, checa este video:
- [Tutorial básico de Kubernetes y contenedores](/res/tutorial-k8s-wordpress.md)
- [Video tutorial](https://web.microsoftstream.com/video/380105ad-3a67-4134-8acd-608bbb5bacc3)

## Contenido de los archivos

**IMPORTANTE**
Dentro de la carpeta de wordpress que después renombras como public, remplaza el nombre del archivo `wp-config-sample.php` por `wp-config.php` y remplaza solo las lineas que corresponden a ese archivo con esto:

```PHP
//Using environment variables for DB connection information

// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */

$connectstr_dbhost = getenv('DATABASE_HOST');
$connectstr_dbusername = getenv('DATABASE_USERNAME');
$connectstr_dbpassword = getenv('DATABASE_PASSWORD');

/** MySQL database name */
define('DB_NAME', 'flexibleserverdb');

/** MySQL database username */
define('DB_USER', $connectstr_dbusername);

/** MySQL database password */
define('DB_PASSWORD',$connectstr_dbpassword);

/** MySQL hostname */
define('DB_HOST', $connectstr_dbhost);

/** Database Charset to use in creating database tables. */
define('DB_CHARSET', 'utf8');

/** The Database Collate type. Don't change this if in doubt. */
define('DB_COLLATE', '');


/** SSL*/
define('MYSQL_CLIENT_FLAGS', MYSQLI_CLIENT_SSL);
```

**Dockerfile**
```docker

FROM php:7.2-apache
COPY public/ /var/www/html/
RUN docker-php-ext-install mysqli
RUN docker-php-ext-enable mysqli
```

**Archivo mywordpress.yaml**
```YAML
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordpress-blog
spec:
  replicas: 1
  selector:
    matchLabels:
      app: wordpress-blog
  template:
    metadata:
      labels:
        app: wordpress-blog
    spec:
      containers:
      - name: wordpress-blog
        image: ACR_LOGIN_SERVER/NOMBRE_SOLUCION:VERSION_SOLUCION
        ports:
        - containerPort: 80
        env:
        - name: DATABASE_HOST
          value: "SERVER_BASE_DE_DATOS"
        - name: DATABASE_USERNAME
          value: "USUARIO_BASE_DE_DATOS"
        - name: DATABASE_PASSWORD
          value: "PASSWORD_BASE_DE_DATOS"
        - name: DATABASE_NAME
          value: "NOMBRE_BASE_DE_DATOS"
      affinity:
        podAntiAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            - labelSelector:
                matchExpressions:
                  - key: "app"
                    operator: In
                    values:
                    - wordpress-blog
              topologyKey: "kubernetes.io/hostname"
---
apiVersion: v1
kind: Service
metadata:
  name: php-svc
spec:
  type: LoadBalancer
  ports:
    - port: 80
  selector:
    app: wordpress-blog
```
**Nota**: remplaza lo que esta en mayúsculas en los valores de `value` e `image` con lo que corresponda en tu caso.

## Comandos

- Para conectarte a la base de datos de MySQL
```
mysql --host=SERVER_DATABASE --user=USUARIO_BASE_DE_DATOS -p
```
**Nota**: Después de este comando te pedirá la contraseña que pusiste al crear el recurso Azure Database foy MySQL.

- Para construir la imagen de docker y posteriormente subirla.
```
docker build --tag myblog:latest .
```
**Nota**: puedes cambiar `myblog:latest` por el nombre de imagen de docker y la versión que quieras.

- Creación del recurso Azure Container Registry (ACR)
```
acr create --resource-group NOMBRE_GRUPO_RECURSO --name NOMBRE_ACR --sku Basic
```

- Creación del recurso de Azure Kubernetes Service (AKS)
```
az aks create --resource-group NOMBRE_GRUPO_RECURSO --name NOMBRE_AKS --node-count 2 --generate-ssh-keys
```

- Login en el recurso ACR (se debe hacer desde Azure CLI para desktop)
```
az acr login --name NOMBRE_ACR
```

- Login en el recurso AKS (se debe hacer desde Azure CLI para desktop)
```
az aks get-credentials --resource-group NOMBRE_GRUPO_RECURSO --name NOMBRE_AKS 
```

- Creación de un tag de docker para subirlo después
```
docker tag myblog:latest ACR_LOGIN_SERVER/wordpress-blog:latest
```
**Nota**: `myblog:latest` lo debes cambiar por el que hayas puesto al ejecutar el comando `docker build` y puedes cambiar `wordpress:latest` por el que desees.

- Subir la imagen de docker al ACR en la nube
```
docker push ACR_LOGIN_SERVER/wordpress-blog:latest
```
**Nota**: Cambia `wordpress-blog:latest` por el que pusiste en el comando `docker tag`.

- Adjuntar el ACR al servicio de Kubernetes
```
az aks update -n myAKSCluster -g NOMBRE_GRUPO_RECURSO --attach-acr NOMBRE_ACR
```

- Ejecutar todo lo que este en el archivo YAML y que wordpress comience a instalarlo
```
kubectl apply -f mywordpress.yaml
```





