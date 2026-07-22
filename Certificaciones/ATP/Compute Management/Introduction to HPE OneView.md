El objetivo de este curso es darnos el conocimiento general para entender HPE OneView y sus capacidades, los temas a explorar son:
- Positioning HPE OneView
- Managaed resources
- User Interface
- Exploring resources
- Adding networks, storage and server
- Server profile and templates
- Plugins and ecosystem
Vamos a ver como HPE OneView puede resolver todas estas necesidades.

Puntos claves, HPE OneView nos permite:
- Hacer mas con menos, es decir nos permite tener la capacidad de desplegar, manejar y soportar la infraestructura mas eficientemente 
- Los clientes pueden entregar respuestas al instante
- Mantener el servicio sin interrupciones 
- Rápidamente escalar recursos y reorganizarlos 
- Eliminar error humano y remueve la necesidad de hacer tareas mundanas 

Después es una guía de como usar la herramienta, esta presentación se enfoca muchisimo en mostrar la herramientas de OneView, no nos explica mucho como funciona o para que sirve, todo esto esta mucho mejor explicado en [[Effortless Compute Management at Scale]].

Esto es lo que la IA tiene para decir de esta presentación:

### 1. Introducción a HPE OneView

El video forma parte del "HPE Cross Hybrid IT Learning Path" y busca dar el conocimiento fundamental para entender y posicionar HPE OneView y sus capacidades ante clientes, ya sea que tengan pocos servidores en un sitio único o múltiples data centers con demandas cambiantes.

### 2. Posicionamiento de HPE OneView

Se presentan los **desafíos clave** que resuelve la herramienta: hacer más con menos, desplegar/gestionar/soportar infraestructura de forma eficiente, mantener uptime, escalar rápido y eliminar errores humanos mediante templates. Todo esto se logra mediante una **API REST unificada**, habilitando la transformación hacia infraestructura definida por software (software-defined infrastructure). Con templates, una sola línea de código puede describir y componer todos los recursos físicos necesarios (compute, storage, redes), incluyendo configuración de BIOS/boot y seguridad. También permite automatizar actualizaciones de firmware de forma no disruptiva, y monitorear proactivamente la salud de toda la infraestructura (servidores, gabinetes, storage, networking) con alertas antes de que ocurran caídas.

### 3. Accediendo a HPE OneView

OneView está disponible en todo el portafolio de hardware HPE (blade systems, ProLiant, Apollo, Superdome Flex, etc.). En HPE Synergy viene incluido en el appliance de gestión llamado **Synergy Composer**. Se puede acceder vía:

- **GUI**: dashboard con control de acceso basado en roles y en "scope", asignación de tareas/alertas entre el staff, notas para mejorar comunicación en handovers.
- **API REST**: permite integración con herramientas como PowerShell, scripts Python o cualquier sistema que use REST APIs.

### 4. Explorando recursos

Se muestra cómo explorar **servidores** (hardware y perfiles, bays, modelos, puertos, actividad reciente), **redes** (configuración de redes Synergy/blade enclosures, interconnects, vista de mapa), **storage** (creación de volúmenes, pools, snapshots, capacidad utilizada) y la **vista de Data Center** (diagrama de grilla de racks, mapa visual de fabrics y conexiones, integración con HPE Remote Support para despacho automático de repuestos ante fallas).

### 5. Redes

Usando el Synergy Composer como ejemplo, se explica cómo crear **redes Ethernet** (Fibre Channel, FCoE, RoCE o Ethernet), agruparlas en **network sets** cuando la conectividad es compleja, y crear **Logical Interconnect Groups** (definen qué red usa qué puertos para conectarse a los switches top-of-rack), incluyendo uplink sets y puertos de uplink.

### 6. Storage

Se detalla cómo agregar **SAN Managers** (Brocade FOS, Brocade Network Advisor, Cisco, HPE), asociarlos a una red para automatizar el zoning, y agregar **sistemas de storage gestionados** (HPE StoreServ, Primera, Nimble, StoreVirtual). También se cubre la creación de **volúmenes**, snapshots y clones, y el uso de **Volume Templates** para estandarizar la creación de storage (con opción de "bloquear" configuraciones, ej. forzar thin provisioning).

### 7. Servidores

Se explica cómo agregar servidores (por IP de iLO, hostname o rango de IPs) en modo "managed" (requiere licencia iLO Advanced) o "monitored", soportando ProLiant, Superdome Flex y Superdome Flex 280. La pantalla de Server Hardware da una vista detallada de adaptadores de red, procesadores, chasis, fuentes de poder y memoria.

### 8. Server Profiles y Templates

Un **server profile** captura toda la configuración de un servidor en un solo lugar, permitiendo replicarla y modificarla rápidamente. Un **server profile template** actúa como fuente centralizada de configuración para un pool de servidores — si cambia el template, los profiles pueden actualizarse cuando se desee. Esto también aplica a **actualizaciones de firmware**: se define un firmware baseline en el template y todos los profiles asociados lo heredan, dando consistencia.

### 9. Monitoreo de salud de recursos

La página de **Activity** permite filtrar por jobs en ejecución, alertas y tareas (completadas o no), y por severidad (críticas o warnings).

### 10. Ciclo de releases

HPE OneView tiene un ciclo de releases rápido; se recomienda estar en la última versión, o como mínimo en el último **milestone release** (que trae arquitectura de actualización mejorada y facilita futuros upgrades sin saltos dolorosos). Se destaca que el soporte para **Gen11** se implementa enteramente vía **Redfish** (estándar RESTful de DMTF con JSON/OData), sin APIs legacy. El video cierra agradeciendo y remitiendo a más info en el learning path y en HPE Seismic.