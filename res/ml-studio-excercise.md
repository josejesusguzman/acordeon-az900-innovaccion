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


10. Para la instancia de proceso si ya no la usarás ya que son máquinas virtales

![Captura Notebooks 4](/res/images/tutorial-ml/tutorial-ml-stop-vm.jpg)




## Carga de un dataset y entrenamiento con el mismo

1. Ahora creamos un Cluster de Proceso

![Captura Cluster](/res/images/tutorial-ml/tutorial-ml-cluster-creation1.jpg)

![Captura Cluster 2](/res/images/tutorial-ml/tutorial-ml-cluster-creation2.jpg)

- **En la siguiente ventana**

  - Colocamos un nombre al proceso
  - Número mímino de nodos: 0
  - Número máximo de nodos: 2 (1 si la suscripción o la cuota no te lo permite)
  - Deshabilitado el acceso SSH


2. Descarga el siguiente archivo CSV que usaremos para crear uestro dataset
    https://aka.ms/diabetes-data

3. Ve al apartado de conjuntos de datos (Datasets) y crea uno

![Captura Datasets 1](/res/images/tutorial-ml/tutorial-ml-datasets1.jpg)


