# Ejercicios de calculo de Acerdo de nivel de Servicio (SLA)

## Instrucciones
De cada una de estas soluciones tienes que calcular el acuerdo de nivel de servicio. Te daré solo la solución y tu tienes que llegar a ella.

**Te recomiendo determinar cuanto tiempo estará disponible y cuanto no en determinado espacio de tiempo como en un mes o en un año**

Te dejo el enlace con la explicación de cada solución por si quieres aprender más como funciona y como se conectan los diferentes recursos de Azure.

**Nota:** Algunos resultados pueden estar redondeados.

- **[Consulta aquí los SLA de los recursos](https://azure.microsoft.com/es-mx/support/legal/sla/)**
- **[Si tienes dudas checa este formulario de SLA](/res/formulario_sla.md)**

## Indice
  - [Ejercicio 1. Microservicios sin servidor integrados en la red virtual](#ejercicio-1-microservicios-sin-servidor-integrados-en-la-red-virtual)
  - [Ejercicio 3. Clasificación de imágenes en Azure](#ejercicio-3-clasificación-de-imágenes-en-azure)
  - [Ejercicio 3. Motor de búsqueda inteligente de productos para comercio electrónico](#ejercicio-3-motor-de-búsqueda-inteligente-de-productos-para-comercio-electrónico)
  - [Ejercicio 4. Clúster de conmutación por error de SQL Server 2008 R2 en Azure](#ejercicio-4-clúster-de-conmutación-por-error-de-sql-server-2008-r2-en-azure)
  - [Ejercicio 6. Análisis de Content Delivery Network](#ejercicio-6-análisis-de-content-delivery-network)
  - [Ejercicio 7. Aplicaciones inteligentes mediante Azure Database for MySQL](#ejercicio-7-aplicaciones-inteligentes-mediante-azure-database-for-mysql)
  - [Ejercicio 8. Aplicaciones inteligentes mediante Azure Database for PostgreSQL](#ejercicio-8-aplicaciones-inteligentes-mediante-azure-database-for-postgresql)
  - [Ejercicio 9. Optimización del suministro de energía](#ejercicio-9-optimización-del-suministro-de-energía)
  - [Ejercicio 10. Portal sanitario del consumidor en Azure](#ejercicio-10-portal-sanitario-del-consumidor-en-azure)
  - [Ejercicio 11. Control de calidad](#ejercicio-11-control-de-calidad)
  - [Ejercicio 12. Aplicación web básica](#ejercicio-12-aplicación-web-básica)
  - [Ejercicio 13. DevOps seguro para AKS](#ejercicio-13-devops-seguro-para-aks)
  - [Ejercicio 14. Inteligencia artificial en el perímetro con Azure Stack Hub: desconectado](#ejercicio-14-inteligencia-artificial-en-el-perímetro-con-azure-stack-hub-desconectado)
  - [Ejercicio 15. Ejecución de un servidor Jenkins en Azure](#ejercicio-15-ejecución-de-un-servidor-jenkins-en-azure)
  - [Ejercicio 16. Mantenimiento predictivo de Azure para IoT industrial](#ejercicio-16-mantenimiento-predictivo-de-azure-para-iot-industrial)
  - [Ejercicio 17. Ofertas personalizadas](#ejercicio-17-ofertas-personalizadas)
  - [Ejercicio 18. Aplicaciones web de varias regiones con conectividad privada a la base de datos](#ejercicio-18-aplicaciones-web-de-varias-regiones-con-conectividad-privada-a-la-base-de-datos)
  - [Ejercicio 19. Compilación de aplicaciones web y para dispositivos móviles](#ejercicio-19-compilación-de-aplicaciones-web-y-para-dispositivos-móviles)
  - [Ejercicio 20. Análisis de IoT con Azure Data Explorer](#ejercicio-20-análisis-de-iot-con-azure-data-explorer)
  - [Ejercicio 21. DevTest y DevOps para soluciones de microservicios](#ejercicio-21-devtest-y-devops-para-soluciones-de-microservicios)

________________________________________________________

## Ejercicio 1. Microservicios sin servidor integrados en la red virtual

![virtual-network-microservices](/res/images/sla/virtual-network-microservices.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/example-scenario/integrated-multiservices/virtual-network-integration)

### Detalles
- El servicio de **API Management** utiliza un nivel Premium escalado en la misma región
- El servicio de **Cosmos DB** se ejecuta en una sola región
- App insights no tiene SLA

### Resultado
**SLA: 99.74 %**

________________________________________________________

## Ejercicio 3. Clasificación de imágenes en Azure

![architecture-intelligent-apps-image-processing](/res/images/sla/architecture-intelligent-apps-image-processing.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/example-scenario/ai/intelligent-apps-image-processing)

### Detalles
- El servicio de **Storage Account (cuenta de almacenamiento)** utiliza el nivel de acceso esporadico
- El servicio de **Blob Storage** utiliza el nivel de acceso esporadico
- El servicio de **Computer Vision (Cognitive Services)** utiliza en nivel básico de servicio
- El servicio de **Cosmos DB** se ejecuta en múltiples regiones.

### Resultado
**SLA: 97.85 %**

________________________________________________________

## Ejercicio 3. Motor de búsqueda inteligente de productos para comercio electrónico

![architecture-ecommerce-search](/res/images/sla/architecture-ecommerce-search.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/example-scenario/apps/ecommerce-search)

### Detalles
- **App Service** utiliza un nivel de servicio básico
- **Cognitive Search** esta configurada con dos réplicas
- **SQL Database** utiliza el nivel Business Critical sin redundancia de zona de uso estandar
- **Cognitive Services** usa el nivel básico

### Resultado
**SLA: 99.64 %**

________________________________________________________

## Ejercicio 4. Clúster de conmutación por error de SQL Server 2008 R2 en Azure

![windows-server-2008-r2-failover-cluster-with-azure-shared-disk](/res/images/sla/windows-server-2008-r2-failover-cluster-with-azure-shared-disk.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/example-scenario/sql-failover/sql-failover-2008r2)

### Detalles
- Una de las **maquinas virtuales** esta configurada para tener dos instancias en zona de disponibilidad. La otra maquina virtual no, es una sola instancia que utiliza discos HDD Standard
- El **SMB es una cuenta de almacenamiento** que con redundancia geografica
- Ignora la red virtual y el disco ocmpartido

### Resultado
**SLA: 94.98 %**
________________________________________________________

## Ejercicio 6. Análisis de Content Delivery Network

![content-delivery-network-azure-data-explorer](/res/images/sla/content-delivery-network-azure-data-explorer.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/content-delivery-network-azure-data-explorer)

### Detalles
- Solo ignora el dashboard de muestro de datos

### Resultado
**SLA: 99.70 %**
________________________________________________________

## Ejercicio 7. Aplicaciones inteligentes mediante Azure Database for MySQL

![intelligent-apps-using-azure-database-for-mysql](/res/images/sla/intelligent-apps-using-azure-database-for-mysql.jpg)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/intelligent-apps-using-azure-database-for-mysql)

### Detalles
- El **Event hub** utiliza el nivel especifico de servicio
- La **cuenta de almacenamiento** es de nivel de acceso esporadico RA-GRS
- Ignora Machine Learning Studio y Power BI

### Resultado
**SLA: 99.78 %**
________________________________________________________

## Ejercicio 8. Aplicaciones inteligentes mediante Azure Database for PostgreSQL

![intelligent-apps-using-azure-database-for-postgresql](/res/images/sla/intelligent-apps-using-azure-database-for-postgresql.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/intelligent-apps-using-azure-database-for-postgresql)

- El **Event hub** utiliza el nivel especifico de servicio
- La **cuenta de almacenamiento** es de nivel de acceso esporadico RA-GRS
- Ignora Machine Learning Studio y Power BI
- El servicio de **Database for PostgreSQL** utiliza Hyperscale Citus

### Resultado
**SLA: 99.74 %**
________________________________________________________

## Ejercicio 9. Optimización del suministro de energía

![energy-supply-optimization](/res/images/sla/energy-supply-optimization.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/energy-supply-optimization)

### Detalles
- Las web apps tomalas como **App service**
- Ignora el servicio de Power BI
- Un servicio de **SQL Database** es de nivel Premium con implementación redundante de zona. El otro servicio tiene una replica y es de nivel Hyperscale
- El servicio de **Storage Queue** esta configurado con almacenamiento de redundancia de zona (ZRS)
- El servicio de **Blob Storage** tiene nivel de acceso esporadico con LRS
- La **maquina virtual** tiene dos instancias instaladas en el mismo conjunto de disponibilidad

### Resultado
**SLA: 98.68 %**
________________________________________________________

## Ejercicio 10. Portal sanitario del consumidor en Azure

![consumer_health_portal](/res/images/sla/consumer_health_portal.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/example-scenario/digital-health/health-portal)

### Detalles
- Toma el SLA de **Azure WAF** como igual al de **Azure Front Door**
- El servicio de **API Management** es d enivel premium con tres implementaciones en zonas de disponibilidad
- El servicio de **Cosmos DB** esta configurado en multiples regiones
- El servicio de **Blob Storage** tiene nivel de acceso esporadico con GRS

### Resultado
**SLA: 98.87 %**
________________________________________________________

## Ejercicio 11. Control de calidad

![quality-assurance](/res/images/sla/quality-assurance.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/quality-assurance)

### Detalles
- El **Events Hub** usa un nivel estándar de servicio
- Ignora el **Raw Stream Data** y **Machine Learning**

### Resultado
**SLA: 99.65 %**
________________________________________________________

## Ejercicio 12. Aplicación web básica

![basic-web-app](/res/images/sla/basic-web-app.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/reference-architectures/app-service-web-app/basic-web-app?tabs=cli)

### Detalles
- **Active Directory** tiene un nivel de servicio básico
- Ignora los servicios **Azure DNS**, **Key Vault**, **plan de App service** y el **Azure Monitor**
- **Logical Server** es un servicio Azure SQL Database y tiene hyperscale con una replica
- Las otras dos bases de datos **SQL Database** son de uso general con tres réplicas (redundancia de zona)
- Considera la disponibilidad minima de un área de trabajo de **Log Analytics**

### Resultado
**SLA: 99.62 %**
________________________________________________________

## Ejercicio 13. DevOps seguro para AKS

![secure-devops-for-kubernetes](/res/images/sla/secure-devops-for-kubernetes.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/secure-devops-for-kubernetes)

### Detalles
- Solo toma en cuenta el SLA de los recursos de Azure y si no tiene SLA no lo tomes en cuenta
- Los **Pipelines** son parte de Azure DevOps y se usa un plan de pago de pipelines
- El **AKS** utiliza zona de disponibilidad
- El servicio de **Azure Monitor** utiliza un área de trabajo de Log Analytics

### Resultado
**SLA: 99.65 %**
________________________________________________________

## Ejercicio 14. Inteligencia artificial en el perímetro con Azure Stack Hub: desconectado

![ai-at-the-edge-disconnected](/res/images/sla/ai-at-the-edge-disconnected.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/ai-at-the-edge-disconnected)

### Detalles
- Si un servicio no tiene SLA ignoralo
- El servicio de **Apache Hadoop** se ejecuta en un cluster de HDImsight
- La **maquina virtual** tiene un SSD estandar y es de una sola instancia
- Una **cuenta de almacenamiento** utiliza RA-GRS y  la otra utiliza ZRS. Ambas no son de acceso esporádico
- El **AKS** no utiliza zona de disponibilidad

### Resultado
**SLA: 98.99 %**
________________________________________________________

## Ejercicio 15. Ejecución de un servidor Jenkins en Azure

![architecture-jenkins](/res/images/sla/architecture-jenkins.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/example-scenario/apps/jenkins)

### Detalles
- La **Jenkins Server** tiene tres instancias en zona de disponibilidad dentro de la misma región
- Las tres **Build VM** están en una grupo de Host dedicado con dos instancias dentro del conjunto de disponibilidad
- Se usa el nivel premium de **Active Directory**
- Los **Managed Disk** toman el SLA de una cuenta de almacenamiento con ZRS
- Ignora el SLA de **Azure Monitor**
- El **Blob Storage** es de nivel de acceso esporadico con LRS

### Resultado
**SLA: 98.63 %**
________________________________________________________

## Ejercicio 16. Mantenimiento predictivo de Azure para IoT industrial

![iot-predictive-maintenance](/res/images/sla/iot-predictive-maintenance.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/iot-predictive-maintenance)

### Detalles
- Ignora los servicios que no tienen SLA
- El servicio **Azure Kubernetes Services** utiliza zona de disponibilidad
- El **Event Hub** usa el nivel específico
- Data Lake = **Data Lake Storage**
- **Power Bi** esta en su edición Embedded

### Resultado
**SLA: 99.59 %**
________________________________________________________

## Ejercicio 17. Ofertas personalizadas

![personalized-offers](/res/images/sla/personalized-offers.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/personalized-offers)

### Detalles
- Ignora los elementos de data, no los servicios de Azure
- El servicios **Cosmos DB** esta hospedado solo en una región
- El servicio de Event Hub usa el nivel básico
- Ignora el **Machine Learning Studio**
- La **base de datos** es de PostgreSQL

### Resultado
**SLA: 99.68 %**
________________________________________________________

## Ejercicio 18. Aplicaciones web de varias regiones con conectividad privada a la base de datos

![app-service-private-sql-multi-region-solution-architecture](/res/images/sla/app-service-private-sql-multi-region-solution-architecture.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/example-scenario/sql-failover/app-service-private-sql-multi-region)

### Detalles
- Cada región tiene dos **App Services** B1
- Cada región tiene un **Private Link**
- La región primaria usa un servicio **SQL Database** Premium con implementación redundante
- La región secundaria usa un servicio **SQL Database** Business Critical con dos replicas
- Ignora el servicio **DNS**

### Resultado
**SLA: 99.76 %**
________________________________________________________

## Ejercicio 19. Compilación de aplicaciones web y para dispositivos móviles

![webapps](/res/images/sla/webapps.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/webapps)

### Detalles
- **API Management** usa el nivel premium con dos zonas de disponibilidad
- Un **AKS** no utiliza zona de disponibilidad. El que manda la información a la app si
- El primer **Event Hub** utiliza el servicio básico
- El segundo **Event Hub** utiliza el servicio de nivel específico
- **Cache for Redis** utiliza el servicio Enterprise Flash sin zona de disponibilidad
- **Blob Storage** tiene LRS
- Es posible escribir en la base de datos de **Cosmos DB** desde varias regiones

### Resultado
**SLA: 99.51 %**
________________________________________________________

## Ejercicio 20. Análisis de IoT con Azure Data Explorer

![iot-azure-data-explorer](/res/images/sla/iot-azure-data-explorer.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/iot-azure-data-explorer)

### Detalles

### Resultado
**SLA:  %**
________________________________________________________

## Ejercicio 21. DevTest y DevOps para soluciones de microservicios

![dev-test-microservice](/res/images/sla/dev-test-microservice.png)

- [Más información aquí](https://docs.microsoft.com/es-mx/azure/architecture/solution-ideas/articles/dev-test-microservice)

### Detalles

### Resultado
**SLA:  %**