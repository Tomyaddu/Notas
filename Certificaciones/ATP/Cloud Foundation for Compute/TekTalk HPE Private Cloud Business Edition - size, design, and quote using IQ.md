Los temas que se van a hablar en esta charla son los siguientes:![[Pasted image 20260717133246.png]]
# TekTalk: HPE Private Cloud Business Edition – size, design y quote usando IQ

**Tipo de documento:** Presentación de partner (Partner TekTalk) de HPE, confidencial, sujeta a Acuerdo de Confidencialidad (CDA). No debe usarse como material para dejar con clientes externos; solo puede compartirse verbalmente bajo CDA.

---

### Agenda

1. HPE Private Cloud Business Edition (PCBE) – visión general del portafolio
2. dHCI
3. SimpliVity
4. Configuración
5. Solution Sizer y "cloud modules"
6. Configurar PCBE con Integrated Quoting (IQ)
7. Recursos

### 1. Visión general del portafolio de PCBE

HPE plantea una **arquitectura para cada carga de trabajo**, combinando rendimiento, escala, resiliencia y protección, todo entregado como HPE GreenLake for Private Cloud Business Edition:

- **HPE Alletra Storage MP B10000 (dHCI - Disaggregated HCI)**: pensado para cargas mixtas a gran escala, con latencia predecible sub-milisegundo (10 veces menor), 100% de disponibilidad de datos garantizada, escalado flexible e independiente de cómputo y storage, protección de datos incorporada y movilidad de datos eficiente y global.
- **HPE SimpliVity (All-in-one HCI)**: orientado a cargas de trabajo de propósito general y edge, con alta disponibilidad en el footprint más eficiente y pequeño posible.

Ambas opciones corren sobre servidores **HPE ProLiant DL Gen11**, y se despliegan tanto en datacenter/co-lo como en edge o nube pública.

### 2. HPE SimpliVity: soporte de doble hipervisor

Se explica que SimpliVity ahora soporta dos "stacks" en paralelo:

- **HPE SimpliVity con HPE Morpheus VM Essentials Software** (hipervisor HVM/KVM), gestionado por Deployment/Upgrade Manager de VM Essentials.
- **HPE SimpliVity con VMware vSphere**, gestionado por vCenter y PCBE (VM vending).

Ambas variantes se apoyan sobre la plataforma de virtualización de datos HPE SimpliVity y hardware HPE ProLiant DL325/DL380 Gen11, y utilizan licenciamiento por término (Term-based LTU) para software y soporte.

### 3. Herramientas de configuración ("Smart Templates")

Se muestran las **Smart Templates** disponibles dentro de OCA (One Config Advanced) para configurar PCBE como servicio (aaS), incluyendo el paso de "Acknowledge Billing" en el setup.

Se ofrece **guía sobre cuándo usar cada herramienta de configuración**:

- **Solution Sizer (SSET)**
- **Smart Templates**
- **OCA (One Config Advanced)**

Cada una tiene un caso de uso distinto según la complejidad y el nivel de personalización requerido.

### 4. Solution Sizer y "Cloud Modules"

Se compara la situación **actual** de PCBE frente al modelo de **Engineered Systems** basado en Cloud Modules:

- **PCBE actual**: mucha "optionality" (complejidad de CPQ), no se vende como sistema de ingeniería, los switches de red son opcionales, el sizing no siempre es preciso, y los problemas de BOM (bill of materials) se descubren recién en el despliegue, generando demoras, sobrecostos y problemas de satisfacción del cliente por falta de pre-validación.
- **PCBE como Engineered Systems**: reduce significativamente las opciones de configuración a instancias estandarizadas, con sizing simple basado en VMs (integrado con CloudPhysics y RV Tools), switches ToR incluidos por defecto (los OOB son opcionales), y sizing/entrega conectados y automatizados. Se detalla una tabla con instancias de cómputo (23 en total, entre Compute/General Purpose/Memory Optimized Gen11 y Gen12), red (3 instancias) y storage (2 instancias: Block Basic y Block Business Critical).

El proceso de **Solution Sizer** se resume en **3 pasos**: seleccionar la oferta de PCBE → definir las cargas de trabajo de cómputo, storage y red → revisar la configuración/BOM y exportarla a OCA.

### 5. Configurar PCBE con Integrated Quoting (IQ)

IQ (junto con Flex Solutions) está disponible en **45 países**, agrupados en tres regiones:

