## Actividad 11 : Conceptos de introducción a las redes

### Problema 4: Análisis y diseño de red Peer-to-Peer (P2P)

Escenario: Un startup tecnológico desea implementar una red P2P robusta para permitir el intercambio eficiente de recursos computacionales entre usuarios distribuidos geográficamente. Esta red debe ser capaz de manejar intercambios dinámicos de archivos, distribución de carga, y debe incorporar medidas de seguridad para prevenir accesos no autorizados.
Preguntas:

1. *¿Cómo se diferenciaría una red P2P de una red cliente-servidor en términos de diseño y topología?*
   En una red P2P, todos los dispositivos actúan como clientes y servidores simultáneamente, permitiendo intercambios directos de recursos entre ellos sin depender de un servidor central. Esto crea una topología descentralizada y distribuida, donde cada nodo es igual en importancia y puede comunicarse directamente con otros nodos. Por otro lado, en una red cliente-servidor, los clientes dependen de un servidor central para acceder a recursos, generando una topología más jerárquica y centralizada.

2. *¿Qué protocolos usarías para gestionar comunicaciones e intercambio de archivos en una red P2P?*
   Para el intercambio de archivos, se puede emplear el protocolo BitTorrent debido a su eficiencia y escalabilidad. En cuanto a las comunicaciones entre nodos, se pueden utilizar los protocolos TCP/IP para garantizar la fiabilidad y la transmisión de datos. Además, se puede implementar la encriptación para proteger la seguridad de las comunicaciones.

3. *¿Cuáles son los posibles problemas de seguridad en una red P2P y cómo se pueden mitigar?*
   Los problemas de seguridad pueden incluir ataques de denegación de servicio (DoS), ataques de hombre en el medio (MITM) y la propagación de malware a través de archivos compartidos. Para mitigar estos riesgos, se pueden implementar firewalls para controlar el tráfico de red, encriptación de extremo a extremo para proteger la privacidad de las comunicaciones y software antivirus para detectar y eliminar el malware.

4. *¿Cómo gestionarías el balanceo de carga al incorporar nodos que actúan como clientes y servidores?*
   Al incorporar nodos que actúan como clientes y servidores en una red P2P, es importante gestionar el balanceo de carga para evitar el uso desigual de los recursos. Esto se puede lograr utilizando algoritmos de balanceo de carga que distribuyan equitativamente las solicitudes entre los nodos disponibles. También se pueden aplicar técnicas como el almacenamiento en caché para reducir la carga en los nodos más activos y mejorar el rendimiento del sistema en general.

