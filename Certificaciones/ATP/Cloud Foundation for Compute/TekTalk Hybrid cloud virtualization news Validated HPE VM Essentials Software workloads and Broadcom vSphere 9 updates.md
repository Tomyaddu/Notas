# TekTalk: Hybrid cloud & virtualization news – HPE VM Essentials, cargas de trabajo validadas y novedades de Broadcom vSphere 9

**Tipo de documento:** Presentación de partner (Partner TekTalk) de HPE, confidencial, sujeta a Acuerdo de Confidencialidad (CDA) — mismas restricciones de uso que el resto de material de partner (no usar como "leave behind" con clientes, no compartir fuera del CDA).

---

### Agenda

1. HPE VM Essentials como alternativa de virtualización – Parissa Mohamadi
2. Gestión de HPE VM Essentials y VMware vSphere – Allan Greentree
3. Cargas de trabajo sobre HPE VM Essentials – Allan Greentree & Denney Liptak (VDI: Omnissa Horizon; bases de datos empresariales: Oracle, SQL Server, MongoDB; protección de datos: Veeam, Cohesity, Cohesity NetBackup/Veritas)
4. Actualización de Broadcom VMware – Eric Siebert
5. Recursos

---

## 1. HPE VM Essentials como alternativa de virtualización

### Contexto: el impacto del cambio de licenciamiento de Broadcom

Los cambios de licenciamiento de Broadcom/VMware generaron una disrupción importante para los clientes:

- Ahora solo se venden **bundles** (VCF, VVF, vSphere Standard).
- Ya no existen licencias perpetuas ni ELAs (Enterprise License Agreements).
- Menor descuento y cargos adicionales (por ejemplo, vSAN).
- El efecto neto es un **aumento de precio de 2 a 4 veces** para la mayoría de los clientes, y de **15 veces o más** en algunos casos.

Esto está acelerando los esfuerzos de re-plataformización y modernización: las cargas de trabajo ya no son "solo VMs". El futuro apunta a una estrategia enfocada en cargas de trabajo (VMs y contenedores combinados), en lugar del enfoque "VM first" del pasado, contemplando también IA y grandes cargas legacy, distribuidas entre edge, datacenter, co-lo y nubes públicas.

### HPE VM Essentials Software: la propuesta de HPE

Se presenta como una nueva solución para **unificar la gestión de VMware y el hipervisor HPE VM Essentials**, con cuatro pilares de valor:

1. **Reducir costos** con el hipervisor integrado HPE VM Essentials: incluye capacidades núcleo como opcionalidad de storage (local, NFS, iSCSI, Fibre Channel), distribución de cargas de trabajo, alta disponibilidad de VM y migración en vivo, protección de datos vía snapshots/backup, y DR con Zerto (integración prevista para 1H 2025).
2. **Simplificar la gestión** entre VMware y HPE: conectar clústeres VMware existentes para gestión y "VM-vending" hacia ESXi y el hipervisor HPE VM Essentials desde una sola interfaz, incluyendo integración de IPAM/DNS, automatización, gestión de secretos y conversión de imágenes de VMware a KVM.
3. **Preparar la infraestructura a futuro** con rutas de consumo y actualización flexibles: disponible como software independiente e integrado en HPE Private Cloud, con posibilidad de escalar a **Morpheus PlatformOps** completo para gestión de nube híbrida, soporte K8s, gobernanza y FinOps.
4. **Reducir riesgos** gracias a soporte de nivel empresarial: construido sobre un núcleo KVM probado, con soporte global de HPE y un ecosistema de ISVs en expansión (protección de datos, VDI, ERP, etc.).

Se aclara que hoy requiere Ubuntu como prerrequisito, y que un instalador integrado llegará en 1H25.

### Disponibilidad: standalone y dentro de HPE Private Cloud

HPE VM Essentials estará disponible tanto como **software independiente** (para hardware HPE y de terceros) como **totalmente integrado** en las soluciones de HPE Private Cloud (gestionadas con Morpheus), dentro de la plataforma HPE GreenLake Cloud Platform, que también contempla despliegues bare metal, contenedores, virtualización y nube pública (con integraciones a Azure, Google Cloud, AWS, Nutanix, Red Hat OpenShift, VMware, Azure Stack HCI, EKS, entre otros).

