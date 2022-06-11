# Uso y comparativa entre Azure Advisor, Monitor, Sentinel, Service Health y Log Analytics

- **Azure Advisor**: Te da **recomendaciones** para ahorrar costos, mejorar la seguridad , la gobernanza y el rendimiento de tu infraestructura de nube
- **Azure Monitor**: Monitorea y visualiza en tiempo real los datos de **rendimiento** (como uso de memoria o procesamiento) de tu infraestructura de nube
- **Azure Log Analytics**:  se usa para **editar y ejecutar** consultas de registros con los datos de los **registros de Azure Monitor**.
- **Azure Sentinel**: Monitoreo, administración, análisis y detección de amanezas de **seguridad** en tus soluciones en la nube
- **Azure Service Health**: Monitorea y te notifica del **status de los servicios** de Microsoft a nivel global o por región
  - [Accede a la página de Estado de Azure](https://status.azure.com/es-es/status)

**Indice**
<!-- TOC -->

- [Uso y comparativa entre Azure Advisor, Monitir, Sentinel, Service Health y Log Analytics](#uso-y-comparativa-entre-azure-advisor-monitir-sentinel-service-health-y-log-analytics)
  - [Azure Advisor](#azure-advisor)
    - [¿Cómo funciona Advisor?](#cómo-funciona-advisor)
    - [Puntuación de Advisor](#puntuación-de-advisor)
  - [Azure Monitor](#azure-monitor)
    - [Datos que recopila Azure Monitor](#datos-que-recopila-azure-monitor)
    - [Diferencia con Azure Log Analytics](#diferencia-con-azure-log-analytics)
  - [Azure Log Analytics](#azure-log-analytics)
  - [Azure Sentinel](#azure-sentinel)
  - [Azure Service Health](#azure-service-health)
    - [Estado de Azure (Azure Status)](#estado-de-azure-azure-status)
    - [Service Health](#service-health)
    - [Resourse Health](#resourse-health)

<!-- /TOC -->

Servicio | Descripción | Ejemplo de uso
-------- | ----------- | -----------
**[Azure Advisor](#azure-advisor)** | Servicio gratuito integrado en Azure que proporciona procedimientos recomendados para las cargas de trabajo. Las recomendaciones que ofrece son personalizadas y accionables. | Te puede **recomendar** reducir el tamaño de una maquina virtual ya que no usamos tanto poder de procesamiento y así ahorrar costos.
**[Azure Monitor](#azure-monitor)** | Plataforma que permite recopilar, analizar y mostrar datos, así como llevar a cabo acciones en función de las métricas y los datos registrados en todo el entorno local y de Azure. | Cuando hay una **falla en una página web**, Azure Monitor te puede informar de la **causa** de la falla y te permite **reiniciar** la solución.
**[Azure Log Analytics](#azure-log-analytics)** | Log Analytics es una herramienta de Azure Portal que se usa para editar y ejecutar consultas de registros con los datos de los registros de Azure Monitor. Puedes escribir una consulta sencilla que devuelva un conjunto de registros y, a continuación, utilizar las características de Log Analytics para ordenarlos, filtrarlos y analizarlos. | Podría ayudarte a detectar fallas en las que intervengan más de un servicio de Azure y determinar de manera más sencilla las causas.
**[Azure Sentinel](#azure-sentinel)** | Una solución de administración de eventos de información de seguridad (SIEM) y respuesta automatizada de orquestación de seguridad (SOAR) que es escalable y nativa de la nube. | Con este puedes monitorear posibles ataques informáticos (hackeos) o intruciones en tus soluciones o páginas.
**[Azure Service Health](#azure-service-health)** | Servicio de administración y monitoreo de servicios de Microsoft a nivel global o por región. Informa de fallas o mantenimientos programados de los servic los de Azure | Puede servirte para enterarte de futuros mantenimientos programados de los servicios que usas y así poder anticipar la acción a realizar.

_______________________________________

## Azure Advisor
![Logo Azure Advisor](/res/images/advisor.jpg)

Azure Advisor analiza de forma continua los recursos y el uso en la nube. Después, recomienda soluciones que pueden ayudarte a mejorar las cargas de trabajo en relación con los cinco pilares Marco de buena arquitectura de Microsoft Azure.

Fundamento | Descripción
-------- | -----------
Optimización de costos | Administración de costos para maximizar el valor proporcionado.
Excelencia operativa | Procesos de operaciones que mantienen un sistema ejecutándose en producción.
Eficiencia del rendimiento | La capacidad de un sistema para adaptarse a los cambios en la carga.
Confiabilidad | La capacidad de un sistema de recuperarse de los errores y seguir funcionando.
Seguridad | Protección de las aplicaciones y los datos frente a amenazas.

 - [Consulta más información sobre el Marco de buena arquitectura de Microsoft Azure](https://docs.microsoft.com/es-es/azure/architecture/framework/)

### ¿Cómo funciona Advisor?

Tras analizar la configuración de los recursos y la telemetría de uso, Advisor ofrece recomendaciones útiles que pueden ayudarle a mejorar la rentabilidad, el rendimiento, la confiabilidad y la seguridad de los recursos de Azure, así como la excelencia operativa.

Advisor funciona en el nivel de suscripción y recursos, ya sea de forma agregada o individual. Puede acceder a las recomendaciones de Advisor como propietario, colaborador o lector de una suscripción o recurso. Estos niveles de acceso también se aplican a los asociados que administran recursos de Azure en su nombre.

### Puntuación de Advisor

La puntuación de Advisor es una clasificación de las suscripciones de Azure en una escala del 0 % al 100 %, con la finalidad de ayudarte a comprender el grado de optimización de los recursos de esas suscripciones, en función de los procedimientos recomendados documentados.

_______________________________________

## Azure Monitor

![Logo Azure Monitor](/res/images/monitor.png)


Azure Monitor ayuda a maximizar la disponibilidad y el rendimiento de las aplicaciones y los servicios. Ofrece una solución completa para recopilar, analizar y actuar en la telemetría desde los entornos local y en la nube. Esta información le ayudará a conocer el rendimiento de las aplicaciones y a identificar de manera proactiva los problemas que les afectan y los recursos de los que dependen.

Entre los ejemplos de lo que puede hacer con Azure Monitor se incluyen:
- Detección y diagnóstico de problemas en aplicaciones y dependencias con Application Insights
- Correlación de problemas de infraestructura con VM Insigths y Container Insights
- Profundización en sus datos de supervisión con Log Analytics para la solución de problemas y diagnósticos profundos
- Soporte técnico de operaciones a escala con alertas inteligentes y acciones automatizadas
- Creación de visualizaciones con paneles y libros de Azure
- Recopile datos de los recursos supervisados mediante métricas en Azure Monitor

### Datos que recopila Azure Monitor

Azure Monitor puede recopilar datos de diversos orígenes, como la aplicación y cualquier sistema operativo o servicio en los que se base, o incluso la propia plataforma. Azure Monitor recopila datos de cada uno de los siguientes niveles:

- Datos de supervisión de aplicaciones
- Datos de supervisión del sistema operativo invitado
- Datos de supervisión de recursos de Azure
- Datos de supervisión de la suscripción de Azure
- Datos de supervisión del inquilino de Azure

Azure Monitor también puede recopilar datos de registro de cualquier cliente de REST mediante Data Collector API. Esto permite crear escenarios de supervisión personalizados y ampliar la supervisión a los recursos que no exponen datos de telemetría en otros orígenes.

### Diferencia con Azure Log Analytics
En septiembre de 2018, Microsoft combinó Azure Monitor, Log Analytics y Application Insights en un solo servicio.

El motor de datos de registro y el lenguaje de consulta de Log Analytics se conocen ahora como registros de Azure Monitor.

**Log Analytics usa los registros de Azure Monitor**


_______________________________________

## Azure Log Analytics

![Logo Log Analytics](/res/images/log-analytics.png)


Con Log Analytics escribir una consulta sencilla que devuelva un conjunto de registros y, a continuación, utilizar las características de Log Analytics para ordenarlos, filtrarlos y analizarlos. 

O bien, puedes escribir una consulta más avanzada para realizar análisis estadísticos y visualizar los resultados en un gráfico para identificar una tendencia determinada. Tanto si trabajas con los resultados de las consultas de forma interactiva como si los usas con otras características de Azure Monitor, como las alertas de consultas de registros o los libros, Log Analytics es la herramienta que vas a usar para escribir y probarlos.

_______________________________________

## Azure Sentinel

![Logo Azure Sentinel](/res/images/azure-sentinel.png)

Microsoft Azure Sentinel es una solución de administración de eventos de información de seguridad (SIEM) y respuesta automatizada de orquestación de seguridad (SOAR) que es escalable y nativa de la nube. Azure Sentinel ofrece análisis de seguridad inteligente e inteligencia frente a amenazas en toda la empresa, de forma que proporciona una única solución para la detección de alertas, la visibilidad de amenazas, la búsqueda proactiva y la respuesta a amenazas.

- [Consulta más información de Azure Sentinel](/res/comparativa-sentinel-sphere.md/#azure-sentinel)

_______________________________________

## Azure Service Health

![Logo Azure Service Health](/res/images/service-health.png)

Azure Service Health es una combinación de tres servicios independientes más pequeños.

### Estado de Azure (Azure Status)
- [Accede a la página de Estado de Azure](https://status.azure.com/es-es/status)

Informa de las interrupciones de servicio en Azure. La página es una vista global del estado de todos los servicios y regiones de Azure. La página de estado es una buena referencia para incidentes con un impacto masivo, pero se recomienda a los usuarios de Azure que aprovechen **Azure Service Health** dentro del Portal de Azure para mantenerse informados sobre los incidentes y el mantenimiento de Azure.

### Service Health
Proporciona una vista personalizada del estado de los servicios y regiones de Azure que **estas usando**. Es el mejor lugar para buscar comunicaciones que afecten a los servicios relativas a interrupciones, actividades de mantenimiento planeado y otros avisos de mantenimiento, ya que tras la autenticación, Service Health conoce los servicios y recursos que usa en la actualidad. 

Service Health realiza un seguimiento de cuatro tipos de eventos de estado que pueden afectar a los recursos:

- **Problemas de servicios**: problemas en los servicios de Azure que le afectan ahora mismo.
- **Mantenimiento planeado**: próximas acciones de mantenimiento que pueden afectar a la disponibilidad de los servicios en el futuro.
- **Avisos de estado**: cambios en los servicios de Azure que requieren su atención. Como el desuso de las características de Azure o los requisitos de actualización (por ejemplo, la actualización a un marco PHP compatible).
**Avisos de seguridad**: infracciones o notificaciones relacionadas con la seguridad que pueden afectar a la disponibilidad de los servicios de Azure.

### Resourse Health

Azure Resource Health ayuda a diagnosticar problemas en los servicios que afectan a los recursos de Azure y a obtener soporte técnico para resolverlos. Informa sobre el mantenimiento actual y pasado de los recursos.
