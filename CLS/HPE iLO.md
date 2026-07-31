### Introducción a iLO
![[Pasted image 20260731092834.png]]

- **HPE Integrated Lights-Out (iLO)**: tecnología propietaria de gestión embebida en productos HPE.
- Permite control remoto **aunque el servidor no esté conectado a la red principal** de la organización (de ahí "Lights-Out").
- Viene embebida en HPE ProLiant y HPE Alletra Storage Server.
- Combina un **ASIC propio de iLO** (diseñado por HPE, no de terceros) + su firmware — así HPE controla exactamente qué funciones incluir y evita vulnerabilidades/consumo innecesario.
- Es fundamental para el arranque del servidor; además da monitoreo de salud, gestión de energía y control térmico.

**Versión de ASIC según generación:**
- HPE ProLiant Gen11 → **iLO 6**
- HPE ProLiant Compute Gen12 (la mayoría) → **iLO 7** (algunos modelos usan iLO 6 en ciertas configuraciones — revisar QuickSpecs del modelo)

### Funciones destacadas de iLO
- **Always On Intelligent Provisioning** y **RBSU** (ROM-Based Setup Utility) simplifican el aprovisionamiento y ciclo de vida.
- **HPE Active Health System**: alertas de salud/servicio, historial de configuración, diagnósticos.
- Gestión de energía remota (encendido/apagado desde cualquier lugar) y perfiles térmicos inteligentes.
- **Workload Performance Advisor** (solo en servidores Intel): sugiere mejoras de rendimiento.
- Gestión/actualización de firmware desde iLO.
- **Silicon Root of Trust** + **secure enclave** (este último solo en iLO 7): protección contra malware, ransomware y otros exploits.

### Licenciamiento de iLO
- **iLO Standard**: incluido gratis en todos los HPE ProLiant (MicroServer, ML, DL, RL, Synergy, XD) y en HPE Alletra Storage Servers. No requiere instalación.
- **iLO Advanced** (única licencia opcional actualmente): incluida automáticamente en módulos de cómputo HPE Synergy; opcional en el resto.
  - Agrega **Integrated Remote Console con Virtual Media** que permanece abierta incluso después de bootear el SO (con iLO Standard, la consola se cierra al bootear el SO).
  - Suma métodos de autenticación: Directory Service, Kerberos, autenticación de dos factores.
  - Agrega soporte de cifrado **CNSA** (Commercial National Security Algorithm).
  - Da derecho a **iLO Federation** (gestión remota multi-servidor) — **deprecado en iLO 7**; HPE recomienda usar **Compute Ops Management** en su lugar.
  - El término de la licencia (1 o 3 años) aplica solo al **contrato de soporte**; las funciones avanzadas siguen funcionando después, pero sin soporte de HPE salvo renovación.
  - Las licencias iLO Advanced son **versionless** (mismo SKU sirve en todas las generaciones con iLO).

### Opciones de compra de licencias iLO Advanced
![[Pasted image 20260731092856.png]]

| Tipo                                                   | Recomendado para                             | Entrega                  | Notas                                                                                                                                                                                                            |
| ------------------------------------------------------ | -------------------------------------------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Single-server**                                      | 1 servidor a la vez (hasta ~5-10 servidores) | Física o electrónica     | Física: certificado en papel, se instala en 1 solo servidor (o instalación de fábrica con SKU terminado en **#0D1**). Electrónica: la misma key se puede instalar en tantos servidores como la cantidad comprada |
| **Flexible Quantity License**                          | 11 a 99 servidores en una compra             | Física únicamente        | Una key activa en múltiples servidores; no disponible para Gen12                                                                                                                                                 |
| **Volume / Tracking / AKA (Activation Key Agreement)** | 100+ licencias a lo largo de varios años     | Contrato (1, 2 o 3 años) | HPE entrega una **master key** que activa iLO en cualquier servidor durante el contrato; no requiere registrar keys individuales                                                                                 |

> Se recomienda **registrar** las licencias para acceder a HPE Support Center, alertas de producto y My HPE Software Center (excepto con AKA, que no lo requiere).

### Formas de acceder a iLO
![[Pasted image 20260731092938.png]]

- **Web UI**: vía navegador (Chrome, Edge, Firefox).
- **Línea de comandos**: estándar DMTF SM CLP.
- **Redfish API** (desde iLO 6): API RESTful estándar de la industria para gestión de infraestructura de datacenter; todas las funciones de iLO están expuestas vía extensiones RESTful.
- **Scripting**: se recomienda Redfish; también soportado XML/PERL (compatibilidad legacy) y cmdlets de PowerShell.
- **IPMI**: soportado por compatibilidad, pero HPE recomienda Redfish en su lugar.

**Conectividad de red:**
- iLO recibe IP automáticamente por **DHCP** y se auto-registra en DNS.
- **Dedicated iLO Port** (recomendado): red de gestión "out-of-band" separada — mejor seguridad, disponibilidad y sin interferencia de la red de producción.
- **Shared Network Port** (algunos modelos): comparte NIC con producción — desventajas: tráfico de producción puede afectar a iLO, breves desconexiones (2-8 seg) durante arranque o actualización de firmware de red, limitado a 100 Mbps, restricciones de NIC teaming.
- Algunos modelos requieren un **kit de habilitación de iLO** opcional.
- **Login inicial**: usuario Administrator + password aleatoria impresa en la etiqueta "iLO Default Networking Settings" (se puede cambiar; o pedir SKU de password estándar; o contratar Factory Express para setearla de fábrica).

### HPE iLO 7 Web UI (rediseño)
- **Menú** simplificado, orientado a flujo de trabajo.
- **Layout de tarjetas ("cards")**: cada tarjeta resume info clave sin necesidad de entrar a cada sección (ej. tarjeta de Firmware con gráfico de barras de capacidad del iLO Repository; tarjeta de Security Log con cantidad de eventos).
- **Dashboard personalizable**.
- **Barra de búsqueda** para llegar directo a cualquier configuración.
- **Quick Glance**: estado rápido de energía, salud y seguridad.
- **Remote Console** accesible desde cualquier pantalla (requiere licencia Advanced); desde ahí se monta Virtual Media (ISO local o de un file share remoto).

### iLO como base de las soluciones de gestión de HPE Compute
![[Pasted image 20260731093057.png]]

- **HPE Compute Ops Management** (cloud-native): principal forma de gestionar múltiples servidores.
- **HPE OneView** (on-prem) y **Compute Ops Management – OneView Edition** (cloud): alternativas para casos de uso específicos.
- Todas se apoyan en iLO como base:
  - **Agentless Management 2.0**: permite monitoreo/gestión centralizada **sin agente instalado en el SO** y sin necesidad de abrir el puerto SNMP en el SO.
  - El monitoreo/alertas de hardware funciona **desde que se conecta el cable de energía y de red**, incluso con el SO caído.
  - Comunicación **out-of-band** por la red de iLO (más seguridad y estabilidad).
  - Monitorea CPUs, memoria, temperaturas, ventiladores, controladoras de almacenamiento, discos (incluye módulos de caché) y fuentes de poder.

### HPE Intelligent Provisioning (introducción)
![[Pasted image 20260731093149.png]]