### Arquitectura de HPE VM Essentials para HPE Private Cloud

Se detalla cómo funciona dentro de PCBE: los nodos HPE VM Essentials alojan las VMs y se conectan mediante un túnel seguro a la HPE GreenLake Platform, con switches Aruba, gestión de ciclo de vida, y almacenamiento sobre HPE Alletra MP Storage. También se muestra el escenario equivalente con **soporte para VMware vSphere**, donde conviven nodos VME y nodos vSphere (gestionados por vCenter), ambos usando el mismo storage compartido HPE Alletra MP.

## 2. Gestión de HPE VM Essentials y VMware

Se explica que HPE VM Essentials Manager permite administrar VMs construidas tanto sobre el hipervisor HPE VM Essentials como sobre VMware vSphere, ofreciendo aprovisionamiento básico, automatización de tareas, orquestación de IPAM/DNS y gestión de secretos.

### Flujo de trabajo para gestionar/convertir VMs de VMware desde VME Manager

Se documenta un procedimiento paso a paso (marcado como _Work In Progress_ en varios puntos, ya que la conversión completa aún está en desarrollo):

1. **Agregar la nube VMware**: iniciar sesión en el VME Manager (requiere rol System Admin), ir a Infraestructura → Clouds → Add → elegir VMware (equivale a agregar un vCenter). Se recomienda usar la IP para la API URL, seleccionar "Inventory Existing Instances" para traer todas las VMs del vCenter, y habilitar la consola del hipervisor.
2. **Convertir a "Managed"**: desde Infraestructura → Compute → Virtual Machines, seleccionar la VM de VMware y elegir Actions → Convert to Managed; luego instalar el agente. El estado pasa de "Discovered" a "Managed VM".
3. **Gestionar desde la instancia VME de VMware**: desde Provisioning → Instances, abrir la VM y gestionarla desde el menú Actions. Advertencia importante: **eliminar una VM gestionada de VMware desde VME también la elimina del vCenter**. "Import as Image" genera una imagen VMDK en VME; "Clone to Image" genera una plantilla en vCenter; "Reconfigure" equivale a "Edit Settings" de vCenter.

Para **convertir VMs de VMware al hipervisor HPE VM Essentials** (marcado como _WIP_, procedimiento actual en VME 8.0.3):

1. **Importar como imagen**: desde la VM de VMware, Actions → "Import as Image"; la imagen VMDK aparece en Library → Virtual Images. Se recomiendan buenas prácticas como nombrar la imagen igual que la VM origen, esperar a que el estado sea "Active", y ajustar opciones avanzadas según drivers VirtIO, UEFI, o ejecutar `dracut` en Linux no-Ubuntu.
2. **Aprovisionar una instancia desde la imagen**: crear una instancia HPE VM eligiendo CPU/memoria/storage equivalentes a la VM original y la imagen VMDK importada; en Windows es necesario adjuntar los drivers VirtIO.
3. **Gestionar desde la instancia HPE VM de VME**: abrir la consola desde Actions. Se documentan pasos específicos para que Windows 10 arranque correctamente cargando manualmente el driver VirtIO (`drvload` y `dism`) si no bootea directamente a la pantalla de login.

## 3. Cargas de trabajo validadas sobre HPE VM Essentials

Se presenta una matriz de cargas de trabajo soportadas, divididas en:

- **Disponibles hoy**: VDI (Omnissa, antes VMware Horizon), bases de datos empresariales (SQL Server, Oracle, MongoDB) y protección de datos (Cohesity, Cohesity NetBackup/Veritas, Veeam — todos con backup basado en agente).
- **Próximamente**: VDI adicional (HP Anyware, Citrix), protección de datos (Commvault), video vigilancia (Milestone) y analítica (Splunk/Elastic). Se aclara que HP Anyware y Citrix aún están en pruebas básicas de interoperabilidad, no recomendadas para producción.

### VDI: Omnissa Horizon

