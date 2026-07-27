Esta sección nos enseña los componentes de computo, como el procesador, la memoria y almacenamiento. Esta parte va a estar mas enfocada en ProLiant Gen 11 y Gen 12, pero muchas cosas que se van a enseñar acá, son validos para otros servidores.

#### Compute Components Overview

Los HPE Compute incluyen como componentes principales:

- Procesadores: Intel, AMD y NVIDIA Grace Hopper Superchip.
- Memoria: DDR5 Registered DIMMs con funciones avanzadas de RAS.
- Almacenamiento: controladoras de almacenamiento y soporte para unidades M.2 y EDSFF (E3.S).
- Red: adaptadores NIC, HBAs Fibre Channel y ranuras de expansión PCIe Gen5 y OCP para GPUs, DPUs, FPGAs y aceleradores.
- Administración: HPE iLO para gestión remota.
- Energía y refrigeración: fuentes de alimentación y opciones de refrigeración por aire o Direct Liquid Cooling (DLC).

Además, incorporan tecnologías de seguridad como HPE Silicon Root of Trust, Secure Boot, TPM 2.0 y Runtime Firmware Validation.

#### PCIe slots

![[Pasted image 20260724104214.png]]
PCIe (Peripheral Component Interconnect Express) es la tecnología que conecta componentes al procesador a través de la placa madre. Los servidores HPE Compute Gen11 y Gen12 utilizan PCIe 5.0, que ofrece una velocidad de 32 GT/s por carril (lane).

Estos servidores disponen de ranuras PCIe donde se instalan risers para agregar componentes como controladoras de almacenamiento, adaptadores de red (NICs) y GPUs. Los modelos Gen12 pueden ofrecer hasta 12 ranuras PCIe Gen5 x16 para una gran capacidad de expansión.


#### OCP slots

![[Pasted image 20260724104244.png]]
Los servidores HPE ProLiant Compute Gen12 incorporan ranuras OCP 3.0 (Open Compute Project), ubicadas en la parte frontal o trasera según el modelo.

Estas ranuras permiten ampliar la conectividad del servidor mediante la instalación de controladoras de almacenamiento, adaptadores de red (NICs) o GPUs, ofreciendo una configuración flexible según las necesidades de cada carga de trabajo. Los servidores Gen12 admiten hasta dos ranuras OCP 3.0 x16.


#### Procesadores y memorias

##### Procesadores:
![[Pasted image 20260724110334.png]]
Los servidores HPE ProLiant ofrecen una plataforma de cómputo flexible para nube híbrida, IA y cargas intensivas de datos, con configuraciones de 1, 2 o 4 procesadores, según el modelo.

La línea incluye modelos con:

- Intel Xeon (el modelo termina en 0).
- AMD EPYC (el modelo termina en 5).
- NVIDIA Grace Hopper (el modelo termina en 4).

Los Gen11 soportan procesadores Intel Xeon de 4.ª y 5.ª generación y AMD EPYC de 4.ª y 5.ª generación. Los Gen12 incorporan los nuevos Intel Xeon 6, optimizados para mayor eficiencia e IA. Además, el DL384 Gen12 integra el NVIDIA GH200 Grace Hopper Superchip, mientras que el RL300 Gen11 utiliza procesadores Ampere Altra basados en arquitectura Arm para entornos cloud-native.


###### Intel:
![[Pasted image 20260724110535.png]]
Intel utiliza una nomenclatura para identificar las características de sus procesadores Xeon.

- Xeon Gen5 y anteriores:
    - Platinum (8 o 9): máximo rendimiento para IA y cargas intensivas.
    - Gold (5 o 6): alto rendimiento para virtualización y gran cantidad de núcleos.
    - Silver (4): cargas de trabajo generales.
    - Bronze (3): uso de entrada.
    - El siguiente número indica la generación, y los restantes identifican el modelo (SKU). Algunos procesadores incluyen un sufijo que indica características o optimizaciones específicas.
- Xeon Gen6:
    - Desaparecen las categorías Platinum, Gold, Silver y Bronze.
    - El primer número (6) identifica la generación.
    - El siguiente número indica la serie (por ejemplo, 6700 o 6500), donde un número mayor suele representar mayor rendimiento.
    - Los dos últimos números corresponden al SKU, y el sufijo indica el tipo de núcleos del procesador.

 E-Cores VS P-Cores
