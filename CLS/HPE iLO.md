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
**Intelligent Provisioning** es una herramienta integrada en los servidores **HPE ProLiant** y **HPE Synergy** que simplifica el ciclo de vida del servidor, desde el aprovisionamiento hasta el desmantelamiento.

Sus principales funciones son:

- **Instalar sistemas operativos** compatibles y preparar el servidor para el **Service Pack for ProLiant (SPP)**.
- **Configurar** el BIOS, **iLO** y las controladoras de almacenamiento (incluyendo la creación de volúmenes **RAID**).
- **Actualizar firmware** y consultar los registros de **Active Health System (AHS)** para monitoreo y diagnóstico.
- **Crear paquetes de despliegue** para automatizar instalaciones y configuraciones en múltiples servidores.
- **Reaprovisionar o desmantelar** servidores mediante un **Secure Erase**, que elimina los datos siguiendo el estándar **NIST 800-88**.

**Versiones compatibles:**

- **Gen11:** Intelligent Provisioning **4.x** (excepto **4.4**).
- **Gen12 + iLO 6:** **4.4**.
- **Gen12 + iLO 7:** **5.x**.
  

#### Accesing Intelligent Provisioning
![[Pasted image 20260803090832.png]]
Tradicionalmente, **Intelligent Provisioning** se ejecutaba al iniciar el servidor, accediendo con **F10** durante el POST.

Con **HPE iLO**, ahora está disponible en modo **Always On**, lo que permite acceder a sus funciones **directamente desde la interfaz de iLO**, incluso con el servidor encendido.

Aunque existen pequeñas diferencias entre la versión tradicional y **Always On**, ambas ofrecen funcionalidades muy similares para la administración y configuración del servidor.

### UEFI
![[Pasted image 20260803090948.png]]
**UEFI** reemplaza al antiguo **BIOS** en los servidores **HPE ProLiant Gen11 y Gen12**, proporcionando un entorno de arranque más moderno y con mayores capacidades.

Sus principales ventajas son:

- Permite **arrancar desde discos de más de 2.2 TB**.
- Es compatible con tarjetas de expansión que requieren **UEFI Option ROM**.
- Ofrece una **interfaz gráfica (UEFI System Utilities)** para configurar el servidor.
- Incluye una **UEFI Shell** para ejecutar scripts y herramientas antes de iniciar el sistema operativo.
- Soporta **despliegues por red** mediante **PXE**, con compatibilidad para **IPv4 e IPv6**.
- Incorpora funciones de seguridad como **Secure Boot**.

Desde **UEFI System Utilities**, los administradores pueden:

- Configurar dispositivos y hardware instalado.
- Habilitar o deshabilitar funciones del sistema.
- Consultar información del servidor.
- Configurar opciones de memoria.
- Seleccionar el dispositivo o partición de arranque.
- Acceder a otros entornos de configuración antes del inicio del sistema operativo.

### Built-In Security for HPE Compute

#### Introdouction of Silicon Root of Trust (iLO 6)
![[Pasted image 20260803091242.png]]
**HPE Silicon Root of Trust** es una tecnología de seguridad integrada en los servidores HPE con **iLO** que protege contra ataques al firmware.

Su funcionamiento es el siguiente:

- Al encender el servidor, **iLO verifica que su propio firmware coincida con una huella digital (fingerprint) inmutable almacenada en el hardware (ASIC)**.
- Si el firmware es legítimo, el proceso de arranque continúa; si detecta una modificación o malware, **detiene el arranque** para evitar comprometer el sistema.
- Luego, **iLO verifica el firmware UEFI**, y **UEFI**, mediante **Secure Boot**, valida el cargador del sistema operativo antes de iniciarlo.

De esta forma, se establece una **cadena de confianza (Chain of Trust)** que verifica cada etapa del arranque y garantiza que **solo se ejecute firmware y software auténtico**, protegiendo al servidor frente a malware, ransomware y otros ataques dirigidos al firmware.

#### SPDM (Added with iLO 6)
![[Pasted image 20260803091424.png]]
A partir de **iLO 6 (Gen11)**, HPE incorporó **SPDM (Security Protocol and Data Model)** para ampliar la protección de **Silicon Root of Trust**.

