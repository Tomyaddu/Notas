Es una charla que hace un deep dive al DL360, DL380 y ML350. La agenda que nos da es un Overview de la gen 12, hablando mas en profundidad en [[TekTalk Introducing HPE ProLiant Compute Gen12 – Engineered for the hybrid world]]
, este es un pequeño roadmap que nos da como guia: ![[Pasted image 20260706092234.png]]
La siguiente slide que nos da es un pequeño resumen ahora si de la Gen12, hablando un poco de los procesadores Xeon 6 y de ILO 7.![[Pasted image 20260706092439.png]]
El "Energy Star 4.0" es una certificación de energía, la cual podríamos "comparar" con los 80 plus gold/platinum en las fuentes para pcs, pero esta certificación es para servidores y datacenters. A continuación nos deja un slide hablando y comparando los procesadores Xeon 6 con la generación anterior y nos habla un poco mas en profundidad para que sirve los "E-Cores" y "P-Cores".![[Pasted image 20260706093055.png]]
Nos dice que la mayor diferencia es que los "Performance-Core" están diseñados para optimizar el trabajo pesado con IA. Por otro lado los "Efficency-Core" apuntar a ser energéticamente mas costo efectivo, cuando se tiene una gran densidad y volumen de trabajo. La siguiente slide nos enseña como reconocer a los procesadores y que significa cada numero que este mismo tiene.![[Pasted image 20260706093540.png]]
El "SP" es Scalable Processor, comenta en la charla que no están diseñando sus motherboards para soportar "AP Processors", ya que son mas para HPC workloads (Este termino se refiere a cargas muy intensas computacionales. Definición exacta: tareas masivas y complejas que requieren procesar conjuntos de datos inmensos y ejecutar billones de operaciones por segundo). Esto es el segundo numero como se ve en el slide, el primer numero nos marca la generación, el tercer numero es sobre el CPU numbering, y el cuarto numero nos define si es E-core o P-core. Luego nos da un slide sobre los CPU, que se pueden ordenar de generación 12:![[Pasted image 20260706094447.png]]
Algunas dudas sobre los sockets están resueltas en el [[Glosario]]. La siguiente slide nos muestra la evolucion entre Gen10, Gen11 y Gen12 ![[Pasted image 20260706095126.png]]
La siguiente slide nos dice que es una comparación entre servidores que son motherboard desing y mattress desing![[Pasted image 20260706095818.png]]![[Pasted image 20260706095835.png]]
No entra mucho en detalle sobre las diferencia entre los 2, habla un pco del de la izquierda, y nos comenta que el de la derecha se vera en futuras sesiones, pero si nos dice que la diferencia principal es la fuente de alimentación, que viene con MCRPS form factor y que el ILO board viene únicamente con PCSCMIO board, y que en el PCMH design (el de la derecha) viene con un fan board. En la siguiente slide nos muestra el motherboard layout para el monolithic board (El de la izquierda):![[Pasted image 20260706100525.png]]
Nos dice que en el frente tenemos un total de 8 MCIO connectors de derecha a izquierda, cada MCIO ports provides by a PCI Gen 5 list to the front storage. Hay algunos excepciones en el cual los 2U servers se conecten por rear MCIO ports to the front, tambien en los 1U severs, en los casos que tenemos que soportar 20 drives, como en E3S from factor , probablemente tengamos que conectar mas lens from the rear MCIO con un cable al frente. Otro diagrama mas:![[Pasted image 20260706101447.png]]
Un poco sobre el power supply, no da mucha explicación ,solo repite lo que esta en la slide, solo agrega que tiene la certificación energy star 4.0:![[Pasted image 20260706101630.png]]
Nos dice que la ultima tecnología que van a introducir es una la cual sirve tanto a nosotros como partners, como a los clientes cuando estemos construyendo sus configuraciones en OCA, nos comenta que están tratando de agregar una alta escalabilidad para los servidores de Gen12, especialmente en los 1U servers, luego procede a comentar lo que esta en esta slide:![[Pasted image 20260706102042.png]]
Por ultimo nos comenta que esto esta disponible para los productos específicos comentados en esta charla (DL360, DL380 y ML350). nos comenta que esta nueva tecnología en OCA se llama "Smart Chassis" y nos comenta como funciona en mas detalle en el siguiente slide: ![[Pasted image 20260706102329.png]]
Nos comenta que el tracking SKU, que veremos en el smart chassis es el siguiente: ![[Pasted image 20260706102718.png]]
Estos son los controllers que se tendrán en el smart chassis, y nos comenta que tendrán mas controladores mas adelante (Talvez ya tengan mas, toca ver en OCA)![[Pasted image 20260706102820.png]]

