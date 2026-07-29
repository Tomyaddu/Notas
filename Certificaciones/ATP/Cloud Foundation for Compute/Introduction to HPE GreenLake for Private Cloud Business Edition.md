Un breve video explicatorio sobre este tema de 10 minutos![[Pasted image 20260717104405.png]]
![[Pasted image 20260717104431.png]]
![[Pasted image 20260717104743.png]]
![[Pasted image 20260717104801.png]]
![[Pasted image 20260717104938.png]]
![[Pasted image 20260717104944.png]]
![[Pasted image 20260717105000.png]]
![[Pasted image 20260717105051.png]]
![[Pasted image 20260717105151.png]]
![[Pasted image 20260717105217.png]]
![[Pasted image 20260717105312.png]]
![[Pasted image 20260717105422.png]]
# ATR1014 – D11 – PCBE HPE – Handout

## Introducción a HPE GreenLake for Private Cloud Business Edition

**Tipo de documento:** Handout de un curso de formación continua (Continuous Learning) de HPE. Es el material de apoyo de un video, no una presentación para clientes. Confidencial, solo para fines de entrenamiento.

---

### Estructura general

El handout está organizado en 5 capítulos, tal como se anuncia en la slide de contenidos: **Tendencias (Trends)**, **Desafíos de los clientes (Customer challenges)**, **Building blocks (bloques de construcción de la solución)**, **Beneficios (Benefits)** y **Demo**.

### 1. Tendencias del mercado

HPE plantea que los "data-first leaders" (empresas que ponen el dato en el centro de su estrategia) innovan más rápido, se recuperan mejor de ataques de ransomware/ciberataques y le sacan ventaja a la competencia. A partir de ahí, se identifican **tres atributos clave** que deben tener las soluciones para las cargas de trabajo actuales:

1. **Experiencia cloud on-premises impulsada por IA (AIOps)**: gestión simplificada de storage y datos en on-prem, edge y nube pública, con autoservicio.
2. **Infraestructura resiliente y eficiente**: arquitectura escalable pensada para aplicaciones críticas de empresa, que evita el "sprawl" de infraestructura mediante un almacenamiento escalable tipo scale-out (subir, bajar y escalar horizontalmente con facilidad).
3. **Protección y gestión de datos simplificada en entornos híbridos**: dado que la nube híbrida ya es la norma, se necesita una solución que facilite la protección de datos entre entornos.

### 2. Desafíos de los clientes

Los administradores de VMs (VM admins) enfrentan una complejidad creciente de infraestructura que retrasa el time-to-market, sumado a presiones de costos y nuevas demandas de aplicaciones. Las empresas buscan extender su nube privada con una experiencia operativa "as a cloud" pero autogestionada (self-managed). La respuesta de HPE a esto es **HPE GreenLake for Private Cloud Business Edition (PCBE)**, que permite construir una nube privada de autoservicio "on demand", donde se necesite.

### 3. Building blocks (componentes de la solución)

PCBE cambia la forma en que los clientes adquieren y gestionan VMs, llevando la experiencia operativa de nube a entornos on-prem, colocados (co-located) y edge. Los componentes necesarios para usar la solución son:

- Una **cuenta de usuario** en la plataforma HPE GreenLake edge-to-cloud, asociada a una cuenta de empresa.
- Una **clave de suscripción válida** para PCBE.
- Uno o más entornos **HPE Alletra dHCI** (soporta despliegues nuevos o existentes, greenfield o brownfield, OpEx o CapEx, todos gestionables desde la misma instancia de DSCC PCBE).
- Opcionalmente, una **cuenta de nube pública** para aprovisionar VMs en la nube (actualmente el único proveedor soportado es **AWS**).

### 4. Beneficios

Los beneficios se agrupan en tres pilares:

**Simple**

- Gestión "1-stop" de VM a infraestructura en todo el entorno híbrido (VMs on-prem + instancias EC2 de AWS).
- Automatización y autoservicio gestionado con IA para resolver problemas de "Day 2 y más allá", incluyendo actualizaciones multi-sitio con 1 clic.
- Autoservicio ágil, con 6 nueves (99.9999%) de disponibilidad de datos y hasta 8 veces más eficiencia en backups frente a otras soluciones.
- Modelo de cotización y pedido basado en atributos y SLA, con instalación y configuración a cargo de expertos en sitio; el cliente puede operar minutos después de conectarse a la red y paga por uso.
- Diferenciadores clave: panel de gestión y visibilidad global (monitoreo y operación de VMs y clústeres desde un solo lugar) y aprovisionamiento/orquestación de VMs de bajo esfuerzo, con actualizaciones "multi-sitio, multi-sistema" en un clic.
- Las actualizaciones en un clic cubren tanto el firmware de HPE ProLiant como el software/OS de HPE, dando un upgrade de stack completo, no disruptivo y automatizado. Incluye gestión del ciclo de vida de infraestructura VMware, con plantillas de "configurar una vez, aplicar a todos".

**Resiliente**

- Disponibilidad garantizada de seis nueves y latencia sub-milisegundo.
- Sin punto único de falla: tolera hasta **tres fallas de disco simultáneas**.
- Servicios de datos adicionales (deduplicación centrada en VM, cifrado) sin afectar el rendimiento.
- Actualizaciones de ciclo de vida inteligentes en un clic (ESXi, firmware, storage).

**Eficiente**

- Reduce costos, evita capas adicionales de protección de datos y mitiga el riesgo de pérdida de datos gracias a la integración con **HPE GreenLake for Backup and Recovery**.
- Cumple el esquema de protección **3-2-1** (tres copias de datos, en dos tipos de medios distintos, con una copia fuera de sitio), evitando tener que integrar soluciones de terceros.
- Permite recuperación rápida de VMs, incluso a nivel de archivo o carpeta.
- La solución combinada permite aprovisionar, desplegar y proteger una VM en **menos de 3 minutos** con pocos clics.

### 5. Demo

Se muestra una demo de creación de una VM: selección del clúster de hypervisor, selección del datastore de destino, selección de una plantilla de sistema operativo y de una política de aprovisionamiento de VMware (que puede referenciar una política de protección definida en HPE GreenLake for Backup and Recovery). También se muestra cómo aplicar una política de protección a una VM de forma sencilla.

El handout cierra remitiendo a **HPE Tech Pro** para más información.

---