La solución de VDI está en calificación (no recomendada aún para producción, sí para pruebas de concepto). La arquitectura contempla: Active Directory, un dispositivo cliente con Horizon Agent, escritorios virtuales Windows 11 con Horizon Agent desplegados sobre HPE VM Essentials, un Connection Server de Omnissa Horizon, todo corriendo sobre un clúster HPE VM Essentials con storage HPE Alletra MP B10000. HPE VM Essentials se encarga del ciclo de vida y gestión de energía de los escritorios virtuales; la autenticación y el "brokering" quedan fuera del alcance de VME. Se planea validar interoperabilidad con HP Anyware para Q2 FY2025; Citrix VAD está bajo evaluación.

### Bases de datos empresariales

Se aclara una limitación importante: **las VMs de VM Essentials solo pueden acceder a sus propios discos virtuales** (no existe equivalente a RDM ni "Multi-writer" como en vSphere), por lo que no hay operaciones de storage clusterizado a nivel VM. Esto afecta las configuraciones posibles de SQL Server y Oracle. El storage compartido a nivel de host del hipervisor sí está soportado, vía NFS, iSCSI o Fibre Channel (storage compartido) o CephFS (storage convergente).

**Pasos comunes para desplegar bases de datos**: aprovisionar una instancia basada en una plantilla personalizada (subir una ISO del SO a Library → Virtual Images, crear una instancia definiendo CPU/memoria/volúmenes/red, instalar y configurar), y luego capturar la instancia de vuelta a la librería como imagen `qcow2` reutilizable.

- **Microsoft SQL Server / MongoDB**: se puede crear una VM plantilla para levantar nodos de clúster, o crear las VMs desde cero usando la funcionalidad de instancias de VME. Es posible automatizar más la configuración de MongoDB con tareas scripteadas, y configurar replica sets o clústeres shardeados. A futuro se prevé soporte de despliegue tanto virtualizado como en contenedores, y migración de VMs de VMware hacia VME.
- **Oracle DB**: se destacan beneficios como eficiencia de costos por licenciamiento per-CPU (maximiza la utilización de núcleos sin costos extra), optimización de rendimiento mediante distribución dinámica de cargas, alta disponibilidad con migraciones en vivo de VM y storage sin downtime, administración de VM comparable (HA, migración en vivo, protección por snapshots/backup nativo), soporte robusto y diverso de storage, fácil optimización del storage de base de datos, escalado no disruptivo (CPU/RAM/volúmenes en caliente, sin reinicio) y mayor costo-efectividad para SQL Server a escala (licenciamiento por socket vs. por núcleo).
- **Oracle 19c**: se aclara que **no hay soporte de Oracle RAC** (todavía), ya que el storage no es compartido entre instancias.
- **SQL Server 2022**: flujo típico — aprovisionar VM con disco de datos separado, instalar Windows Server 2022, configurar y crear plantilla; luego desplegar instancias desde la plantilla (unir al dominio, instalar agente, etc.) e instalar SQL Server de forma normal. Para alta disponibilidad se recomienda investigar Always-On Availability Groups.
- **MongoDB**: cada shard obtiene su propia instancia (permitiendo escalar), la instancia `mongos` balancea las consultas, y las pruebas se hicieron sobre CentOS 9.

### Protección de datos

- **Veeam**: sin integración nativa aún; solo backup basado en agentes de Veeam.
- **Cohesity y Cohesity NetBackup (Veritas)**: sin integración nativa aún; solo backup basado en agentes.
- **Commvault**: integración nativa prevista para Q2 FY25; hoy ya soporta backup basado en agente (protección granular de apps/datos, con mayor overhead en el host) y a futuro backup basado en imagen (backup/restore de VMs completas a través del hipervisor, con backups completos e incrementales y restauración masiva instantánea a cualquier punto en el tiempo).

Se documenta también la arquitectura de integración del hipervisor HPE VM Essentials con backup KVM (sobre Ubuntu), gestionada desde la UI de VME, cubriendo ciclo de vida de cargas de trabajo, integración con hipervisor, integración de backup e integración de red.

### Matriz de validación de cargas de trabajo

Se presenta una tabla resumen (disponible públicamente en el sitio de soporte de HPE) con partners, producto, versión, SO invitado y tipo de validación, incluyendo: Veeam Backup & Replication 12.3, Cohesity Data Cloud 7.1.2+, Cohesity/Veritas NetBackup 11, Oracle Database 19c (Oracle Linux 8u10), Microsoft SQL Server 2022 (Windows Server 2022), MongoDB Enterprise Advanced 8.0.0 (CentOS 9) y Omnissa Horizon 8.13.1 (Windows 11 Pro/Enterprise y Windows Server 2022).