![[Pasted image 20260724110800.png]]
Los Intel Xeon 6 ofrecen dos tipos de núcleos para adaptarse a diferentes cargas de trabajo:

- P-Cores (Performance Cores): diseñados para máximo rendimiento en centros de datos. Los 6700 ofrecen hasta 86 núcleos y los 6500 hasta 32 núcleos, ambos con Hyper-Threading (2 hilos por núcleo), siendo ideales para aplicaciones empresariales, virtualización y telecomunicaciones.
- E-Cores (Efficient Cores): orientados a eficiencia energética y alta densidad, con hasta 144 núcleos, sin Hyper-Threading. Están optimizados para servicios cloud-native, microservicios y distribución de contenido.

Esta arquitectura permite elegir entre mayor rendimiento (P-Cores) o mayor eficiencia y densidad (E-Cores) según las necesidades de la carga de trabajo.![[Pasted image 20260724112028.png]]
Significado de los sufijos en los procesadroes Xeon 4 y 5 (HPE ProLiant Gen 11)![[Pasted image 20260724112635.png]]
Los servidores HPE ProLiant Gen11 incorporan procesadores Intel Xeon Scalable de 4.ª y 5.ª generación, disponibles en distintas variantes para adaptarse a diferentes cargas de trabajo.

Los sufijos de los procesadores indican el tipo de carga para la que están optimizados, permitiendo configurar servidores para IA, Machine Learning, analítica, nube, edge y telecomunicaciones, equilibrando rendimiento y eficiencia según las necesidades del cliente.

- **H:** optimizado para **bases de datos y analítica**, con alto número de núcleos y aceleradores Intel DSA e IAA.
- **M:** orientado a **transcodificación multimedia**, IA y HPC, optimizado para instrucciones **Intel AVX**.
- **N:** diseñado para **redes, 5G y edge**, priorizando alto rendimiento y baja latencia.
- **S:** optimizado para **almacenamiento** e **infraestructura hiperconvergente (HCI)**.
- **P:** pensado para entornos **Cloud Infrastructure as a Service (IaaS)**, con altas frecuencias y consumo controlado.
- **Q:** procesadores con **refrigeración líquida**, que ofrecen mayor rendimiento manteniendo el mismo TDP.
- **U:** optimizados para **servidores de un solo socket**, aprovechando al máximo un único procesador.
- **V:** orientados a **Cloud Software as a Service (SaaS)**, con mayor densidad de máquinas virtuales por servidor.
- **Y:** incorporan **Intel Speed Select Technology – Performance Profile (SST-PP)**, permitiendo aumentar la frecuencia base cuando se utilizan menos núcleos.

![[Pasted image 20260724113454.png]]

###### AMD

![[Pasted image 20260724113523.png]]
Los procesadores AMD EPYC utilizan una nomenclatura que permite identificar sus características:

- El primer número indica la serie (9000 para las generaciones 4 y 5).
- El segundo número representa la cantidad de núcleos o el rango de núcleos.
- El tercer número refleja el nivel de rendimiento: cuanto mayor es (entre 1 y 6), mayor es la frecuencia. El 7 identifica procesadores de alta frecuencia y los 7 u 8 también pueden indicar modelos con 3D V-Cache.
- El último número identifica la generación: 9004 corresponde a la 4.ª generación (Genoa/Bergamo) y 9005 a la 5.ª generación (Turin).
![[Pasted image 20260724113730.png]]


#### Memorias
![[Pasted image 20260724115333.png]]
Los servidores HPE ProLiant Compute Gen12 ofrecen gran capacidad y ancho de banda de memoria, ideales para virtualización, SAP HANA e IA/ML.

- Soportan hasta 8 canales de memoria y 32 DIMMs (16 por socket).
- Utilizan DDR5, con velocidades de hasta 6400 MT/s en Gen12 y hasta 4800 MT/s en Gen11.
- DDR5 mejora la densidad, rendimiento y confiabilidad frente a DDR4.

La memoria HPE Smart Memory ofrece módulos de 16 GB a 256 GB, mejorando el rendimiento, reduciendo la latencia e integrando HPE Active Health Service (AHS) para detectar y analizar problemas de memoria.

Además, cuentan con Advanced ECC para detectar y corregir errores de memoria y modos RAS (Reliability, Availability, Serviceability) que permiten al BIOS o al sistema operativo gestionar y corregir fallos de memoria.

#### GPUS