---
### DL360

La siguiente parte de la charla habla sobre el server DL360, estos son algunas de las especificaciones: ![[Pasted image 20260706103112.png]]
En la siguiente slide nos muestra las opciones que tenemos para los chassis CTO![[Pasted image 20260706103711.png]]
También nos da una comparación entre las dimensiones, si hay confusion con el tema de SFF y LFF, esta explicado en [[Glosario]] ![[Pasted image 20260706104142.png]]
![[Pasted image 20260706104420.png]]
Vista delantera del DL360:![[Pasted image 20260706104650.png]]
Un poco mas de detalle en cada uno de los 3:![[Pasted image 20260706104849.png]] ![[Pasted image 20260706105004.png]]
![[Pasted image 20260706105018.png]]
Viste trasera del DL360:![[Pasted image 20260706105059.png]]
Vista superior y sus detalles con Air Cooling:![[Pasted image 20260706105336.png]]
Vista superior y sus detalles con Liquid Cooling: Nos comenta que esta pensado para trabajar mejor con un sistema close loop, también nos comenta que tiene un sistema especifico en el que cuando el ILO 7 detecta una fuga en el sistema de cooling, notifica a la herramienta de managment y apago el servidor preventivamente, hasta que se resuelva el problema de la fuga. Se habla mas de esto en [[TekTalk HPE ProLiant Compute (1 of 2) - Options - Gen12 unique technologies and strategies (accelerators, memory, DLC)]] ![[Pasted image 20260706105502.png]]
![[Pasted image 20260706110059.png]]
Hay muchísima información en la aplicación de "HPE Product Bulletin", si hay preguntas consultar ahí.![[Pasted image 20260706110649.png]]
![[Pasted image 20260706110731.png]]
![[Pasted image 20260706110836.png]]
Nos dice que la principal diferencia entre el closed loop cooling entre la Gen11 y la Gen12 es el sistema hablado antes que detecta las fugas, y en esta ultima slide nos da una comparación overall de la generación 11 con la generación 12. También tenemos una comparación con los competidores, la cual nos dice que puede estar desactualizada, pero que en una comparación general contra los competidores  ![[Pasted image 20260706111241.png]]![[Pasted image 20260706111412.png]] 

---

### DL380

Ahora vamos con DL380, empieza comentándonos que muchos de las características que teníamos en Gen11 siguen estando presentes en el Gen12, algunos de los cambios claves es que ahora tenemos la opción de soportar diferentes boots devices and support differents necks(?)![[Pasted image 20260706111905.png]]
![[Pasted image 20260706111948.png]]
![[Pasted image 20260706112146.png]]
![[Pasted image 20260706112318.png]]
![[Pasted image 20260706112346.png]]
![[Pasted image 20260706112502.png]]
![[Pasted image 20260706112519.png]]
![[Pasted image 20260706112616.png]]
![[Pasted image 20260706112738.png]]
![[Pasted image 20260706112901.png]]
Nos comenta que como en el Gen11, tenemos una amplia posibilidad para ampliar la parte trasera![[Pasted image 20260706113001.png]]
![[Pasted image 20260706113405.png]]
![[Pasted image 20260706113436.png]]
![[Pasted image 20260706113554.png]]
DL360 no tiene Closed Loop, ya que no tiene valor tenerlo ![[Pasted image 20260706113809.png]]
Ultima parte donde nos muestra sus diferencias contra los competidores y con su generación anterior:![[Pasted image 20260706113915.png]]
![[Pasted image 20260706114039.png]]


---

### ML350

Nos arranca comentando que la motherboard la comparte con DL360, DL380 y Emerald 350, por esto las características principales son las mismas ![[Pasted image 20260706114420.png]]
En esta generación nos comenta que ya no soportan las memorias satas, únicamente las NVMe![[Pasted image 20260706114737.png]]
![[Pasted image 20260706114935.png]]
![[Pasted image 20260706115004.png]]
![[Pasted image 20260706115044.png]]
![[Pasted image 20260706115143.png]]
![[Pasted image 20260706115302.png]]
![[Pasted image 20260706115439.png]]
![[Pasted image 20260706115637.png]]
![[Pasted image 20260706115710.png]]
![[Pasted image 20260706115737.png]]
