# Comparativa entre Azure Sentinel y Azure Sphere

 - **Azure Sentinel**: Monitoreo, administración, análisis y detección de amanezas de seguridad **en tus soluciones en la nube**
 - **Azure Sphere**: Seguridad en tiempo real para dispositivos del **Internet de las cosas (IoT)**

Servicio | Descripción | Ejemplo de uso
-------- | ----------- | -----------
**[Azure Sentinel](#azure-sentinel)** | Una solución de administración de eventos de información de seguridad (SIEM) y respuesta automatizada de orquestación de seguridad (SOAR) que es escalable y nativa de la nube. | Con este puedes monitorear posibles ataques informáticos (hackeos) en tus soluciones o páginas.
**[Azure Sphere](#azure-sphere)** | Plataforma de aplicaciones segura y de alto nivel con características de comunicación y seguridad integradas para dispositivos conectados a Internet. | Para proteger la comunicación entre Azure y un sistema de cámaras de seguridad.

**Indice**
<!-- TOC -->

- [Comparativa entre Azure Sentinel y Azure Sphere](#comparativa-entre-azure-sentinel-y-azure-sphere)
  - [Azure Sentinel](#azure-sentinel)
    - [Conexión con datos](#conexión-con-datos)
    - [Workbooks (Libros)](#workbooks-libros)
    - [Análisis](#análisis)
    - [Investigación](#investigación)
  - [Azure Sphere](#azure-sphere)
    - [Ejemplo de lavaplatos conectado a la red](#ejemplo-de-lavaplatos-conectado-a-la-red)
    - [Las siete propiedades de dispositivos muy protegidos](#las-siete-propiedades-de-dispositivos-muy-protegidos)
    - [Arquitectura de hardware de Azure Sphere](#arquitectura-de-hardware-de-azure-sphere)

<!-- /TOC -->

________

## Azure Sentinel
![Logo Azure Sentinel](/res/images/azure-sentinel.png)

 - **Administración de eventos de información de seguridad (SIEM)**: Sistema que detecta fallos y amanezas de seguridad reconociento los patrones de ataques de seguridad anteriores.
- **Respuesta automatizada de orquestación de seguridad (SOAR)**: Hace referencia a la gestión de casos y flujos de trabajo, la automatización de tareas y un medio centralizado para acceder a la información sobre las amenazas, realizar consultas y compartir dicha información. Mejora y automatiza la respuesta a ataques de seguridad.

Azure Sentinel ofrece análisis de seguridad inteligente e inteligencia frente a amenazas en toda la empresa, de forma que proporciona una única solución para la detección de alertas, la visibilidad de amenazas, la búsqueda proactiva y la respuesta a amenazas.


Azure Sentinel incorpora de forma nativa bases contrastadas, como **Log Analytics** y **Logic Apps**. Además, enriquece la investigación y la detección con AI al proporcionar el flujo de inteligencia de amenazas de Microsoft y permitirle aportar su propia inteligencia de amenazas.

![Explain Azure Sentinel](/res/images/sentinel-capabilities.png)


### Conexión con datos
Para incorporar Azure Sentinel, primero debes conectarte a  orígenes de seguridad. Sentinel incluye varios conectores para soluciones de Microsoft, que están disponibles inmediatamente y proporcionan integración en tiempo real, entre las que se incluyen las soluciones de **Microsoft 365 Defender**(anteriormente, Protección contra amenazas de Microsoft) y orígenes de **Microsoft 365**, incluido Office 365, Azure AD, Microsoft Defender for Identity (anteriormente, Azure ATP) y Microsoft Cloud App Security, entre otros.

### Workbooks (Libros)
Después de conectar los origenes de datos, Sentinel  puede supervisar los datos mediante la integración de Azure Sentinel con los libros de Azure Monitor, lo que proporciona versatilidad al crear libros personalizados. También incluye plantillas de libro integradas.

![Explain Azure Sentinel](/res/images/sentinel-workbooks.png)


### Análisis

Para reducir el ruido y minimizar el número de alertas que tienes que revisar e investigar, Azure Sentinel usa **análisis para correlacionar** las alertas con los incidentes. Los **incidentes** son grupos de alertas relacionadas que, juntas, crean una posible amenaza procesable que se puede investigar y resolver.

### Investigación

Las herramientas de investigación profunda de Azure Sentinel están actualmente en versión preliminar y te ayudan a conocer el ámbito y a encontrar la causa principal de una posible amenaza de seguridad. 

_______

## Azure Sphere
![Logo Azure Sphere](/res/images/azure-sphere.png)

Consta de una unidad de microcontrolador híbrida, protegida y conectada; un sistema operativo (SO) basado en Linux de alto nivel y personalizado, y un servicio de seguridad basado en la nube que proporciona seguridad de forma continua y renovable.

La unidad de microcontrolador de Azure Sphere integra capacidades de procesamiento en tiempo real, además de la capacidad de ejecutar un sistema operativo de alto nivel. Esta unidad de microcontrolador de Azure Sphere, junto con su sistema operativo y plataforma de aplicaciones, permite crear dispositivos protegidos con conexión a Internet que se pueden actualizar, controlar, supervisar y mantener de forma remota. Un dispositivo conectado que incluye un (Unidad de Microcontrolador) MCU de Azure Sphere, ya sea junto con MCU existentes o en lugar de estos, proporciona una seguridad, productividad y oportunidad mejoradas. Por ejemplo:

 - Un entorno de aplicaciones protegido, conexiones autenticadas y uso opcional de periféricos minimizan los riesgos de seguridad debido a suplantación de identidad, software malintencionado o ataques por denegación de servicio, entre otros.
 - Las actualizaciones de software se pueden implementar automáticamente desde la nube en cualquier dispositivo conectado para solucionar problemas, proporcionar nuevas funcionalidades o contrarrestar métodos emergentes de ataque, lo que permite mejorar la productividad del personal de soporte técnico.
 - Los datos de uso de productos se pueden notificar a la nube a través de una conexión segura para ayudar a diagnosticar problemas y diseñar nuevos productos, lo que aumenta la oportunidad de servicio de productos, interacciones positivas con los clientes y desarrollos futuros.

### Ejemplo de lavaplatos conectado a la red

![Example Azure Sentinel](/res/images/lavaplatos-example.png)

Desde la esquina superior izquierda y en el sentido de las manecillas:
- Microsoft publica actualizaciones para el sistema operativo de Azure Sphere a través del servicio de seguridad de Azure Sphere
- La ingeniería de producto de la empresa publica actualizaciones para su aplicación DW100 a través del servicio de seguridad de Azure Sphere
- El servicio de seguridad de Azure Sphere implementa de forma segura el sistema operativo actualizado y el software de la aplicación DW100 en el lavaplatos en las ubicaciones del usuario final
- El lavaplatos de se comunica con el servicio de seguridad de Azure Sphere para determinar qué versión del software de Azure Sphere y del software de aplicación DW100 debe ejecutarse en cada dispositivo del usuario final y recopilar los datos de informe de errores que se notifican al servicio. El lavaplatos de Contoso también se comunica con el servicio en la nube de Contoso para obtener más información
- Los servicios en la nube de  admiten aplicaciones para solucionar problemas, analizar datos e interactuar con el cliente. Los servicios en la nube de Contoso pueden hospedarse en Microsoft Azure, en el servicio en la nube de otro proveedor o en la propia nube de la empresa
- Los modelos DW100 de la empresa en ubicaciones de usuario final descargan el software de la aplicación y el sistema operativo actualizados a través de su conexión al servicio de seguridad de Azure Sphere. También pueden comunicarse con la aplicación de servicio en la nube de la empresa para notificar datos adicionales

### Las siete propiedades de dispositivos muy protegidos
- [Clic para más información](https://docs.microsoft.com/es-mx/azure-sphere/product-overview/what-is-azure-sphere#azure-sphere-and-the-seven-properties-of-highly-secured-devices)

- Raíz de confianza basada en hardware
- Pequeña base informática de confianza
- Defensa en profundidad
- Compartimientos dinámicos
- Autenticación sin contraseña
- Seguridad energética
- Informe de errores

### Arquitectura de hardware de Azure Sphere

Un MCU cruzado de Azure Sphere consta de varios núcleos en una única matriz, como se muestra en la imagen siguiente.

![Grafico Azure Sentinel](/res/images/graphic-mcu-01.png)
