

FIPS 140-3 Level 3 es un estándar de alta seguridad del gobierno de EE. UU. y Canadá que certifica que un módulo criptográfico (hardware o software) protege datos confidenciales de manera ultra segura

VDI significa Virtual Desktop Infrastructure 

ASIC significa Application-Specific Integrated Circuit y es un microchip de silicona diseñado a medida (ILO 7 es un ASIC)

Un servidor de dos sockets posee dos zócalos físicos (CPU sockets) en la motherboard, permitiendo instalar dos procesadores compatibles. Algunos modelos de procesadores están diseñados para funcionar en configuraciones de uno o dos sockets, dependiendo de la plataforma que soporten.

SAP HANA (High-Performance Analityc Appliance) es un modelo el cual permite guardar información directamente en la RAM, en vez de los discos tradicionales. Esto nos permite tener un procesador super rápido, lo que le permite a las empresas correr tareas transaccionales y tareas de análisis muy complejas en tiempo real.
 
CTO significa "Configure To Order", básicamente vos elegís una base, y luego elegís los componentes internos

BTO significa "Build To Order", básicamente ya viene todo de fabrica configurado

SFF significa "Small From Factor" que se refiere a discos de 2.5 pulgadas (El espacio que se te da en el rack)

LFF significa "Large From Factor" que se refiere a discos de 3.5 pulgadas (El espacio que se te da en el rack)

Rich I/O: I/O significa Input / Output. Rich I/O quiere decir Tiene muchas posibilidades de expansión.

PCIe significa: Peripheral Component Interconnect Express, es el "camino" por donde se comunican, se podria decir que es el protocolo decir "PCIe" a secas

PCIe Lanes, son los carriles que tiene la "autopista" mientras mas carriles mas ancho de banda

OCP significa Open Compute Project son slots especiales pensados principalmente para placad de red, no ocupan un slot PCIe tradicional

Primary Riser es una placa que permite agregar mas slots de PCIe

Secondary Riser es lo mismo pero es el segundo modulo (Si el servidor lo soporta)

OCP Controller, es el controlador que administra los dispositivos instalados en los slots OCP

PCIe Controller, es el controlador que administra los dispositivo PCIe, no suele ser algo que se configure, pero aparece en muchos diagramas

PCIe Slots son las ranuras donde se conectan las tarjetas, como una PC, para tenerlo mas claro es donde va conectada la tarjeta grafica, o la memoria NVE

HCC significa High Core Count, procesadores con muchos núcleos (Normalmente mas de 64 cores)

LCC significa Low Core Count, procesadores con pocos núcleos, pero generalmente con mayor frecuencia, ideal para aplicaciones que necesitan velocidad por núcleo

SKU significa Stock Keeping Unit, es simplemente el código comercial del producto. Por Ejemplo, talvez un DL380 tiene diferentes memorias, diferentes CPU o diferentes fuentes, todas estas variaciones tienen un SKU distinto.

HPE NO VENDE SERVIDORES, vende infraestructura empresarial, los servidores son solamente una parte. Vende literalmente todo:

- Servidores (Ejemplo DL340, DL360, DL380)
- Storage (Ejemplo Alletra, MSA, Nimble)
- Networking (Switches, Routers, WiFi, Aruba)
- Software (GreenLake, iLo, OneView, InfoSigth)
- Servicios (Consultoría, Soporte, Implementación)

DIMMs es el modulo de memoria RAM física

DIMMs Slot, es el espacio donde va la memoria RAM

SAN significa Storage Area Network, es una red exclusiva para conectar storages. No es para trafico normal, solo para almacenamiento.

Hipervisor es un monitor de maquinas virtuales, es una capa de software o firmware que actúa como intermediario entre el hardware físico y múltiples sistemas operativos virtuales

VMware, es un hipervisor, un software que administra las maquinas virtuales. VMware reparte CPU, RAM, discos y red entre todas las maquinas virtuales.

DL significa Density Line, son los servidores en rack

ML significa Modular Line, son torres (parecidas a un PC) y son mas usadas en PyMEs

HBM aparece cuando hablamos de GPUs, significa High Bandwidth Memory



DPC significa DIMMs per Channel, ósea cuantos módulos de memoria hay conectados por cada canal de memoria del procesador 

AP y SP  son los procesadores en nombre clave. SP significa Scalable Processor y se refiere a procesadores Intel. AP en algunos contextos significa versiones especiales de procesadores (AMD).}

NIC significa Network Interface Card y es simplemente una placa de red.

DC-MHS significa Data Center Modular Hardware System, es un estándar de diseño para las motherboards

SED significa Self Encrypting Drive, es un disco que cifra automáticamente todo lo que guarda, su información nunca queda escrita en texto plano. Este disco necesita una KEY para accederse. Cuando halbmoas de SED Devices hablamos de SSD o HDD

MCRPS significa Muti-Connectors Redundant Power Supply, son fuentes redundantes de HPE que, soportan redundancia, hot plug, alta eficiencia y diferentes potencias

Server BMC significa Baseboard Management Controller, es un pequeño computador que vive dentro del servidor y sirve incluso si el sistema operativo muere (o no hay). ILO es un BMC

MRController significa Mega Raid Controller, es un controlador de RAID 1,5,10

 Hot Plug se le dice cuando podes agregar o sacar algo del servidor sin apagarlo.
 
Un Appliance es un sistema diseñado para cumplir una función específica y que ya viene preparado para hacerlo.

Compliance significa que cumple con la función esperada, si hay algo que esta fuera de orden, o que no cumple con la función esperada, decimos que esta "Out of Compliance"

IQ significa integrated Quoting y la sección que habla en profundida esto es [[TekTalk HPE Private Cloud Business Edition - size, design, and quote using IQ]]

Vsphere es el "controlador" de las maquinas virtuales, se encarga de que el uso de la virtualización sea cómoda y fluida, haciendo que las maquinas virtuales que tengan mucha carga, se vayan a otro servidor para que funcionen bien. Una buena analogía es que Vcenter es el "cerebro" que actúa como el controlador principal, y ESXi actua como el motor que hace la virtualización en si. Algo a tener en cuenta es que Vsphere es el nombre del paquete (Vcenter y ESXi), no es una solución aparte, simplemente que cuando hablamos de Vsphere hablamos del paquete completo.

HCI significa Hyper Converge Infrastructure, es el "controlador" de la infraestructura (computación, almacenamiento, redes y virtualización), y la une virtualmente. Esta solución nos permite que tengamos una "nube privada", y agilicemos todas las tareas de virtualización, sin necesidad de instalar hardware en ningún lado (Obviando que necesitamos el hardware del servidor para poder correr todo). 

AI/ML inference es la ejecución practica donde un modelo de IA entrenado aprende patrones para tomar decisiones, hacer predicciones o generar resultados en nueva data nunca antes vista. 