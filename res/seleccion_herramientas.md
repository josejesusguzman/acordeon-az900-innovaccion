# Criterios básicos de selección de herramientas

Una parte importante (aunque no la única ni la más indispensable) es la elección de las herramientas que más se adapten a la solución a realizar. Ya sea por relación costo/beneficio, función, dependencia de otra herramienta, se utilizarán multiples herramientas para soluciones robustas.

**Nota**: Más herramientas en una solución pueden aumentar su robustez y capacidad de respuesta pero la hacen cada vez más compleja y con menos SLA.

No es necesario tener una herramienta de cada categoria ya que esto dependerá de las necesidades de la solución y del contexto en el que la estemos haciendo.

Además, las capacidades y funciones de cada herramienta pueden variar dependiendo del nivel de servicio o *pricing tier* contratado. Por ello es importante siemrpe revisar el ***pricing tier*** de cada solución antes de hacer la selección más adecuada.



## 1. Cómputo o procesamiento

La categoría que ejecutará nuestra solución, procesará las solicitudes de los usuarios y/o realizará las acciones que deben hacerse.

![Diagrama de compute](/res/images/diagrama-select-compute.jpg)

**"Lift-and-shift"** es una estrategia de migración de una carga de trabajo a la nube sin volver a diseñar la aplicación ni realizar cambios en el código. También se denomina rehospedaje.

- Para más información consulta la [documentación](https://docs.microsoft.com/es-mx/azure/architecture/guide/technology-choices/compute-decision-tree)

## 2. Almacen de datos

Esta categoria guardará los datos y archivos necesarios para el correcto funcionamiento de la solución

![Desición data](/res/images/data-store-decision-tree.png)

## 3. Balanceo de carga

Equilibrio de carga hace referencia a la distribución de cargas de trabajo entre varios recursos de proceso. El equilibrio de carga busca optimizar el uso de recursos, maximizar el rendimiento, minimizar el tiempo de respuesta y evitar la sobrecarga de un solo recurso. También puede mejorar la disponibilidad al compartir una carga de trabajo entre recursos de proceso redundantes.

Servicio |	Global/regional	| Tráfico recomendado
--------- | ----------- | ----------------------------
**Azure Front Door** |	Global |	HTTP(S)
**Traffic Manager** |	Global |	No HTTP(S)
**Application Gateway**|	Regional |	HTTP(S)
**Azure Load Balancer** |	Global |	No HTTP(S)

![Balanceo de carga](/res/images/load-balancing-decision-tree.png)

## 4. Seguridad

Grupo de herramientas para blindar las soluciones sobre Azure contra todo ataque externo o falla interna.

![Diagrama de elección de herramientas](/res/images/diagrama_seguridad.jpg)

- [Más información aquí](/res/comparativa_azureAD.md)

## Otros

Además Azure tiene otras categorias que se alinean de acuerdo a necesidades más epecificas como:

- [Blockchain](https://docs.microsoft.com/es-es/azure/blockchain/)
- [Internet de las cosas (IoT)](https://docs.microsoft.com/es-es/azure/iot-fundamentals/)
- [Inteligencia artificial](https://docs.microsoft.com/es-es/azure/cognitive-services/)
- [Machine Learning](https://docs.microsoft.com/es-es/azure/machine-learning/)
- [Redes](https://docs.microsoft.com/es-es/azure/networking/)
- [DevOps](https://docs.microsoft.com/es-es/azure/devops-project/)




