# Comparativa de servicios de seguridad de red de Azure

Recurso | Abstracción
--------- | -----------
Azure DDoS Protection | Se usa para evitar ataques masivos envió de peticiones a las soluciones y evitar que colapsen
Azure Firewall | Se utilizar para limitar las conexiones entrantes y salientes de Azure.
Grupos de seguridad de red (NSG) | Lo puedes considerar como un Firewall interno para los recursos de tu solución.
Azure Application Gateway | Proporciona cifrado y descifrado de de conexión segura SSL, inspecciona el tráfico web y detectar ataques en la capa de HTTP.

## Grupos de seguridad de red (NSG)
Un **grupo de seguridad de red permite filtrar el tráfico de la red desde y hacia los recursos** de Azure en una red virtual. Los puedes considerar como un **firewall\***  interno. Un NSG puede contener varias reglas de seguridad entrantes y salientes que permiten filtrar el tráfico por dirección IP de origen y destino, puerto y protocolo.

Un NSG puede contener las siguientes reglas de seguridad:
Propiedad | Descripción
--------- | -----------
Nombre | Nombre único para el NSG.
Prioridad | Rango entre 100 y 4096 donde los números más bajos se procesan antes que los más altos.
Origen o destino | Una dirección IP o intervalo de direcciones IP.
Protocolo | HTTP. TCP, UDP, etc.
Dirección | ¿Se aplica al tráfico entrante o saliente?
Intervalo de puertos | Puerto único o intervalo de **puertos\***. Por ejemplo, 80, 433, 443... 
Acción | Permitir o Denegar.

## Azure Firewall
**Servicio de seguridad de red administrado ayuda a proteger los recursos en las redes virtuales de Azure.**

Una red virtual es similar a una red tradicional con la que trabajaría en su propio centro de datos.

Azure Firewall proporciona una ubicación central para crear, aplicar y registrar directivas de conectividad de red y de aplicaciones entre suscripciones y redes virtuales.

- Azure Firewall solo cuando no hay aplicaciones web en la red virtual.

## Azure Aplication Gateway
Es un **equilibrador de carga de tráfico web administrado y un proxy inverso completo HTTP(S)** que puede realizar cifrado y descifrado de capa de conexión segura (SSL). Application Gateway también utiliza Web Application Firewall para **inspeccionar el tráfico web y detectar ataques en la capa HTTP**. 

- Application Gateway solo cuando solo hay aplicaciones web en la red virtual y los grupos de seguridad de red (NSG) proporcionan un filtrado de salida optimo.

### Selecciona la herramienta correcta

![Diagrama de elección de herramientas](/res/images/diagrama_seguridad.jpg)

## Azure DDoS Protection
Azure DDoS Protection ayuda a proteger los recursos frente a **ataques DDoS\***.

La red global de Azure se usa para distribuir y mitigar el tráfico de ataques entre regiones de Azure.

Esta herramienta tiene dos niveles de servicio:
- **Basic:** ya se encuentra habilitado de forma automática y sin coste en tu suscripción de Azure. 
- **Estandar:** ofrece funcionalidades adicionales de mitigación adaptadas específicamente a los recursos de Azure Virtual Network. Además, proporciona supervisión del tráfico siempre activa y mitigación en tiempo real de los ataques a nivel de red más comunes.

## Ejemplos de uso

Servicio | Ejemplo
--------- | -----------
Azure DDoS Protection | Un atacante puede dejar fuera de servicio el sitio web enviando un gran volumen de tráfico de red a los servidores.
Azure Firewall | Se puede usar para limitar de las maquinas virtuales a solo unas direcciones IP especificadas.
NSG | Para denegar de forma predeterminada que las maquinas virtuales se puedna conectar entre si. De esta forma podrías hacer más dificil a un atacante vulnerar toda tu solución si ya logró acceder a una VM.
Azure Aplication Gateway | Cuando tienes una aplicación web en una VM y los usuarios acceden a ella por medio de una intranet y usando protocolo HTTP (el mismo de Internet).

---

**Firewall**: bloquea accesos no autorizados, permitiendo al mismo tiempo comunicaciones autorizadas.
**Puerto**: Un puerto es numero de 16 bits por lo que existen 65.536 puertos en cada ordenador. Las aplicaciones utilizan estos puertos para recibir y transmitir mensajes.
**Ataque de denegación de servicio (DDoS)**: tipo de ataque en el que se intenta colapsar los servidores mediante el envío de un gran número de peticiones que simulan ser usuarios reales con el objetivo de que el servicio deje de estar disponible.
**FQDN:**  Fully Qualified Domain Name (FQDN) se refiere a la dirección completa y única necesaria para tener presencia en Internet. Está compuesta por el nombre de host y el de dominio y se utiliza para localizar hosts específicos en Internet y acceder a ellos mediante la resolución de nombres.

- **Ejemplo de FQDN**
~~~
docs.microsoft.com.
[Nombre de host].[Dominio].[TLD].[Raíz]
~~~