Gracias a **SPDM**, el servidor no solo verifica el firmware de **iLO** y **UEFI**, sino también el de otros componentes de hardware, como:

- **CPLD (Complex Programmable Logic Device)**, presente en dispositivos como controladoras de almacenamiento.
- **Dispositivos PCIe**, incluyendo controladoras de almacenamiento y adaptadores de red.
- **Firmware Intel SPS (Server Platform Services)** de los procesadores Intel.
- **UEFI BIOS (System ROM)**, cuya firma digital sigue siendo validada.

En resumen, **SPDM extiende la cadena de confianza** para autenticar múltiples componentes del servidor y garantizar que ninguno haya sido comprometido antes del arranque.

#### Silicon Root of Trust recovery
![[Pasted image 20260803091548.png]]
Además de **detectar firmware comprometido**, **HPE Silicon Root of Trust** puede **recuperarlo automáticamente**.

- Mantiene una **copia segura del firmware** de componentes críticos como **iLO, UEFI, Intel SPS y CPLD**.
- Si detecta que alguno de estos firmwares ha sido modificado o comprometido, **restaura automáticamente una versión confiable**, sin necesidad de intervención del administrador.

En otras palabras, **Silicon Root of Trust no solo detecta ataques al firmware, sino que también recupera el servidor a un estado seguro de forma automática**.

#### Silicon Root of trust with the iLO 7 secure enclave
![[Pasted image 20260803091647.png]]
En los servidores **HPE ProLiant Gen12 con iLO 7**, HPE incorpora un **Secure Enclave**, un procesador de seguridad dedicado, aislado y reforzado que se encuentra integrado dentro del ASIC de iLO. Su función es asumir el primer paso de la cadena de confianza (**Chain of Trust**), validándose a sí mismo y verificando el firmware de iLO antes de permitir que este comience a ejecutarse. De esta forma, incluso si existiera una vulnerabilidad en el firmware de iLO, la cadena de confianza permanece protegida.

Además, iLO 7 mejora el mecanismo de recuperación del firmware. Mantiene **múltiples copias de respaldo** de todos los elementos críticos (almacenadas en diferentes medios, como memoria NOR interna, NOR externa y NAND Flash). Si se detecta firmware comprometido, el **Secure Enclave** —o el propio ASIC de iLO si el enclave no puede ejecutarse— inicia automáticamente el proceso de recuperación para restaurar una versión confiable del firmware. También amplía la validación de firmware a procesadores y dispositivos PCIe o modulares (DC-MHS).

### Beneficios del Secure Enclave

El Secure Enclave proporciona un nivel de seguridad superior durante todo el ciclo de vida del servidor, desde la fabricación hasta el retiro del equipo. Al ejecutarse en un entorno aislado y resistente a manipulaciones, protege especialmente los servidores instalados en ubicaciones donde la seguridad física puede ser limitada.

Entre sus principales ventajas se encuentran:

- **Elimina vulnerabilidades asociadas a la EEPROM externa**, evitando ataques físicos como _chip clipping_ que podrían comprometer el firmware.
- **Gestiona de forma segura claves criptográficas, certificados y credenciales**, actuando como un intermediario de confianza.
- **Permite la transferencia segura de propiedad del servidor** sin necesidad de hardware adicional, ofreciendo funcionalidades similares a un **TPM** integrado.
- Gracias a estas capacidades, los servidores **HPE ProLiant Gen12** son los **primeros servidores estándar de la industria** en cumplir con la certificación **FIPS 140-3 Nivel 3**, uno de los estándares de seguridad criptográfica más exigentes para proteger frente a ataques físicos y lógicos.

#### Additional HPE Compute security features