- **AMS (NA y LATAM)**: EE. UU., México, Canadá, Chile, Colombia, Puerto Rico, Argentina, Perú.
- **EMEA**: Luxemburgo, Alemania, Reino Unido, Francia, España, Italia, Países Bajos, Bélgica, Emiratos Árabes Unidos, Suiza, Turquía, Dinamarca, Austria, Portugal, Sudáfrica, Suecia, República Checa, Arabia Saudita, Hungría, Finlandia, Polonia, Irlanda, Grecia, Noruega, Israel, Eslovaquia, Rumania.
- **APJ**: Japón, India, Nueva Zelanda, Singapur, Australia, Malasia, Corea del Sur, Tailandia, Hong Kong, Filipinas, Taiwán.

Se incluye una demo en vivo de configuración de PCBE con IQ/Flex, usando en conjunto Smart Templates, OCA y Flex (IQ).

### 6. HPE Private Cloud Business Edition TCO tool

Se presenta como una **herramienta única que cubre todo el recorrido del cliente (customer journey)**:

- **Hoy (V1)**: sirve como disparador de conversación, toma inputs de carga de trabajo basados en VMs y recomienda la configuración de hardware de menor costo, enfocada en la propuesta de valor de HPE Morpheus VM Essentials.
- **Futuro (V2)**: opciones de configuración y sizing más granulares, importación desde CloudPhysics/PCBE Sizer, desglose detallado de costos y análisis competitivo de hardware.

Funcionalidades destacadas de la herramienta (accesible desde NinjaOnline):

- Landing page para elegir entre HPE SimpliVity y PCBE con Alletra MP B1000, ingresar cargas de trabajo basadas en VMs, elegir el término de soporte y ajustar configuraciones avanzadas (ratios de vCPU, reducción de datos, etc.).
- **Widget de comparación HVM vs. competencia**: analiza el costo de HPE Morpheus VM Essentials frente a otros hipervisores populares.
- **Widget de costo a escala**: compara licenciamiento por núcleo (core-based) vs. por socket a gran escala.
- Resumen de hardware y análisis de costos: detalle completo de cómputo y storage de la solución recomendada.
- Otras funciones: reporte descargable con valores de carga de trabajo personalizados, soporte multi-moneda, posibilidad de ajustar la configuración de hardware para ver otras plataformas soportadas, y análisis de costo por VM.

### 7. HPE SimpliVity Sizer

Disponible en NinjaOnline, permite configurar un clúster SimpliVity en varios pasos:

1. **Configurar el clúster**: seleccionar el hipervisor, agregar el clúster SimpliVity y los grupos de VMs bajo el clúster.
2. **Ingresar la carga de trabajo**: parámetros de eficiencia de almacenamiento, crecimiento del clúster, y detalles de la carga de VMs (cantidad de VMs, vCPU total, ratio V-to-P, vMemory total, capacidad total, IOPS y requisitos de backup).
3. **Revisar la solución de sizing**: recomendación del Sizer, resultados del sizing y utilización de recursos.
4. **Resumen de sizing**: con opción de exportar el resumen generado.

### 8. Nuevo SKU base común para SimpliVity (C-Node)

Se anuncia un plan de transición de los nodos A/B a un nuevo **SKU C-Node**:

1. A partir del **2 de febrero**, solo se pueden crear nuevos SKUs C-Node en los sistemas de cotización.
2. Las cotizaciones existentes con SKUs A-Node o B-Node pueden seguir editándose y fabricándose sin cambios durante la transición.
3. A partir del **1 de mayo**, la transición a C-Nodes será completa (los nodos A y B quedarán inactivos).

Se detalla la tabla de equivalencia de SKUs: S2V30A/B → S2V30C (HPE SimpliVity 380 Gen11 8 SFF CTO Node) y S2V31A/B → S2V31C (HPE SimpliVity 325 Gen11 8 SFF CTO Node), además de nuevos SKUs FIO para VMware y VME.

### 9. HPE SimpliVity – Smart Templates

Pasos para usar Smart Templates con SimpliVity: seleccionar el catálogo de Smart Templates (desde CapEx/Buy o aaS) → seleccionar "Hyperconverged" bajo Compute → seleccionar la configuración deseada de la plantilla. Se aclara que el Smart Template para aaS estará disponible próximamente.

### 10. Recursos

Se listan fuentes públicas (sitio web de HPE, videos de YouTube), recursos de HPE y partners (Seismic Briefcase de soluciones de nube privada, PSNow), el HPE Demo Portal, formación técnica sobre PCBE y canales de Slack (de HPE y de partners), además de dos enlaces a actividades de SalesPro para más formación.

---
