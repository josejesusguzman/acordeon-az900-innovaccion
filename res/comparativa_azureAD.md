# Comparativa e información sobre Azure AD y Windows AD

Azure Active Directory | Windows Active Directory
---------------------- | ------------------------
Para entornos de nube | Para entornos fisicos, on-premise o de nube privada
Se usa con las aplicaciones de Microsoft | Se utiliza con Windows Server
Puedes utilizarlo para autenticar a tus usuarios | Se puede sincronizar con Azure AD

## Windows Active Directory Windows AD)
**Para ambientes on-premise de Windows Server**

Generalmente se encuentra aislado del resto del mundo.

Si se requiere comunicación con el mundo externo se hace necesario abrir una gran cantidad de puertos para lograrlo, y posiblemente nos enfrentemos a conflictos de DNS de Internet y nuestra zona interna.

## Azure Active Directory (Azure AD)
**Para ambientes de nube**

Azure AD es un servicio basado en la web que admite múltiples dispositivos y múltiples plataformas, por lo cual no se basa en los mismos protocolos con los que estamos familiarizados en el mundo on-premise, en su lugar se usan protocolos basados en la web tales como: SAML 2.0, WS-Federation, OAuth, OpenID, REST Graph, entre otros.

Azure AD es usado por Microsoft para inciar sesión sus servicios de nube como Microsoft 365 o Microsoft Teams. 

De hecho, la caida que tuvo Microsoft Teams en septiembre del año pasado no fue debido a un ataque malicioso o a una falla en sus servidores, sino a un error en el servicio de Active Directory el cual ocasionaba que los usuarios no pudiesen iniciar sesión. Por ello, si tenias ya una sesión activa no llegaste a ser afectado.

Para más información: [Tweet de Microsoft](https://twitter.com/MSFT365Status/status/1310741317085851649)

![Tweet de Microsoft](/res/images/tweet_microsoft.png)

### Ejemplo de utilidad de Azure AD

Un proveedor de una aplicación corporativa que funciona en la intranet, y en un momento dado el proveedor decide llevar su aplicación a la nube, en ese momento requiere que cada usuario de la aplicación tenga un juego de credenciales (user/password) para poder ingresar a su aplicación recién alojada en la nube.

La siguiente imagen muestra el escenario antes de que el proveedor migrará su aplicación a la nube, con el fin de ofrecer el servicio de la misma a otras empresas, ya "montado" el proveedor en al nube, pronto la aplicación on-premise que utiliza autenticación contra un AD local dejará de ser mantenida por el mismo.

![Imagen Azure AD 1](/res/images/azuread1.png)
*Aplicación on-premise*

Una vez la aplicación fue llevada a la nube el usuario no podrá utilizar sus credenciales de red, es decir; no podrá autenticarse contra AD, en su lugar deberá tener un juego de credenciales que se almacenará probablemente en una base de datos en los servidores alojados en la nube donde se aloja ahora la aplicación, tal como se muestra en la siguiente imagen:


![Imagen Azure AD 3](/res/images/azuread3.png)
*Aplicación en la nube (SaaS)*

Lo anterior obliga a que el usuario tenga que memorizar otro juego de credenciales diferentes a las de red para ingresar a la aplicación, y lo mismo tendrá que hacer no solo con esta aplicación sino con cualquier otra que aplicación externa que el usuario necesite.

![Imagen Azure AD 4](/res/images/azuread4.png)
*Aplicación integrada con Azure Active Directory (AAD)*

Como se puede apreciar en la imagen anterior, el usuario inicia sesión en la aplicación utilizando las mismas credenciales de la red corporativa, gracias a que dichas credenciales están siendo sincronizadas desde el AD local hacia AAD.

Además, en el Portal de Azure puedes encontyrar muchas aplicaciones de terceros que ya se integran con Azure AD.

![Imagen Azure AD 5](/res/images/azuread5.png)

## En conclusión

Básicamente podemos **concluir** que Azure Active Directory es un servicio orientado específicamente al tema de autenticación de aplicaciones basadas en la nube, mientras que Windows Active Directory, es orientado especialmente al mundo on-premise, ya que además de el manejo de identidad y acceso permite la administración centralizada de cambios y configuraciones en una red basada en Windows.