## 4. Actualización de Broadcom VMware

### vSphere / VCF 9.0

- vSphere 9.0 se lanzó en disponibilidad inicial (IA) el **15 de abril de 2025**.
- VCF pasa de la versión 5.2 a la **9.0**, para alinearse con la numeración de vSphere, y **VCF pasa a ser el nombre de producto principal** y foco de Broadcom (junto con vSphere Standard, Enterprise Plus y vSphere Foundation/VVF).
- Se introduce un **nuevo esquema de versionado**: lo que antes era "update release" ahora se llama "minor release". El formato pasa de `<major>.0.<update>-0.<patch>.build` (ej: 8.0 U2b/P03) a `<major>.<minor>.<maintenance>.<patch>.<build>` (ej: 9.2.0.0, 9.2.1.0).

### Storage externo en VCF 9.0

- VCF 9.0 (GA 15/4/25) permite soporte de storage externo para el dominio de administración **sin necesidad de vSAN**, tanto en 5.2 como en 9.0.
- Soporte end-to-end de bloques de **4K**.
- Mejoras en **vVols**: habilita clustering de invitados con front-end vNVMe y back-end SCSI, y certificación mejorada del proveedor VASA (vVols NextGen).
- **NFS**: soporte de `krb5p` con NFS 4.1 y VAAI Unmap para NFS v3.
- **NVMe**: soporte de autenticación NVMe-oF en ESXi (TP-8006).
- Soporte **greenfield** con VMFS (FC) y NFS, e importación **brownfield** para todas las topologías de storage externo.

### Soporte de vSphere 9.0 en storage de HPE

- HPE Storage soportará VCF 9.0 en la mayoría de las plataformas desde el día 0, **excepto Nimble/Alletra 5000/6000**, que no tendrán soporte de vSphere 9.0 al momento del lanzamiento.
- El plug-in remoto de vCenter para Nimble aún no está listo (estaba planeado para el release "Pebble.700" pero se retrasó); se espera que llegue con el release **"Pismo.100" (Q3)**.

### vCenter Plug-in

- A partir de VCF 9.0, los plug-ins de vCenter **ya no requerirán firma ni certificación**.
- El soporte de plug-ins locales se eliminó; **solo se soportan plug-ins remotos**.
- Próximamente se lanzará **SIP4VC 13.1**, que agrega: restauración a snapshot de lectura/escritura (sin copia completa), implementación de snapshot instantáneo para Nimble/Alletra 6K, visualización de snapshots vVol no gestionados, operación de restauración de snapshot (vVols), y visualización de memoria/swap en vVols.

### vVols NextGen

VMware introduce una nueva certificación **vVols NextGen** en vSphere 9.0, con el objetivo de ofrecer un modelo VASA prescriptivo que garantice una experiencia consistente y optimizada entre plataformas de storage. Agrega requisitos adicionales para los proveedores VASA de los partners: cumplir requisitos de latencia y tamaño de lote para operaciones VASA, alta disponibilidad del proveedor VASA, y capacidad de escalar por encima de **128 conexiones de host** (casos de uso de alto fan-in / escala de nube). La certificación vVols legacy quedará deprecada en 9.0 y se eliminará en el siguiente release mayor. **HPE Alletra MP será la única plataforma certificada para vVols NextGen.**

### Alletra MP: integración vVols de referencia

La habilitación de vVols comienza en el "Release 3" e incluye una arquitectura de vVols rediseñada: múltiples endpoints de protocolo, contenedores de storage mapeados a CPGs, multipathing optimizado y nuevas CLI de gestión. Escala empresarial: hasta **6.000 VMs**, **72.000 vVols** y **8.000 vVols replicados**. Incluye migración de datos rápida y eficiente (Xcopy, con Xcopy extendido en releases posteriores), capacidades de vVols (snapshots por minuto/hora/día/semana, replicación asíncrona, QoS por IO/ancho de banda, reducción de datos con compresión/deduplicación/cifrado, thin provisioning) y mejor gestión mediante plug-ins (gestor de replicación, gestor de snapshots, cuotas de contenedores, dashboard de insights). El roadmap por release incluye: nuevo modelo de certificados (VASA 5.0, Release 4), alta disponibilidad del proveedor VASA (VASA 6.0, Release 5), clustering estirado/stretched (VASA 6.0, Release 6) y soporte NVMeoF (VASA 4.0, Release 4).

