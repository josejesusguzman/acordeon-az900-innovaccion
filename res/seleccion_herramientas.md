# Criterios básicos de selección de herramientas

Una parte importante (aunque no la única ni la más indispensable) es la elección de las herramientas que más se adapten a la solución a realizar. Ya sea por relación costo/beneficio, función, dependencia de otra herramienta, se utilizarán multiples herramientas para soluciones robustas.

**Nota**: Más herramientas en una solución pueden aumentar su robustez y capacidad de respuesta pero la hacen cada vez más compleja y con menos SLA.

No es necesario tener una herramienta de cada categoria ya que esto dependerá de las necesidades de la solución y del contexto en el que la estemos haciendo.

Además, las capacidades y funciones de cada herramienta pueden variar dependiendo del nivel de servicio o *pricing tier* contratado. Por ello es importante siemrpe revisar el ***pricing tier*** de cada solución antes de hacer la selección más adecuada.

## 1. Cómputo o procesamiento

La categoría que ejeuctará nuestra solución, procesará las solicitudes de los usuarios y/o realizará las acciones que deben hacerse.

![Diagrama de compute](/res/images/diagrama-select-compute.jpg)

**"Lift-and-shift"** es una estrategia de migración de una carga de trabajo a la nube sin volver a diseñar la aplicación ni realizar cambios en el código. También se denomina rehospedaje.

- Para más información consulta la [documentación](https://docs.microsoft.com/es-mx/azure/architecture/guide/technology-choices/compute-decision-tree)

## 2. Almacen de datos