- **TPM 2.0 (Trusted Platform Module):** Todos los servidores **HPE ProLiant Gen11 y Gen12** incluyen un **TPM 2.0 integrado**, un chip de hardware que almacena de forma segura claves de cifrado, certificados y otra información sensible utilizada para la autenticación y la seguridad.
- **Certificados de identidad del servidor:** Desde **Gen11**, todos los servidores incorporan un certificado **IDevID (Initial Device Identifier)** instalado de fábrica, que proporciona una identidad única y permanente del servidor. En **Gen12 con iLO 7**, también se admite **LDevID (Locally Significant Device Identifier)**, una identidad definida por el cliente. Ambos certificados ayudan a implementar arquitecturas **Zero Trust**, permitiendo autenticar que el servidor es un dispositivo confiable.
- **Server Configuration Lock:** Protege el servidor contra modificaciones no autorizadas creando una **huella digital (fingerprint)** de la configuración, almacenada en el **TPM 2.0**. Durante el arranque (POST), cualquier cambio en componentes como **CPU, memoria (DIMM), dispositivos PCIe, configuración de seguridad o firmware** es detectado y el sistema detiene el inicio hasta que un administrador autorice el cambio mediante contraseña. Puede habilitarse de fábrica mediante **Trusted Supply Chain** o manualmente por el cliente.
- **Chassis Intrusion Detection:** Detecta y registra la apertura o cierre del chasis, incluso si el servidor está apagado, permitiendo identificar posibles manipulaciones físicas. También puede activarse de fábrica con **Trusted Supply Chain**.
- **Algoritmos resistentes a la computación cuántica:** Los **ProLiant Gen12 con iLO 7** incorporan firmas de firmware compatibles con los estándares **NIST** y **CNSA 2.0**, utilizando algoritmos criptográficos diseñados para resistir futuros ataques de computadoras cuánticas, reforzando la seguridad a largo plazo.

#### **HPE Trusted Supply Chain (TSC)**

Es un servicio para clientes que requieren el máximo nivel de seguridad e integridad del hardware. Los servidores se fabrican en una instalación segura de HPE en EE. UU., siguiendo estrictos controles de fabricación, inspección y trazabilidad.

Además, el servidor sale de fábrica con varias medidas de seguridad ya habilitadas:

- **Chassis Intrusion Detection** activado.
- **Server Configuration Lock** habilitado para proteger el equipo durante el transporte.
- **UEFI Secure Boot** habilitado.
- **iLO Security State** configurado en **High Security (iLO 6)** o **Secure Standard (iLO 7)**, utilizando cifrado seguro (AES) para las conexiones web, SSH y la API REST.
- Incluye una logística segura durante el transporte.
- Los modelos se identifican con una **"T"** en el nombre (ej. **DL380T**) y una etiqueta **Trusted Supply Chain**.
- En **Gen12**, HPE añadió **Trusted Supply Chain a nivel de rack**, garantizando también la integridad de racks completos.

---

#### **HPE Server Security Optimized Service (SSOS)**

Ofrece el mismo endurecimiento de seguridad (**hardening**) que Trusted Supply Chain, pero **sin fabricar el servidor en la instalación segura de EE. UU.**

Incluye:

- Chassis Intrusion Detection.
- Server Configuration Lock.
- UEFI Secure Boot.
- iLO Security State en High Security o Secure Standard.

A diferencia de Trusted Supply Chain, este servicio está disponible para **modelos globales**, incluyendo **LATAM, EMEA y APJ**.

---

### Data at Rest Encryption (Cifrado de datos en reposo)

Los servidores **HPE ProLiant Gen12** ofrecen múltiples opciones para proteger los datos almacenados.

**Gestión de claves (Key Management):**

- **HKM (Host Key Management)**
- **LKM (Local Key Management)**
- **RKM (Remote Key Manager)**
- **EKM (Enterprise Key Manager)**

Esto permite adaptar la estrategia de cifrado según las necesidades de seguridad y cumplimiento.

**Tecnología de cifrado:**

- Gen12 utiliza exclusivamente **Self-Encrypting Drives (SEDs)**, donde el cifrado se realiza directamente en el disco.
- Compatible con:
    - **Intel vROC**
    - **HPE Compute MR Storage Controllers**
    - **HPE Compute SR Storage Controllers**
- Algunas funciones pueden requerir licencias y no todas las combinaciones de controladores y cifrado son compatibles.

**Administración del cifrado:**  
Puede realizarse mediante:

- **UEFI**
- **HPE MR Storage Administrator (MRSA)** para controladores MR.
- **Smart Storage Administrator (SSA)** para controladores SR.
- Herramientas de línea de comandos (**SSACLI** y **StorCLI**).
- **HPE iLO**, para administrar de forma centralizada los gestores de claves remotos (RKM).