# Sobre el Cloud Adoption Framework

El Cloud Adoption Framework es una guía que sirve para el recorrido de la implementación de tecnologías de nube en una organización. 

Este marco de trabajo contempla tareas organizacionales, técnicas y de planeación para la correcta migración a la nube.

**Aquí te mostraré los pasos a base de ejemplos, pasos a seguir o entregables posibles.**

- [Descarga aquí todas las plantillas de documentación adaptadas a Microsoft Azure](https://docs.microsoft.com/es-es/azure/cloud-adoption-framework/reference/tools-templates)

## 1 Definir la estrategia.

[Template sugerido para esta etapa](/res/docs/cloud-adoption-framework-strategy-and-plan-template.docx)

### 1.1 Definir y documentar las motivaciones

:book: Reúnase con las partes interesadas clave y la dirección para documentar la motivación que hay detrás de la adopción de la nube.

Algunas posibles motivaciones para migrar a la nube son:
- Ahorros en costos
- Reducción de la complejidad técnica o de proveedores
- Optimización de las operaciones internas
- Aumento de agilidad empresarial
- Preparación para nuevas funcionalidades técnicas
- Escalado para satisfacer demandas del mercado
- Escalado para satisfacer demandas geográficas
- Integración de una cartera de TI compleja

Sin embargo, la organización se puede centrar más en la innovacción como con los siguientes ejemplos:
- Aumento de la agilidad comercial
- Preparación para nuevas funcionalidades técnicas
- Creación de nuevas funcionalidades técnicas
- Escalado para satisfacer demandas del mercado
- Escalado para satisfacer demandas geográficas
- Experiencias de los clientes mejoradas e involucración
- Transformación de productos o servicios

### 1.2 Documentación de los resultados empresariales

:book: Implique a las partes interesadas y a los ejecutivos motivados para que documenten resultados empresariales concretos.

[Plantilla de resultados empresariales](/res/docs/business-outcome-template.xlsx)

Algunos de los resultados emrpesariales esperados por digferenets roles son:

- **Liderazgo financiero**: aumentar la rentabilidad sin perder de vista el cumplimiento
- **Marketing**: lograr nuevos clientes, conservar los conseguidos y crear una reputación
- **Ventas**: acelerar las ventas, mejorar el valor de los clientes
- **Recursos humanos**: conservar, contratar y capacitar a los empleados
- **Liderazgo ejecutivo**: cumplir los requisitos de crecimiento del mercado y las métricas de sostenibilidad medioambiental

Cada rol puede generar entregables y resultados diferentes. Por ejemplo, los resultados fiscales pueden ser las declaraciones de impuestos, proyecciones de ventas, presupuestos, etc.

### 1.3 Desarrollo de un caso empresarial

:book: Desarrolle un caso de negocio para validar el modelo financiero que sea compatible con las motivaciones y los resultados.

Las migraciones a la nube pueden generar una rápida rentabilidad de la inversión (ROI) por los esfuerzos de transformación en la nube.

![ROI](/res/images/roi.jpg)

El ROI puede ser una buena justificación para una migración a la nube ya que determina que cantidad de ingresos y tiempo necesitas para recuperar la inversión hecha.

El costo o inversión inicial puede contemplar:
- Capacitación del equipo
- Costos de la migración
- Costo por tiempo invertido
- Inversión inicial en la nube. Consulta la [calculadora de precios de Azure](https://azure.microsoft.com/es-mx/pricing/calculator/)
  - Diferencia el costo contra un ambiente on-premise con [la calculadora de TCO](https://azure.microsoft.com/es-mx/pricing/tco/calculator/)

### 1.4 Elección adecuada del primer proyecto

:book: El primer proyecto de adopción de la nube le ayudará a alinear las motivaciones con los esfuerzos técnicos. Este artículo puede ayudarle a elegir el primer proyecto de un modo prudente.

Algunos rubros para elegir el proyecto pionero son:

- **Eventos empresariales críticos**: cuando un evento empresarial crítico es la motivación principal, la implementación de una herramienta como Azure Site Recovery podría ser un buen primer proyecto. Durante la migración, usarás una herramienta como Azure Migrate para migrar rápidamente los recursos del centro de datos. Pero durante el primer proyecto, podrás usar primero Azure Site Recovery como herramienta de recuperación ante desastres. Reduzce las dependencias en los recursos de recuperación ante desastres del centro de datos antes de planear pragmáticamente la migración.

- **Motivaciones de migración**: cuando la migración es la motivación principal, es aconsejable empezar con la migración de una carga de trabajo no crítica. En la guía de configuración de Azure y la guía de migración a Azure se proporcionan instrucciones para la migración de la primera carga de trabajo.

- **Motivaciones de innovación**: cuando la innovación es la motivación principal, la creación de un entorno de desarrollo y pruebas de destino puede ser un excelente primer proyecto.

También puedes empezar con proyectos como:
- No productivos o que no estén en ambientes de producción
- Interfaz de escritorio virtual (VDI)
- Desarrollo y pruebas
- Aplicaciones sencillas
- Laboratorios de pruebas

## 2 Creación del plan

### 2.1 Patrimonio digital

:book: Realiza el inventario y racionalización del patrimonio digital según supuestos que se alinean con las motivaciones y resultados empresariales.

1. Requieres de un **inventario** donde contemples completamente los recursos, aplicaciones, software, hardware, sistemas operativos y métricas de rendimiento del sistema.

2. Requieres hacer un **análisis cuantitativo** contestando preguntas como:

- ¿Está el recurso en uso hoy en día?
- Si es así, ¿está optimizado y dimensionado correctamente?
- ¿Qué dependencias existen entre los recursos?

3. **Análisis cualitativo** [Elige un enfoque de los presentados en este documento](https://docs.microsoft.com/es-es/azure/cloud-adoption-framework/digital-estate/approach)

4. **Decisión de racionalización** Usando los tres puntos anteriores, se toma la desición de Rehospedar, Refactorizar, Rediseñar, Volver a generar (Regenerate) o Remplazar los recursos. [Más información de las 5Rs de la racionalización aquí.](https://docs.microsoft.com/es-es/azure/cloud-adoption-framework/digital-estate/5-rs-of-rationalization#the-five-rs-of-rationalization)

### 2.2 Alineación inicial de la organización

:book: Establece un plan para la alineación inicial de la organización que admita el plan de adopción.

En este punto se asignan los recursos humanos y no humanos a las diferentes tareas que tendrá la organización de la nube. Por ejemplo:

- ¿Qué persona completará las tareas técnicas del plan de adopción de la nube?
- ¿Qué persona será responsable de la capacidad del equipo para entregar cambios técnicos?
- ¿Qué persona se encargará de la gobernanza?
- ¿Existen otras funcionalidades o personas que tengan responsabilidad en el plan de adopción de la nube?

### 2.3 Plan de preparación de las aptitudes

:book: Crea un plan para afrontar las carencias en la preparación de las aptitudes.

Para crear este plan necesitas:

1. Detectar y documentar las preocupaciones de cada equipo al adoptar la nube

Por ejemplo, el equipo de TI puede tener preocupaciones por el incremento en su necesidad de capacitación y ahí se incluirían las preferencias de entrenamiento en el plan de preparación.

2. Detección de brechas. Una brecha es un rol, aptitud o proceso necesario para la transformación digital que no existe actualmente en la empresa.

3. Trabajo en equipo interdisciplinario. Por ejemplo, tecnología con recursos humanos. 

### 2.4 Plan de adopción de la nube

:book: Desarrolla un plan de adopción de la nube para administrar los cambios en el patrimonio digital, las aptitudes y la organización.

1. **Requisitos previos**: confirma que se han completado todos los pasos de requisitos previos antes de crear el plan.

2. **Definición y clasificación por prioridades de las cargas de trabajo**: clasifiqua por prioridades las 10 primeras cargas de trabajo para establecer un trabajo pendiente de adopción inicial.

3. **Adaptación de los recursos a las cargas de trabajo**: identifica qué recursos (propuestos o existentes) son necesarios para posibilitar las cargas de trabajo clasificadas por prioridades.

4. **Revisión de las decisiones de racionalización**: revisa las decisiones de racionalización para refinar las decisiones de la ruta de adopción: **migrar o innovar**.

5. **Establecimiento de iteraciones y planes de versiones**: las iteraciones son los bloques de tiempo asignados para realizar el trabajo. Las versiones son la definición del trabajo que se debe realizar antes de desencadenar un cambio en los procesos de producción.

6. **Estimación del tiempo**: establece escalas de tiempo aproximadas para fines de planeamiento de versiones, en función de las estimaciones iniciales.

## 3 Preparación de la organización

### 3.1 Guía de instalación de Azure

:book: Revisa la guía de instalación de Azure para familiarizarse con las herramientas y los enfoques necesarios para crear una zona de aterrizaje.

- [Introducción a la guía de configuración de Azure](https://docs.microsoft.com/es-es/azure/cloud-adoption-framework/ready/azure-setup-guide/)

### 3.2 Zonas de aterrizaje de Azure

:book: Elige la opción de zona de aterrizaje más adecuada para establecer un punto de partida basado en código para su entorno.

Las zonas de aterrizaje de Azure permiten la migración de aplicaciones y el desarrollo. 

Es la puesta en marcha de varias suscripciones que tiene en cuenta la escala, seguridad, gobernanza, redes e identidad para poder comenzar a trabajar con la nube.

### 3.3 Expansión de la zona de aterrizaje

:book: Amplía la primera zona de aterrizaje para cumplir los requisitos de plataforma del plan de adopción de la nube.

- **Consideraciones básicas**: refactoriza una zona de aterrizaje para refinar el hospedaje, los fundamentos y otros elementos básicos.
- **Expansiones de operaciones**: agrega configuraciones de administración de operaciones para mejorar el rendimiento, la confiabilidad y la excelencia operativa.
- **Expansiones de gobernanza**: agrega configuraciones de la gobernanza para mejorar el costo, la confiabilidad, la seguridad y la coherencia.
- **Expansiones de seguridad**: agrega configuraciones de la seguridad para mejorar la protección de los datos confidenciales y los sistemas críticos.

### 3.4 Procedimientos recomendados

:book: Utiliza los procedimientos recomendados para validar las modificaciones de la zona de aterrizaje, con el fin de garantizar la correcta configuración de las zonas de aterrizaje actuales y futuras.

Estas recomendaciones dependerán de los recursos, el tipo de solución a implementar, las áreas, la organización...

## 4. Adopción de la nube



## 5. Control y administración de los entornos de nube


- [Procedimientos recomendados de preparación para Azure](https://docs.microsoft.com/es-es/azure/cloud-adoption-framework/ready/azure-best-practices/)

Para aprender más de el consulta los siguientes dos recursos:
- [Aceleración del uso de la nube con Cloud Adoption Framework para Azure](https://docs.microsoft.com/es-mx/learn/modules/build-cloud-governance-strategy-azure/2-accelerate-cloud-adoption-framework)
- [Plataforma de adopción de la nube de Microsoft para Azure](https://docs.microsoft.com/es-es/azure/cloud-adoption-framework/)