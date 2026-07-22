Es un video el cual te enseña a como tener una charla con clientes acerca de la generación 12, algo importante de lo que habla es que en [Siesmic](https://hpe.seismic.com/apps/home) hay material, como para tener presentaciones a clientes, o tener mas guías técnicas sobre productos, hay un catalogo grande de cosa.

Comenta también los principales desafíos que los clientes sufren, seguridad vulnerable, una falta de visibilidad e información oportuna (No solo importan tener la información, si no tener la información cuando se necesita), resolver nuevos problemas/cargas de trabajo, ineficiencias (el consumo y costo de energía).

El portfolio de la generación 12 tiene 3 ideas principales, las cuales son Seguridad, Optimización y Automatización. Muchas de estas cosas están descriptas en [[TekTalk Introducing HPE ProLiant Compute Gen12 – Engineered for the hybrid world]]. Algunas dispositivas que vale la pena agregar:![[Pasted image 20260703113659.png]]
Un poco de la explicación de esta dispositiva:
- "Supply Chain Transition": Se refiere a que cuando sale de la fabrica el servidor, entra en una linea de transito de confianza, para tratar de negar que se manipule el server físicamente, antes de llegar a destino.
- "Chassis Intrusion": Utiliza un switch conectado al al system-board del servidor, si el panel de acceso es removido o abierto, manda una señal hacia el chip ILO, graba lo sucedió a través del "Integrated Managment Log" (Es un Log-file de texto, el cual enumera los errores y eventos en el hardware) y manda una señal a la BIOS.
- "Chip Clipping": Se refiere a una técnica de ataque, el cual una persona no autorizada abre el chasis del servidor y conecta una "pinza" directo al chip desprotegido. Esto les permite extraer data o manipular el firmware, el cual les permite leer claves criptográficas sensibles o inyectar código malicioso directamente en la motherboard. La protección que ofrece HPE es una Virtual UEFI ROM, el cual inutiliza este tipo de ataque al hacer que la ROM sea virtual y no tengan lugar físico para llevar a cabo el ataque.

Una de la nuevas innovaciones es el [[HPE Moprheus VM Essentials Software]] .

Estos son los servidores de generación 12 que se lanzaron ![[Pasted image 20260703120736.png]]
Son lideres en refrigeración liquida ![[Pasted image 20260703121311.png]]
Algo interesante que agrega es que el COM (Compute Ops Managment) es que es un SaaS (Software as a service) y esta en la nube. Es una gran solución para ahorrar tiempo en la gestión 