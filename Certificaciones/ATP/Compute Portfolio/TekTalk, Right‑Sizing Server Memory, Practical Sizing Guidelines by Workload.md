Esto es un poco de los temas que se va a hablar en esta charla![[Pasted image 20260706125351.png]]
Uno de los principales problemas ahora mismo con las DRAM, es la gran demanda y la baja producción de la misma, esta charla trata de darnos una guía practica de como sacar el mayor provecho a las DRAM. Vamos a tener principalmente 2 líneas de pensamiento cuando tratemos de sacar el mayor provecho ![[Pasted image 20260706125915.png]]

 - Optimización:
 Para entender como optimizar toda nuestra DRAM disponible, primero tenemos que entender como funciona la carga de trabajo, las cargas de trabajo están separados en que tan densas sean, tenemos ligeras, medianas y pesadas. La siguiente slide es un mapa conceptual de que deberíamos hacer para poder sacar el mejor provecho a las DRAM: ![[Pasted image 20260706130325.png]]

- Targeted Workloads:
Nos dan una comparación conceptual, de que no todas las cargas de trabajos son iguales, nos dan este ejemplo con los autos, no todos están hechos iguales, su función es la misma, llevarnos de punta A a punto B, pero la pregunta es ¿Cuál de todos los autos es el mas adecuado para el trabajo? Lo que nos quiere dar a entender con esto es que, a veces es mas igual de importante como voy a llegar de punta A a punto B, a comparación de solo llegar (que vendría ser el objetivo final)![[Pasted image 20260706130817.png]]
Acá tenemos un "Spectrum" de los servidores el cual nos va mostrando que servidor es optimo para cada carga de trabajo![[Pasted image 20260706130939.png]]
Un punto interesante que toca, es que a veces la gente tiende a sobre provisionar en termino de RAM, y que deberíamos de calcular la carga de trabajo sin tener en cuanta el sobre provisionamiento ![[Pasted image 20260706131058.png]]
La siguiente slide nos muestra un grafico conceptual, el representa frecuencia sobre memoria, y nos dice que con la misma capacidad, talvez puedo tener diferentes frecuencias, o que con la misma frecuencia puedo tener diferentes capacidades  ![[Pasted image 20260706131634.png]]
Nos explica de nuevo, que no todas las cargas de trabajo están pensadas iguales y uno de los conceptos mas importantes que tenemos que tener en cuenta es que el concepto de los GB/Core, cuantos GB/Core necesito en la CPU, para poder cumplir con mis necesidades. Esto por ejemplo es algo muy usando cuando hablamos de virtualización, básicamente todas las maquinas virtuales necesitan en promedio cierto numero de GB/Core.![[Pasted image 20260706132414.png]]
Nos dan una guideline general, la cual saco AMD hace unos años sobre sus CPUs, la cual dice que esta buena tenerla en cuanta como para entender el concepto general de que necesitamos para cada workload ![[Pasted image 20260706132653.png]]
A continuación nos da un ejemplo, el agarra un workload especifico que le pide 8 GB/Core y empieza a hacer una matemática simple, que nos va a servir para calcular a gran escala nuestra necesidad sabiendo que tipo de carga de trabajo tienen (Cabe aclarar que este tipo de optimización esta pensada para optimizar Capacity/Core, a conticnuación veremos como se hace Candwith/Core):![[Pasted image 20260706132945.png]]
Nos explican que este método de Capacity/Core es lo mas utilizado, por que es muy fácil saber cuanto es tu capacity en cualquier maquina, corres un comando con linux o windows y te dice cual es tu capacidad y entonces es mucho mas fácil calcular. Nos deja un grafico bastante complejo, en el que en resumidas cuentas nos quiere decir es que al tener una cuenta baja de cores podemos ser mas flexibles con el bandwidth ![[Pasted image 20260706134324.png]]![[Pasted image 20260706134231.png]]
Tambien tenemos otro grafico de latencia:![[Pasted image 20260706134525.png]]
Tenemos los mismos gráficos pero para AMD (El anterior era de intel), la diferencia principal es que intel nos da un 50% de utilización con core bajos, en cambio AMD nos da casi un 75% de utilización ![[Pasted image 20260706134801.png]]
![[Pasted image 20260706134811.png]]
¿Que significa realmente todos estos graficos? Nos están dando a entender que realmente debemos fijarnos en la cual es el objetivo del cliente.

- Strategic de-optimazing:
Para finalizar llegamos a la parte de "Strategic de-optimazing", una de las estrategias que nos da es no utilizar la DRAM como el storage mas optimo, si no que dejarlo en otro lugar, para poder tener mas DRAM para otras tareas![[Pasted image 20260706135349.png]]
Nos dejan también una pirámide que nos rankea el memory performance![[Pasted image 20260706135548.png]]
Básicamente nos muestra que abajo de la RAM tenemos la memora NVMe, y se hace la pregunta de si simplemente esta un tier debajo de la RAM, podríamos utilizarlo para poder de-optimizar algo que este usando memoria RAM, y lo hagamos usar la memoria NVMe. A lo que nos responde diciendo que estan experimentando de usar una combinación de ambas, la DRAM y la memoria NVMe, y que en algunos casos están recomendando usar esta combinacion para algunas cargas de trabajo![[Pasted image 20260706135913.png]]
Estos son algunos de los resultados que HPE saco de probar esta combinación:![[Pasted image 20260706140000.png]]
También nos deja en claro que obviamente, siempre es mejor conseguir toda la DRAM que podamos para el trabajo necesario, pero con los precios que hay y con la baja producción es una buena "out of the box" idea para solucionar estos problemas , que obviamente no es tan optimo como usar DRAM para todo lo que necesitamos, pero que te da un performance aceptable.

También tenemos unas ultimas estrategias que nos dejan listadas para tener en cuenta:
![[Pasted image 20260706140300.png]]
![[Pasted image 20260706140604.png]]
