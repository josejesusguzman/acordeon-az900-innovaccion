# Comparativa entre los servicios de Cognitive Services

- **[Experimenta la IA de primera mano](https://aidemos.microsoft.com/)**
- [Blog de cognitive services](https://azure.microsoft.com/es-mx/blog/topics/cognitive-services/)

Azure Cognitive Services son servicios basados en la nube con API REST y SDK de biblioteca cliente disponibles para ayudarle a integrar inteligencia cognitiva en sus aplicaciones. Puede agregar características cognitivas a sus aplicaciones sin tener conocimientos sobre inteligencia artificial (IA) o ciencia de datos.

Los Cognitive Services se dividen en cinco categorias:

 - [Visión](#visi%C3%B3n)
 - [Voz](#voz)
 - [Idioma](#idioma)
 - [Decisión](#decisi%C3%B3n)
 - [Search](#search)
 - [Definiciones](#definiciones)

---------------------------------

## Visión

Servicio | Descripción | Ejemplo de uso
-------- | ----------- | -----------
**Computer Vision** | Proporciona acceso a algoritmos avanzados que procesan imágenes y devuelven información basada en las características visuales de interés. | Se puede usar para agrupar imagenes basadas en logos, caras, objetos, colores y brindar las leyendas para las imagenes.
**Custom Vision** | Servicio de reconocimiento de imágenes que permite crear, implementar y mejorar sus propios identificadores de imágenes. Un identificador de imágenes aplica etiquetas (que representan clases u objetos) a las imágenes, en función de sus características visuales. | Se usa para que entrenes a la IA con tus propias imagenes de manera rápida y sencilla. Por ejemplo, defectos en la linea de producción.
**Face** | Proporciona acceso a algoritmos faciales avanzados, lo que permite la detección y el reconocimiento de atributos faciales. | Detectar rostros en una imagen, etiquetar personas, saber donde se encuentran las caras en la imagen, identificar una cara especifica o grupos de personas.
**Form Recognizer** | Identifica y extrae pares clave-valor y datos de tabla de documentos de formulario; luego, genera datos estructurados, incluidas las relaciones en el archivo original. | Analizar facturas, documentos de identidad (IFE), tarjetas de presentación o crear modelos personalizados para los formularios
**Video Indexer** | Permte extraer información de un video. Solución de IA de Azure Media Services y parte de la marca Azure Cognitive Service. Proporciona la capacidad de extraer información profunda (sin necesidad de análisis de datos o conocimientos de codificación) mediante el uso de modelos de Machine Learning basados en varios canales (voz, voces y objeto visual). Los modelos se pueden personalizar y entrenar aún más. | Hacer que el video este disponivle para personas con discapacidad, indexar videos por palabras o caras para mejores busquedas o hacer un sistema de recomendaciones para los usuarios

---------------------------------

## Voz

Servicio | Descripción | Ejemplo de uso
-------- | ----------- | -----------
**Servicio de voz** | Agrega a las aplicaciones características habilitadas por voz. El servicio Voz incluye varias funciones, entre otras: voz a texto, texto a voz y traducción de voz. | Con este puedes convertir voz a texto y visceversa, traducir voz o crear un asistente virtual

Dentro del servicio de Speech puedes encontrar las siguientes subcategorias:

### Voz a Texto
**Permite:**
Caracteristica | SDK* | API*
-------- | ----------- | -----------
Conversión de voz en texto en tiempo real ([Uso de LUIS](https://docs.microsoft.com/es-mx/azure/cognitive-services/luis/what-is-luis)) | [Sí](https://docs.microsoft.com/es-mx/azure/cognitive-services/speech-service/speech-sdk) | [Sí](https://docs.microsoft.com/es-mx/azure/cognitive-services/speech-service/overview#reference-docs)
Conversión de voz en texto por lotes | No | [Sí](https://westus.dev.cognitive.microsoft.com/docs/services/speech-to-text-api-v3-0)
Conversación entre varios dispositivos | Sí | No
Transcripción de conversaciones| Sí | No
Creación de modelos de habla personalizada| No | [Sí](https://westus.dev.cognitive.microsoft.com/docs/services/speech-to-text-api-v3-0)

### Texto a Voz
**Permite:**
Caracteristica | SDK* | API*
-------- | ----------- | -----------
Texto a voz	 | [Sí](https://docs.microsoft.com/es-mx/azure/cognitive-services/speech-service/speech-sdk) | [Sí](https://docs.microsoft.com/es-mx/azure/cognitive-services/speech-service/overview#reference-docs)
Transcripción de conversaciones| No | [Sí](https://docs.microsoft.com/es-mx/azure/cognitive-services/speech-service/overview#reference-docs)

### Traducción de Voz
La traducción de voz habilita la traducción de voz en varios idiomas en tiempo real en sus aplicaciones, herramientas y dispositivos. Use este servicio para la traducción de voz a voz y voz a texto.	

- [SDK](https://docs.microsoft.com/es-mx/azure/cognitive-services/speech-service/speech-sdk)
- No cuenta con API

### Asistentes de voz
Los asistentes de voz que utilizan el servicio de voz permiten a los desarrolladores crear interfaces de conversación naturales, similares a la humana, para sus aplicaciones y experiencias. El servicio del asistente de voz proporciona una interacción rápida y confiable entre un dispositivo y una implementación de asistente que usa el canal de voz de **Direct Line Speech de Bot Framework** o el servicio integrado de comandos personalizados para la finalización de tareas.	

- [SDK](https://docs.microsoft.com/es-mx/azure/cognitive-services/speech-service/voice-assistants)
- No cuenta con API


### Speaker Recognition
¨Proporciona algoritmos que comprueban e identifican a los hablantes por sus características de voz únicas. Speaker Recognition se usa para responder a la pregunta "¿quién está hablando?".

- Sí cuenta con SDK
- [API](https://docs.microsoft.com/es-es/rest/api/speakerrecognition/)

---------------------------------


## Idioma

Servicio | Descripción | Ejemplo de uso
-------- | ----------- | -----------
**Language Understanding: LUIS** | Es un servicio conversacional de inteligencia artificial basado en la nube que aplica inteligencia de aprendizaje automático personalizado a una conversación o un texto de lenguaje natural de un usuario para predecir el significado global y extraer información pertinente y detallada. | Con LUIS se pueden crear bots conversacionales, para soporte de clientes.
**QnA Maker** | Permite generar un servicio de preguntas y respuestas a partir de contenido semiestructurado. | Creación de bots personalizados de manera muy sencilla
**Text Analytics** | Proporciona procesamiento de lenguaje natural en texto sin formato para el análisis de opiniones, la extracción de frases clave y la detección del idioma. | Puede funcionar muy buen para detectar el sentimiento de un texto o de que trata
**Traductor** | Traductor proporciona la traducción de texto automática casi en tiempo real. | Servicios de traducción
**Lector inmersivo** | El Lector inmersivo agrega a las aplicaciones funcionalidad de comprensión y lectura en pantalla. | Se puede usar para mejorar la comprensión lectora en niños, aprender mejor un idioma o como servicio de dictado para personas con discapacidad visual.

---------------------------------


## Decisión

Servicio | Descripción | Ejemplo de uso
-------- | ----------- | -----------
**Anomaly Detector** | Anomaly Detector permite supervisar y detectar anomalías en datos de series temporales. | Detección de malfuncionamientos en maquinaria o motores con sensores IoT.
**Content Moderator** | Content Moderator proporciona la supervisión de posibles contenidos ofensivos, indeseables y peligrosos. | Evitar que una perosna publique groserias o discursos de odio en una aplicación.
**Metrics Advisor** | Metrics Advisor proporciona una detección de anomalías personalizable en los datos de serie temporal de varios variados y un portal web con todas las características para ayudarle a usar el servicio. | Puede diagnosticar y correlacionar las anomalias en un flujo de trabajo, aplicación, maquina, etc.
**Personalizer** | Personalizer permite elegir la mejor experiencia para mostrar a los usuarios y aprender de su comportamiento en tiempo real. | Mostrare los productos que al usuario más le interesen de un e-commerce.

---------------------------------


## Search

Servicio | Descripción 
-------- | -----------
Bing News Search | Devuelve una lista de artículos de noticias cuya relevancia se ha determinado para la consulta del usuario.
Bing Video Search | Devuelve una lista de vídeos cuya relevancia se ha determinado para la consulta del usuario.
Bing Web Search | Devuelve una lista de resultados de la búsqueda cuya relevancia se ha determinado para la consulta del usuario.
Bing Autosuggest | Permite enviar un término de consulta de búsqueda parcial a Bing y obtener una lista de consultas sugeridas.
Bing Custom Search | Permite crear experiencias de búsqueda a medida de los temas que le interesan.
Bing Entity Search | Devuelve información sobre las entidades que Bing determina que están relacionadas con la consulta del usuario.
Bing Image Search | Devuelve una lista de imágenes cuya relevancia se ha determinado para la consulta del usuario.
Bing Visual Search | Devuelve información sobre una imagen, como imágenes visualmente similares, orígenes de compra de productos encontrados en la imagen y búsquedas relacionadas.
Bing Local Business Search | La API Bing Local Business Search permite que las aplicaciones busquen información de ubicación y contacto sobre las empresas locales en función de las consultas de búsqueda.
Bing Spell Check | Permite realizar correcciones de gramática y ortografía en contexto.

### Cognitive Search
Aunque cognitive Search usa Cognitive Services para algunas tareas, es una tecnología de búsqueda diferente que admite otros escenarios.

Azure Cognitive Search (anteriormente conocido como "Azure Search")  es un servicio de búsqueda en la nube que proporciona a los desarrolladores las API y herramientas necesarias para crear una experiencia de búsqueda de datos enriquecida en un contenido privado y heterogéneo en las aplicaciones web, para aplicaciones móviles y empresariales.

Un servicio de búsqueda se coloca entre los almacenes de datos externos que contienen los datos no indexados y su aplicación cliente que envía solicitudes de consulta a un índice de búsqueda y controla la respuesta. 

![Arq Cognitive Search](/res/images/azure-search-diagram.jpg)

**Algunos usos reocmendados:**
- Consolidación de contenido heterogéneo en un índice de búsqueda privado definido por el usuario.
- Implementación con facilidad de características relacionadas con la búsqueda como relavancia, filtros, autocompletado, etc.
- Transformación de grandes archivos de imagen o texto no diferenciados, o archivos de aplicación almacenados en Azure Blob Storage o Cosmos DB, en documentos JSON que se pueden buscar
- Adición de análisis de texto lingüístico o personalizado.

---------------------------------


## Definiciones

**SDK:** Software Development Kit o kit de desarrollo de software en Español es un conjunyo de herramientas que provee un entorno de trabajo, paquetes o librerias qeu posibilitan crear software o aumentar las capacidades de este.

**API:** Application Programming Interface o interfaz de programación de aplicaciones en Español. Una API es un conjunto de definiciones y protocolos que se utiliza para desarrollar e integrar el software de las aplicaciones. Las API permiten que sus productos y servicios se comuniquen con otros, sin necesidad de saber cómo están implementados.