### Paridad de funciones entre Nimble y GreenLake for Block

Se compara la tabla de funciones vVols entre **Nimble/Alletra 6000**, **Primera/Alletra 9000** y **GreenLake for Block**: máximo de vVols (10.000 / 42.000 / 36.000), vVols replicados (3.000 / 1.000 / 2.400), compresión y deduplicación (sí en las tres), SRM (400 / 500 / 1.000 VMs), replicación y snapshots (sí en las tres), cifrado (VM / Disco / Disco), NVMeoF (no / no / **sí**), clustering estirado (no / no / **sí, R5**), recycle bin (sí / no / **sí, R5**), iSCSI CHAP (sí / no / sí) y límites de contenedor de storage (sí / no / sí).

### Historia de VASA y soporte de HPE Storage

Se traza una línea de tiempo desde **VASA 1.0** (jul 2011, vSphere 5.0, especificación original basada en strings para VMFS) hasta **vVols NextGen** (vSphere 9.0), pasando por VASA 2.0 (GA de vVols, vSphere 6.0), VASA 3.0 (soporte de replicación, vSphere 6.5), VASA 3.5 (iSCSI CHAP, vSphere 7.0 U1), VASA 4.0 (NVMeoF, vSphere 8.0), VASA 5.0 (nuevo modelo de certificados, vSphere 8.0 U1) y VASA 6.0 (clustering estirado, vSphere 8.0 U3). Se detalla el soporte por plataforma HPE (Alletra MP, Alletra 9000, Alletra 6000/5000, Primera, Nimble, 3PAR) y fechas planificadas (por ejemplo, VASA 5.0 en Alletra 9000 y Primera para Q4-2025, vVols NextGen en Alletra MP para Q2-2025).

### Nueva función de alta disponibilidad del proveedor VASA (R5, VASA 6.0)

Se presenta el diseño de **VASA Provider HA**: failover automático a una instancia sobreviviente si un proveedor falla, cumplimiento con la especificación VASA 6.0 y el programa "vVol Next" de VMware. Todos los VPs (Virtual Providers) ven todos los contenedores de storage, pero solo uno posee todas las llamadas VASA en un momento dado, incluso en entornos multi-host y multi-contenedor. En el primer release, la prioridad de ambos VPs será fija en 255, y se planea un máximo de dos VPs para todos los modelos. A partir de 8.0.3 se soportará el registro de ambos VPs (en versiones más antiguas de vSphere se recomienda registrar solo VP1). El estado de la sesión puede determinarse desde el estado del VP en vCenter.

### vVols Stretched Clustering

En desarrollo para Alletra MP en el **Release 6**. Conceptos clave: un contenedor "estirado" (stretched) es aquel donde el mismo ID de contenedor es reportado por los proveedores VASA en ambos sitios de un metro-clúster; todos los vVols dentro de un contenedor estirado también lo están; un contenedor solo puede estirarse entre dos sitios a la vez (aunque un mismo sitio puede estirar distintos contenedores hacia distintos sitios simultáneamente); ambos arrays exponen el mismo PE (Protocol Endpoint) para un contenedor estirado, lo que implica que ambos exponen el mismo par `{PE, secondary lun id}`; y cada vVol debe estar "bound" (enlazado) en ambos arrays del metro-clúster, permitiendo failover entre rutas y acceso desde cualquiera de los dos arrays del clúster.

## 5. Recursos

Se listan activos públicos y de entrenamiento: presentación de ventas de HPE VM Essentials con cargas de trabajo, technical briefs/blogs/videos de MongoDB, technical brief de SQL Server, technical brief y blogs de Veeam (3 partes), material de Broadcom VMware, soluciones de storage de HPE para VMware, consideraciones de despliegue de vVols y vSphere 8 sobre HPE Alletra Storage MP B10000, despliegue de VMware Cloud Foundation con Alletra MP B10000, y una presentación de Tech Jam sobre despliegue de soluciones de carga de trabajo en HPE VM Essentials.

---

