# Ejercicio con Azure Machine Learning Studio

En esta práctica lo que harás será crear un modelo de predicción de diabetes de acuerdo con un dataset brindado. Todo lo harás con el portal de Azure y Machine Learning Studio. Además, aprenderás a usar un poco mejor la plataforma.

## Creación de un recurso de Aprendizaje automático
Para usar Azure Machine Learning Studio necesitamos un recurso de Aprendizaje Automático de Azure que nos proporcionará el área de trabajo y la facturación a nuestra suscripción de Microsoft Azure.

1. Dirigete a portal.azure.com Si te lo pide, inicia sesión
2. Busca el recurso **Aprendizaje automático***

![Busqueda de Azure](/res/images/tutorial-ml/tutorial-ml1.jpg)

3. Configura y crea el recurso
    * No te precupes por los apartados de Cuenta de almacenamiento, Almac{emn de claves o Application Insights ya que se autocompleta.
    * En registro de contenedor deja ninguno
    * Ya puedes darle clic en Revisar y crear

![Formulario de Azure](/res/images/tutorial-ml/tutorial-ml-form-azure.jpg)

4. Espera a que termine de crearse exitosamente, ve a ml.azure.com y selecciona el nombre del recurso que acabas de crear
    * Si no aparece, dale clic en el botón de actualizar del lado derecho de la lista o espera un minuto a que aparezca.

![Selección workspace](/res/images/tutorial-ml/tutorial-ml-select-workspace.jpg)

5. Crea una instancia de cómputo. Guiáte de las capturas de pantalla

![Captura de ML Studio en Proceso](/res/images/tutorial-ml/tutorial-ml-instancia.jpg)

Hay cuatro tipos de recursos de computo que puedes crear:
- **Instancias de cómputo**: estaciones de trabajo de desarrollo que l@s científic@s de datos pueden usar para trabajar con datos y modelos.
- **Clústeres de cómputo**: clústeres escalables de máquinas virtuales para el procesamiento bajo demanda del código del experimento.
- **Clústeres de inferencia**: objetivos de implementación para servicios predictivos que utilizan sus modelos entrenados.
- **Computación adjunta**: vínculos a otros recursos de computación de Azure, como máquinas virtuales o clústeres de Azure Databricks.

![Captura MV 1](/res/images/tutorial-ml/tutorial-ml-creacion-instancia-1.jpg)

- Selecciona una de las máquinas virtuales mostradas (Recuerda cuidar tu crédito de Azure)
- Da clic en siguiente, ponle un nombre al proceso y da clic en Crear

6. Ve al apartado de Notebooks y haz clic en el icono de Terminal para abrir una

![Captura Notebooks](/res/images/tutorial-ml/tutorial-ml-notebooks-terminal.jpg)

7. ejecuta el siguiente comando que clonará un repositorio con practicas en forma de Notebooks

~~~
 git clone https://github.com/MicrosoftLearning/mslearn-dp100
~~~

![Captura Notebooks Term](/res/images/tutorial-ml/tutorial-notebooks-terminal2.jpg)

8. Despliega la carpeta creada (si no aparece después de la ejecución da clic en actualizar). Y entra al Notebook titulado Get Started with Notebooks.

![Captura Notebooks 3](/res/images/tutorial-ml/tutorial-mlnotebook3-exec.jpg)

9. Ejecuta el Notebook ya sea comando por comando o todo el Notebook con el icono de doble Play en la parte superior

![Captura Notebooks 4](/res/images/tutorial-ml/tutorial-ml-notebook-exec1.jpg)

- **Lee todo el Notebook para saber más sobre ellos**
- Este es el resultado esperado:
![Captura Notebooks 4](/res/images/tutorial-ml/tutorial-ml-notebook-exec2.jpg)


10. Deten la instancia de proceso si ya no la usarás ya que son máquinas virtuales y se siguen ejecutando aunque no las uses.

![Captura Notebooks 4](/res/images/tutorial-ml/tutorial-ml-stop-vm.jpg)

______________________________________

## Carga de un dataset y entrenamiento con el mismo

### Creación de un cluster de proceso

1. Ahora creamos un Cluster de Proceso

![Captura Cluster](/res/images/tutorial-ml/tutorial-ml-cluster-creation1.jpg)

![Captura Cluster 2](/res/images/tutorial-ml/tutorial-ml-cluster-creation2.jpg)

- **En la siguiente ventana**

  - Colocamos un nombre al proceso
  - Número mímino de nodos: 0
  - Número máximo de nodos: 2 (1 si la suscripción o la cuota no te lo permite)
  - Deshabilitado el acceso SSH

![Captura Creación de clusteres](/res/images/tutorial-ml/tutorial-ml-datasets1.jpg)

### Creación del Dataset

2. Descarga el siguiente archivo CSV que usaremos para crear uestro dataset
    https://aka.ms/diabetes-data

3. Ve al apartado de conjuntos de datos (Datasets) y crea uno

- Llena el primer formulario con los siguiente datos:
  - Agrega un nombre y descripción a tu dataset
  - Selecciona el **Tipo de conjunto de datos** en Tubular
- En el siguiente formulario **carga** el archivo CSV del paso anterior y dale clic en siguiente
- En el siguiente formulario deja todo como esta y solo cambia lo siguiente:
  - **Encabezados de columna** como **Solo el primer archivo tiene encabezados**
- En el aprtado de esquema deja todos seleccionados excepto Path

![Captura Creación de dataset 4](/res/images/tutorial-ml/tutorial-ml-creacion-dataset-4.jpg)

- Confirma que todo este bien y dale en continuar

### Creación de un experimento

4. Ve al apartado de **ML Automatizado** y dale clic en **Nueva ejecución de ML Automatizado**

![Captura Nueva ejecución ML](/res/images/tutorial-ml/tutorial-ml-ejecucion-ml-automatizado.jpg)

- Selecciona el dataset que acabamos de crear y dale siguiente
- En el siguiente formulario
  - Selecciona la opción de **Crear**
  - Ponle un nombre a tu experimento
  - En **Columna de destino** selecciona **Diabetic (Integer)
  - Selecciona el **Cluster de proceso** previamente creado
- En la sección de **Selección del tipo de tarea** selecciona **Clasificación** (debe aparecer una palomita verde del lado derecho) 
- Da clic en **Ver opciones de configuración adicionales** y replica los valores siguientes y da clic en guardar:

![Captura Nueva ejecución ML 2](/res/images/tutorial-ml/tutorial-ml-ejecucion-ml-automatizado2.jpg)

Esto hace que el **Tiempo de trabajo de entrenamiento** sea de máximo 30 minutos y que el el experimento termine si el modelo alcanza en Valor ponderado de AUC el valor de que pusiste en **Umbral de puntuación de métrica**.

- Después le das clic en **Ver configuración de caracterización** y revisas que **Habilitar catracterización** este encendido

- Da clic en **Finalizar** y espera que termine el experimento

![Captura experimento terminado](/res/images/tutorial-ml/tutorial-ml-experimento-terminado.jpg)

5. Cuando se termine de ejecutar eñ experimento, en la vista de detalalle de la ejecución da clic los algoritmos usados debajo de **Nombre del algoritmo**

![tutorial-ml-detail-results](/res/images/tutorial-ml/tutorial-ml-detail-results.jpg)

6. Revisa las métricas arrojadas por el experimento

![tutorial-ml-metrics](/res/images/tutorial-ml/tutorial-ml-metrics.jpg)

tutorial-ml-metrics

7. Da clic en el botón implementar

- Dale un nombre y una descripción a la implementación del modelo 
- En **Tipo de proceso** selecciona **Instancia de Contenedor de Azure**
- **Habilita la autenticacion**

Estro creará un nuevo **Modelo** junto con un Endpoint o **Punto de conexión** el cual usaremos para conectarnos mediante Notebooks.

8. Ve a la sección de **Puntos de conexión**, selecciona el que recien has creado, ve a la pestaña de **Consumir** y espera a que el **Punto de conexión REST** este disponible (puede tardar unos minutos)

- ML Studio te notificará cuando este listo. Sal y vuelve a entrar a tu Endpoint para actualizarlo y que aparezca la URL

![tutorial-ml-select-endpoint](/res/images/tutorial-ml/tutorial-ml-select-endpoint.jpg)

![tutorial-ml-select-endpoint](/res/images/tutorial-ml/tutorial-ml-rest-keyselect.jpg)

9.  Copia y guarda la URL del **Punto de conexión REST** y la **Clave Principal** o Primary key

10. Ve a la sección **Notebooks**, abre la carpeta **mslearn-dp100** y abre el notebook **02-Get AutoML Prediction**

11.  Coloca la URL del Endpoint como valor de la variable **endpoint** y la Primary Key como valor de la variable **key**

12. Ejecuta el notebook y observa el resultado

13. Si ya no lo vas a ocupar, borra el cluster de proceso

____________

