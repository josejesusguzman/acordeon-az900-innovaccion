# Tutorial y comandos de acceso para Kubernetes

## Herramientas a utilizar
- [Visual Studio Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/downloads)
- [(Solo Windows) Subsistema de Windows 10 para Linux (hasta el paso 5)](https://docs.microsoft.com/es-mx/windows/wsl/install-win10#step-1---enable-the-windows-subsystem-for-linux)
- [Docker](https://www.docker.com/get-started)
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)

**Nota:** todo el software tiene versión para Windows, Linux y Mac OS.

---------------------------------------


- *Solo Innovacción: [Link de la clase](https://web.microsoftstream.com/video/61dac7dd-db01-40cc-bf3e-6c4798bf015e?st=1990)*

¿No sabes que es Docker y Kubernetes (K8s)? Da clic aquí :point_right: [Video de Kubernetes](https://youtu.be/oTf0KxK1QNo)

- [Ruta de aprendizaje de Azure Kubernetes Services (AKS)](https://docs.microsoft.com/en-us/learn/paths/intro-to-kubernetes-on-azure/)

---------------------------------------

## Comandos y pasos a seguir

1. Después de haber instalado Azure CLI debes hacer *login* con el siguiente comando:
~~~
az login
~~~
Te redigirá a la página de Azure para que inicies sesión. Debes tener una suscrpción activa de Microsoft Azure.

2. Instala los comandos de Kubernetes en el CLI de Azure
~~~
az aks install-cli
~~~

3. Clona el repositorio en tu computadora con el siguiente comando:
~~~
git clone https://github.com/Azure-Samples/azure-voting-app-redis.git
cd azure-voting-app-redis
~~~
Al clonar un repositorio, estas haciendo una copia local de todo el código dentro de una carpeta de tu equipo. Se seleccionó este porque ya tiene varios archivos de configuración requeridos para trabajar con docker.

El comando CD te posiciona en la carpeta que se creo del repositorio. Puedes cambiar el nombre de la carpeta que se crea al clonar poniendo un espacio después del link de GitHub y colocando el nombre de la nueva carpeta. Por ejemplo:
~~~
git clone https://github.com/Azure-Samples/azure-voting-app-redis.git reto-innovaccion
~~~
**Tip: Trata de que tus nombres de carpeta y archivos no tengan espacios, usa guiones o masyúsculas para separar palabras.**


4. Después de clonar tu repositorio, construye el proyecto e instalalo en un Docker local (en tu computadora) con el siguiente comando.
~~~
docker-compose up -d
~~~
- Puedes corroborar el status de tus contenedores desde la interfaz del cliente de Docker:


![Docker en Windows](/res/images/docker-screenshot.png)

- Desde la terminal con el siguiente comando:
~~~
docker ps
~~~

- Para ver que imagenes de Docker tienes instaladas
~~~
docker images
~~~

- Para corroborar que esta funcionando lo que acabas de hacer, ve a [http://localhost:8080](http://localhost:8080)

- Y para detener la ejecución del contenedor usas:
~~~
docker-compose down
~~~

## Creación de los recursos necesarios y subir a Azure

Voy a usar las siguientes "variables" en las cuales tu vas a remplazar con lo que corresponde en tu implementación.

- **GRUPO_DE_RECURSOS** = El grupo de recursos donde pondremos nuestras soluciones de Azure
- **NOMBRE_RECURSO_CONTENEDOR** = Como nombraremos a nuestro recurso Azure Container Registry (ACR)
- **ACR_LOGIN_SERVER** = El link de *login* de nuestro contenedor en Azure (lo obtendremos más tarde)

1. Creas un grupo de recursos de Azure
~~~
az group create --name GRUPO_DE_RECURSOS --location eastus
~~~
En la palabra en mayúsculas iría el nombre que le quieras poner a tu grupo de recursos.

2. Creas el recurso ACR en plan básico
~~~
az acr create --resource-group GRUPO_DE_RECURSOS --name NOMBRE_RECURSO_CONTENEDOR --sku Basic
~~~

3. Haces *login* en el recurso que acabas de crear para controlarlo remotamente. 
~~~
az acr login --name NOMBRE_RECURSO_CONTENEDOR
~~~
**Nota**: Usa tus credenciales de Azure que pusiste en el primer paso del tutorial.

4. Obtienes el ACR_LOGIN_SERVER
~~~
az acr list --resource-group GRUPO_DE_RECURSOS --query "[].{acrLoginServer:loginServer}" --output table
~~~
**Nota**: Te aparecerán todos los *Login Server* de tu grupo de recursos si es que tienes más.

5. Creamos un tag de Docker
~~~
docker tag mcr.microsoft.com/azuredocs/azure-vote-front:v1 ACR_LOGIN_SERVER/azure-vote-front:v1
~~~
Este Tag es necesario para el versionamiento de nuestra solución y porque para subir la solución a Azure nos pide un TAG.

**Nota**: Debes cambiar el v1 que aparece hasta el final de ambas partes del comando por el que corresponda. Puedes ver la versión usando el comando `docker images`

6. Subimos la solución a nuestro ACR en la nube
~~~
docker push ACR_LOGIN_SERVER/azure-vote-front:v1
~~~
**Nota**: igual debe coincidir la versión con la del TAG que acabas de crear.

- Podemos comprobar si se subio exitosamente ya que veremos el nombre de nuestra solución después de ejecutar el siguienet comando:
~~~
az acr repository list --name NOMBRE_RECURSO_CONTENEDOR --output table
~~~

- Y la versión con este otro comando:
~~~
az acr repository show-tags --name NOMBRE_RECURSO_CONTENEDOR --repository NOMBRE_SOLUCIÓN --output table
~~~
**NOMBRE_SOLUCIÓN**: Hace referencia al nombre de nuestra solución que arrojó el comando anterior.

## Creación e immplementación del Kubernetes

1. Creamos el Kubernetes con el siguiente comando

En este punto vamos a agregar una nueva variable.
- **NOMBRE_RECURSO_K8S** = Como nombraremos a nuestro recurso Azure Kubernetes Service (AKS)

~~~
az aks create \
    --resource-group GRUPO_DE_RECURSOS \
    --name NOMBRE_RECURSO_K8S \
    --node-count 2 \
    --generate-ssh-keys \
    --attach-acr NOMBRE_RECURSO_CONTENEDOR
~~~
Este comando crea un servicio de AKS con dos nodos y le adjuntamos de nuestro ACR previamente creado.

:book: **Nodo**: Un nodo es una máquina de trabajo en Kubernetes, previamente conocida como minion. Un nodo puede ser una máquina virtual o física, dependiendo del tipo de clúster.

2. Haces *login* en el AKS para controlarlo por terminal
~~~
az aks get-credentials --resource-group GRUPO_DE_RECURSOS --name NOMBRE_RECURSO_K8S
~~~

- Puedes corroborar que los nodos se encuentren funcionando con siguiente comando:
~~~
kubectl get nodes
~~~
**Nota**: no es necesario especificar a que recurso AKS noes referimos ya que con el comando anterior le decimos a Azure CLI cual queremos controlar.

3. Vas a modificar le código del archivo **azure-vote-all-in-one-redis.yaml**

Vas a encontrar estas lineas de código:
~~~
containers:
- name: azure-vote-front
  image: mcr.microsoft.com/azuredocs/azure-vote-front:v1
~~~

Y lo vas a remplazar por esto:
~~~
containers:
- name: azure-vote-front
  image: ACR_LOGIN_SERVER.azurecr.io/azure-vote-front:v1
~~~

**Nota**: Es muy importante que respetes los espacios y la identación de dos espacios del archivo ya que un error en esto lanzará un error al tratar de construir los contenedores.

4. Hacemos el *deploy* de la aplicación en el AKS
~~~
kubectl apply -f azure-vote-all-in-one-redis.yaml
~~~

Esperas unos minutos a que todo se instale y listo. Si de inmediato te aparece un error, espera unos cinco minutos para que ya puedas ver tu página.

Te debe aparecer algo así:
![Pantallazo Solución](/res/images/azure-vote.png)

Para acceder, tienes que hacerlo desde el navegador poniendo la IP pública en la barra de direcciones.

5. Para obtener la dirección IP pública de la solución ejecutas el siguiente comando:
~~~
kubectl get service azure-vote-front --watch
~~~

Te dará algo similar a esto:
```console
azure-vote-front   LoadBalancer   10.0.34.242   ->52.179.23.131<-   80:30676/TCP   67s
```
La IP pública es el valor de la cuarta columna de izquierda a derecha
**Nota**: Las flechas no aparecerán, las agregué con fines demostrativos.
**Nota**: También puedes obtener la dirección IP desde el recurso de IP pública que se creó automaticamente junto con el AKS. Esto también lo puedes ver en portal.azure.com

## Control y administración de Kubernetes
Una de las ventajas de usar Kubernetes es que puedes escalar tu aplicación o hacerla más pequeña de manera sencilla. Con solo un comando puees crear replicas exactamente iguales de tus contenedores con aplicación y todo.

:book: **Pod**: Los pods son los objetos más pequeños y básicos que se pueden implementar en Kubernetes. Un pod representa una instancia única de un proceso en ejecución en tu clúster.

- Para escalar los pods utilizas este comando:
~~~
kubectl scale --replicas=5 deployment/azure-vote-front
~~~

- Para comprobar el escalamiento ejecutas el siguiente comando:
~~~
kubectl get pods
~~~

Y el resultado debe ser algo similar a esto:
```console
kubectl get pods

                                    READY     STATUS    RESTARTS   AGE
azure-vote-back-2606967446-nmpcf    1/1       Running   0          15m
azure-vote-front-3309479140-2hfh0   1/1       Running   0          3m
azure-vote-front-3309479140-bzt05   1/1       Running   0          3m
azure-vote-front-3309479140-fvcvm   1/1       Running   0          3m
azure-vote-front-3309479140-hrbf2   1/1       Running   0          15m
azure-vote-front-3309479140-qphz8   1/1       Running   0          3m
```
Este comando también te sirve para saber el status de tus pods al momento de su ejecución.

- También puedes escalar los nodos del AKS con el siguiente comando
~~~
az aks scale --resource-group GRUPO_DE_RECURSOS --name NOMBRE_RECURSO_K8S --node-count 3
~~~
Después de `docker images`, va el número de nodos que necesites agregar.

**Nota**: Mientras más pods y más nodos ejecutandose a la vez tengas, más se elevará tu factura de Azure.

Si quieres aprender más de Kubernetes consulta la [documentación oficial](https://kubernetes.io/es/)