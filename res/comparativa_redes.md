# Comparativa de servicios de redes de Azure

- [Documentación de redes de Azure](https://docs.microsoft.com/es-es/azure/networking/)

Servicio | Descripción | Ejemplo de uso
-------- | ----------- | -----------
**[Azure Front Door](#azure-front-door)** | Servicio que sirve como punto de entrada a nivel global para las aplicaciones, es decir, que una aplicación web pueda ser consumida en todo el mundo sin porblemas. | Una página web creada en Estados Unidos puede servir a sus usuarios de la misma manera en Japón.
**[Azure Virtual Network](#azure-virtual-network)** | Es el bloque fundamental de creación de redes privadas en Azure. Permite a muchos recursos como las maquinas virtuales comunicarse entre si. Es similar a una red fisica tradicional pero virutalizada con escalabilidad, alta disponibilidad y aislamiento. | Para conectar dos maquinas virtuales de Azure o conectar una a un servidor fisico.
**[Azure VPN Gateway](#azure-vpn-gateway)** | El servicio de puerta de enlace de Azure para enviar tráfico cifrado entre una red virtual de Azure y una ubicación local a través de la red pública de Internet. | Si haces una llamada a una API externa o a tu servidor local podrías hacerlo de manera segura y cifrada con VPN Gateway.
**[Azure ExpressRoute](#azure-expressroute)** | Permite ampliar las redes locales y conectarlas con la nube de Microsoft sin que estas conexiones pasen por el Internet convencional. | Si tienes un servidor local y quieres que se comunique con recursos que tienes en Azure como una maquina virtual la forma más segura es con ExpressRoute.
**[Azure Traffic Manager](#azure-traffic-manager)** | Es un equilibrador de carga de tráfico basado en DNS. Este servicio permite distribuir el tráfico a las aplicaciones orientadas al público en las regiones globales de Azure. Traffic Manager también proporciona puntos de conexión públicos con alta disponibilidad y rápida capacidad de respuesta. | Si necesitas que soluciones de Azure en diferentes partes del mundo se conectan o si necesitas que todo el mundo accesa a tu aplicación usas Traffic Manager
**[Azure CDN](#azure-cdn)** | Una red de entrega de contenido (CDN) es una red distribuida de servidores que puede proporcionar contenido web a los usuarios de manera eficaz. | Para que usuarios accedan en todo el mundo con una mejor experiencia sin necesitar servidores en todos el mundo.


## Azure Front Door

![Azure-Front-Door](/res/images/front-door.png)

**Front Door** funciona en la **capa 7 (capa HTTP/HTTPS)** y usa el protocolo de difusión por proximidad con división TCP y la red global de Microsoft para mejorar la conectividad global. Al igual que Traffic Manager, Front Door es resistente a errores, incluidos los que afectan a una región completa de Azure.

Front Door permite definir, administrar y supervisar el enrutamiento global para el tráfico web mediante la optimización para obtener un rendimiento de usuario final de nivel superior y confiabilidad a través de una conmutación por error global rápida.

**Características clave:**

- Rendimiento acelerado de la aplicación mediante el uso del protocolo Anycast basado en la división TCP
- Supervisión del sondeo de estado inteligente para los recursos de back-end
- Enrutamiento basado en ruta de acceso URL para las solicitudes.
- Habilita el hospedaje de varios sitios web para una infraestructura de aplicaciones eficaz
- Afinidad de sesión basada en cookies
- Descarga de SSL y administración de certificados
- Definición de su propio dominio personalizado
- Seguridad de las aplicaciones con el firewall de aplicaciones web (WAF) integrado
- Redireccionamiento del tráfico HTTP a HTTPS con el redireccionamiento de direcciones URL
- Ruta de acceso de reenvío personalizada con la reescritura de direcciones URL
- Compatibilidad nativa con conectividad IPv6 de un extremo a otro y el protocolo HTTP/2

## Azure Virtual Network

![Virtual Network](/res/images/virtual-network.png)

Una red virtual de Azure permite que los recursos de Azure se comuniquen de forma segura entre ellos, con Internet y con redes locales. Entre los escenarios clave que se pueden realizar con una red virtual se incluyen los siguientes: la comunicación de los recursos de Azure con Internet, la comunicación entre los recursos de Azure, la comunicación con los recursos locales, el filtrado del tráfico de red, el enrutamiento del tráfico de red y la integración con los servicios de Azure.

**Virtual Network permite:**
- Comunicación entre recursos de Azure
- Comunicación con Internet
- Comunicación con recursos locales
  - **Azure ExpressRoute**: se establece entre la red y Azure, mediante un asociado de ExpressRoute. Esta conexión es privada. El tráfico no pasa por Internet.
- Filtrado del tráfico de red
- Enrutado del tráfico de red

## Azure VPN Gateway

![VPN Gateway](/res/images/vpn-gateway.png)

Una puerta de enlace de red virtual se compone de dos o más máquinas virtuales que se implementan en una subred específica llamada subred de la puerta de enlace. Las máquinas virtuales de puerta de enlace de red virtual contienen tablas de enrutamiento y ejecutan servicios específicos de puerta de enlace. Estas máquinas virtuales se crean al generar la puerta de enlace de red virtual. No se pueden configurar directamente las máquinas virtuales que forman parte de la puerta de enlace de red virtual.

El tipo de puerta de enlace "VPN" especifica que el tipo de puerta de enlace de red virtual creado es una "puerta de enlace de VPN". Esto lo distingue de una puerta de enlace de ExpressRoute, que usa un tipo de puerta de enlace diferente. Una red virtual puede tener dos puertas de enlace de red virtual, una puerta de enlace de VPN y una puerta de enlace de ExpressRoute.

## Azure ExpressRoute

![ExpressRoute](/res/images/expressroute.png)

La conectividad puede ser desde una red de conectividad universal (IP VPN), una red Ethernet de punto a punto o una conexión cruzada virtual a través de un proveedor de conectividad en una instalación de ubicación compartida. Las conexiones de ExpressRoute no pasan por la red pública de Internet. Esto permite a las conexiones de ExpressRoute ofrecer más confiabilidad, más velocidad, latencia coherentes y mayor seguridad que las conexiones normales a través de Internet.

- **ExpressRoute utiliza proveedores externos de comunicaciones para hacer la comunicación de punto a punto**

**Ventajas principales**
- Conectividad de nivel 3 entre la red local y la nube de Microsoft a través de un proveedor de conectividad. La conectividad puede ser desde una red de conectividad universal (IP VPN), una red Ethernet de punto a punto, o una conexión cruzada virtual a través de un intercambio de Ethernet.
- Conectividad de servicios en la nube de Microsoft en todas las regiones dentro de la región geopolítica.
- Conectividad global a los servicios de Microsoft en todas las regiones con el complemento ExpressRoute Premium.
- Enrutamiento dinámico entre la red y Microsoft a través de BGP.
- Redundancia integrada en todas las ubicaciones de configuración entre pares para una mayor confiabilidad.
- El tiempo de actividad de conexión SLA.
Compatibilidad con QoS de Skype para la empresa.

## Azure Traffic Manager

![Traffic Manager](/res/images/traffic-manager.png)

Traffic Manager usa DNS para dirigir las solicitudes del cliente al punto de conexión de servicio adecuado en función de un método de enrutamiento del tráfico. Traffic Manager también proporciona supervisión de estado de todos los puntos de conexión. El punto de conexión de puede ser cualquier servicio accesible desde Internet hospedado dentro o fuera de Azure.

**Traffic Manager ofrece las siguientes características:**
- Aumento de la disponibilidad de la aplicación
- Mejora del rendimiento de las aplicaciones
- Mantenimiento del servicio sin inactividad
- Combinación de aplicaciones híbridas
- Distribución del tráfico para implementaciones complejas

### Uso con recursos de seguridad web

Servicio |	Global/regional	| Tráfico recomendado
--------- | ----------- | ----------------------------
**Azure Front Door** |	Global |	HTTP(S)
**Traffic Manager** |	Global |	No HTTP(S)
**Application Gateway**|	Regional |	HTTP(S)
**Azure Load Balancer** |	Global |	No HTTP(S)

## Azure CDN
![Azure CDN](/res/images/azure-cdn.png)

Las redes CDN guardan el contenido almacenado en caché de los servidores perimetrales en ubicaciones de punto de presencia (POP) que están cerca de los usuarios finales, para minimizar la latencia.

Entre las **ventajas** de usar Azure CDN para entregar los recursos de un sitio web se incluyen:
- Mejor rendimiento y experiencia para los usuarios finales, sobre todo a la hora de utilizar aplicaciones donde son necesarios varios recorridos de ida y vuelta para cargar el contenido.
- Gran escalado para mejorar la administración de cargas instantáneas pesadas, por ejemplo, al comienzo de un evento de lanzamiento de un producto.
- Distribución de las solicitudes de usuario y entrega del contenido directamente desde los servidores perimetrales, de forma que se envía menos tráfico al servidor de origen.
