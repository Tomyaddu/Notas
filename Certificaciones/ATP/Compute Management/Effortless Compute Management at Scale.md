Estos son los temas que se van a abordar en esta presentación ![[Pasted image 20260713130831.png]]

### Recap de Compute Software Portfolio

Nos comenta que hay muchas cosas que están muchas cosas en HPE y están trabajando duramente para simplificar las herramientas de server managment, nos hace un recap de las herramientas que tienen y que van a seguir estando en funcionamiento ![[Pasted image 20260713131238.png]]
Nos comenta que ILO es un "built-in server" managment solution, nos comenta que después van a hablar un poco mas en profundidad sobre ILO, nos comenta igual que tengamos en cuenta que ILO es el corazón de todo, luego tenemos la opción de manejarnos o con COM o OneView. Nos dice que la herramienta de ILO es muy buena, pero cuando cuando tenemos que manejar 4 o 5 servers necesitamos una herramientas mas robusta para manejar los servidores. 

Acá es donde entra HPE OneView es la solución "on-prem" server management, es una herramienta "legacy-based" el cual corre en una VM, es excelente para manejar muchos racks y muchas filas de servidores en el lugar (por eso "on-prem").

Compute Ops Management (COM) por otra parte es una solución "cloud-base" o una SaaS y con esto vienen unas ventajas únicas, como es una SaaS siempre esta actualizada. Es ideal para clientes que tiene que lidiar con entornos distribuidas , pongamos como ejemplo, que el cliente tiene algunos servers en un data center, algunos edge servers, y tiene incontables sitios remotos, o talvez todos estos servidores no están en 1 solo país y talvez necesitan ver el panorama entero de todos los servidores, en una sola pantalla y COM le ofrece esto mismo.

Nos comenta que estas 2 soluciones no pueden coexistir en el mismo servidor, pero tenemos una solución entre media la cual es un "add-on" llamada COM OneView edition, lo que intenta hacer esta solución es mostrarnos todas las aplicaciones de OneView y los servidores manejados por OneView en COM. Esto nos permite manejar nuestros servidores en COM con normalidad, pero cuando toca los servidores de OneView, solo podemos verlos y nos da muchísima información, pero no podemos manejarlo desde esta herramienta, vamos a tener que ir a OneView 


### Deep Dive into ILO

En esta parte nos da un recorrido sobre las innovaciones que trae ILO 7 en la linea de ProLiant servers, nos comenta que tiene un nuevo ASIC, este es un pequeño Recap:![[Pasted image 20260713133859.png]]
Nos comenta que tiene una arquitectura totalmente nueva de firmware, tiene un procesador mas potente, una expansión de memoria y de almacenamiento, lo que nos da mas performance para características nuevas como el "Secure Enclave", muchas de estas cosas están explicadas mejor en [[TekTalk Introducing HPE ProLiant Compute Gen12 – Engineered for the hybrid world]], acá nos deja con la arquitectura del ILO 7 y nos comenta un poco mas sobre el "Secure Enclave"![[Pasted image 20260713134706.png]]
Algo interesante que agrega, es que si al iniciar la validación falla, entonces el "Secure Enclave" inicia la recuperación automática desde un punto en el que el firmware no fue comprometido, entonces esto hace virtualmente imposible poder corromper la firmware. Para resumir un poco, esto nos asegura que si el atacante consigue acceso al servidor principal, ILO 7 nos deja tranquilos de que la seguridad no fue vulnerada del todo. En el siguiente slide nos deja la evolucion entre La gen11 y la gen 12 en termino de Silicon Root of Trust (SRoT). Vuelvo a insistir, mucho de las cosas habladas aca, ya se hablaron en [[TekTalk Introducing HPE ProLiant Compute Gen12 – Engineered for the hybrid world]], así que dejo las slides como Recap ![[Pasted image 20260713135508.png]]
![[Pasted image 20260713142407.png]]
![[Pasted image 20260713142515.png]]
 SPDM significa Secure Protocol and Data Model, es un estandar creado por el DMTF (Organizacion que define muchos estandares), básicamente nos dice que lo que estamos conectando sea autentico, una vez que lo confirma, nos deja usarlo. lo que nos quiso decir el presentador es lo siguiente: En Gen12 ampliamos el uso de SPDM. Antes solo autenticábamos algunos dispositivos como almacenamiento y red. Ahora también autenticamos el Host Processor Module, los backplanes, los PCIe Risers y las fuentes de alimentación. Gracias a esto, iLO puede verificar criptográficamente que todos esos componentes son genuinos antes de permitir que el servidor los utilice, aumentando la seguridad de toda la plataforma.
![[Pasted image 20260713142805.png]]
Nos Habla ahora un poco sobre la nueva experiencia de usuario en el nuevo ILO 7 y como rediseñaron todo desde 0 ![[Pasted image 20260713143335.png]]
![[Pasted image 20260713143521.png]]
![[Pasted image 20260713144056.png]]
![[Pasted image 20260713145008.png]]
![[Pasted image 20260713145025.png]]
![[Pasted image 20260713145301.png]]
![[Pasted image 20260713145536.png]]
![[Pasted image 20260713145843.png]]
![[Pasted image 20260713150223.png]]
![[Pasted image 20260713150654.png]]
