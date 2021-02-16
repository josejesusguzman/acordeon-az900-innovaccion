# Formulario calculo de Nivel de Servicio (SLA)

**Para buscar el SLA de cada servicio consulta la [página de Acuerdos de nivel de servicio](https://azure.microsoft.com/es-mx/support/legal/sla/)**

Para todos los servicios de Azure encontrarás cifras similares a 99.99% o 99.95%. Esto quiere decir que el servicio está disponible la gran mayoría del tiempo en un año.

**Por ejemplo:**

<img src="/res/images/cosmos_db.png" alt="drawing" width="150"/>

El servicio de **Azure Cosmos DB** ofrece un SLA de 99,999 %, esto quiere decir que el servicio tiene "*derecho*" a fallar o ser interrumpido por 52.56 minutos al año. 

Al inicio 00.001% puede parecer poco, pero ya puesto en minutos por año resulta que es un tiempo considerable ¡Es casi una hora sin servicio!

Otro ejemplo es el de **Azure Kubernetes Service (AKS)** ya que sin zonas de disponibilidad tienen un acuerdo de nivel de servicio del 99.95% que nos da como espaico de interrupción (redondeando hacia arriba) 263 minutos que se traducen en una interrupción de** 4 horas 23 minutos**. 

¿Te imaginas que el sistema este sin servicio por casi cuatro horas y media?

Aclaro de nuevo, esto no significa que vayan a haber 4 horas de interrupción continuas sino es la suma de todos los tiempos más pequeños y su resultado es el máximo que Azure tiene "derecho" a interrumpirse.

## Calculo del SLA por arquitectura o conjunto de servicios

Es posible (y necesario) calcular el nivel de acuerdo de servcio de toda la solución en conjunta para efectos de calidad en el servicio, terminos y condiciones y previsión.

Esto se hace **multiplicando** los SLA de cada recurso integrante de la solución. Por ejemplo:

![Diagrama 1 SLA](/res/images/diagrama1_sla.jpg)

~~~
99.95% * 99.95% = 0,99900025 = 99.9%
~~~

Sin embargo, esto se complica cuando tenemos algo así:

![Diagrama 2 SLA](/res/images/diagrama2_sla.jpg)

En esta arquitectura todo puede pasar como:

- SQL Server en RegiónA está sin servicio
- SQL Server en RegiónB está sin servicio
- App Service en RegiónA está sin servicio
- App Service en RegiónB está sin servicio
- Traffic Manager está sin servicio
- Combinaciones varias de todo lo anterior

Para este caso (disponibilidad serial y paralela), comenzaremos con nuestra probabilidad compuesta para cada región (aunque a veces puede variar por recurso en cada región), asumiendo que no hay probabilidad independiente para la región en sí y que cada región está aislada y, como tal, una falla de base de datos solo elimina su región.

Tenemos la probabilidad OK del **Traffic Manager P(T) = 0.9999** y cada par de **app+DB con una probabilidad OK P(G) = 0,99900025**.

El número de regiones que tenemos juega un rol, ya que tenemos que aplicar el producto de la probabilidad de falla solo para obtener la probabilidad de que ambas regiones caigan al mismo tiempo: 

~~~
0,00099975 * 0,00099975 = 0,0000009995000625
~~~

Lo que significa una disponibilidad general de al menos una región de **99,049375%**. 

Ahora que tenemos la disponibilidad general de las regiones, el producto con el del administrador de tráfico nos da la disponibilidad general del sistema:

~~~
0.9999 * 0,9999990004999375 = 0,99989900059988750625
~~~

La disponibilidad general es **99.989900 %**.

Traducido a minutos por año. Recordando que cada año equivale a 525600 

~~~
525600 * (1- 0.99989900) = 53.0856
~~~

**53 minutos de servicio caido**

![Diagrama 3 SLA](/res/images/diagrama3_sla.jpg)

**NOTA:** En tu examen tendrás acceso a una calculadora así que no te preocupes por las cuentas, preocupate más por aprender el proceso.

[Más información aquí](https://docs.microsoft.com/en-us/azure/architecture/framework/resiliency/business-metrics#slas-for-multiregion-deployments)

