# Jerarquia de suscripciones de Azure

Con Azure, tu puedes tener multiples suscripciones por cuenta, cada suscripción puede poseer multiples grupos de recursos que a su vez poseen varios recursos que son las bases para tu solución de Azure.

Una **suscripción** es una unidad lógica (digital) de servicios de Azure vinculada a una cuenta que es una identidad de Azure Active Directory (Azuer AD). 
Todo recurso debe tener una suscripción ya que a esta se le hace el cobro del uso de dicho recursos.

A continuación te muestro un par de diagramas que muestra la jerarquia en la que Azure coloca tus recursos

![Imagen de diagrama con letras](res/../diagrama_simple.jpg)

![Imagen de diagrama con ilustraciones](res/../diagrama_imagenes.png)
*Fuente: Microsoft*

La organización puede optar por crear multiples suscripciones por:
1. Mejor control en los gastos
2. Emular la organizacional de la compañia
3. Crear una suscripción por entorno de desarrollo, por solución, por plataforma...
4. Porque existen los **Limites de suscripción** y deben tomarse en cuenta. Estos dependerán de cada recursos. Por ejemplo, el número máximo de circuitos ExpressRoute por cada suscripción es de 10.

No obstante, la organización de estas suscripciones puede ser más compleja y ajustada a las necesidades de tu organización agregando los siguientes componentes:
- **Cuenta de facturación**: es un elemento de línea en la factura que muestra los cargos en los que se incurre ese mes
- **Perfil de facturación**: para configurar varias facturas en una misma cuenta de facturación se crean los perfiles de facturación. Cada perfil de facturación contiene su propia factura mensual y método de pago
- **Sección de factura**: para organizar grupos de suscripciones

Se entiende **factura** como la cuenta que tienes que pagar a fin de mes por el uso de los recursos. Un ejemplo puede ser el recibo de luz de tu casa, te llega cada X tiempo y su costo dependerá de cuanto consumes en ese periodo.

![Imagen de diagrama con letras](res/../diagrama_extendido.jpg)
