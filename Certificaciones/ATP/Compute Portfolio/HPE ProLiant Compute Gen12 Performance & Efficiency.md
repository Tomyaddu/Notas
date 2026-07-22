El video habla específicamente del desempeño y la eficiencia en los servidores de generación 12, explica que lo que nos hace ir a una nueva generación de servidores es un nuevo socket de CPU. 

### INTEL

El nuevo socket en la generación 12 es el Xeon 6, es muy importante recalcar que tenemos 2 tipos de cores el tipo E (Efficency) y el tipo P (Performance)

E-Cores: Tienen una gran densidad, están diseñados para darte muchos cores, no tienen un gran desempeño, pero son muy energía-eficiente. el nombre clave de los E-cores son "Sierra Forest". Ejemplo tenemos el 6780E el cual tiene 144 cores, para mas eficiencia. Los E-Cores están pensado para proveedores de servicios, y gente armando su propia nube

P-Cores: Están diseñados para ser muy rápidos, el nombres clave de los P-Cores son "Granite Rapids", usan los procesadores SP. Ejemplo tenemos el 6787P el cual tiene 86 cores. Los P-Cores tendemos a verlos en muchas empresas y para el caso de la mayoría este seria el procesador mas común para elegir.

Intel también tiene una buena opción cuando se trata de un single socket, con un DL340 se puede tener 86 Cores y 2TB de RAM.

Hay una sección en [[TekTalk HPE ProLiant Compute - DL320-DL340 Gen12 Deep Dive]], La cual habla un poco mas en profundidad sobre Xeon 6, muy importante visitarlo para poder teminar de comprender la familia Xeon 6.
### AMD

En AMD no hubo un cambio de socket, simplemente tienen un nuevo procesador llamado "Turin" conocido como Zen 5 o Zen 5C (Mas chico), estos procesadores ya están actualmente en los servidores de generación 11 (DL3X5). Entonces, si se sigue usando el mismo procesador, ¿Por que debería cambiar de generación 11? Una de las razones es que la generación 12 tiene ILO 7 (El cual esta enfocado en la seguridad - [[TekTalk Introducing HPE ProLiant Compute Gen12 – Engineered for the hybrid world]]), también vamos a tener casos en los que vamos a querer acentuar ese socket solitario. Por ejemplo aumentar la capacidad de memoria admitida, por otra parte se supera el TDP máximo con 1 socket solo, de 400W a 500W, es por esto que se puede soportar el ultimo Zen 5C con 192 Cores o el Zen 5 con 128 Cores (No hay mucha diferencia entra Zen 5 y Zen 5C, la principal diferencia es una mayor "clock speed" y mas cache para el Zen 5 (No se diferencian como intel en Efficency y Performance)). Esto nos permite, por ejemplo en un DL345 tener 128 cores con 3TB de ram en 1 solo socket server. Esto por ejemplo tiene mucho beneficio en licencia de software como [[HPE Moprheus VM Essentials Software]] ya que este tiene licencia por sockets, y no por cores.

---

### Cooling


Después de hablar de todo el tema de performance y eficiencia, hay que hablar de otro tema muy importante, que es como se va a refrigerar todo esto, HPE ofrece la opción de DLC (Direct Liquid Cooling). esto se vuelve cada vez mas y mas necesario para los datacenters por múltiples razones, pero algunas de ellas es performance, densidad y eficiencia. Performance, se convierte cada vez mas critico, ya que estamos adquiriendo servidores cada vez mas valiosos, por lo cual queremos que estos servidores vayan lo mas óptimos posibles, y para lograr esto, necesitamos que estén bien refrigerados. Eficiencia, queremos que las cosas corran al menor costo operativo posible, mientras dejan la menor cantidad de huella de carbón 

El siguiente grafico nos muestra las diferencias entre air cooling y liquid cooling, vemos que al tener 1U por aire cooling, tenemos mucho calor emanando todavía, podemos achicar esto al tener un server 2U con el mismo sistema. Pero también podemos tener el Direct Cooling, el cual no baja significativamente su refrigeración, pero si salva muchos costos en el aire acondicionado (Representado por los cuadrados de arriba) ![[Pasted image 20260703144607.png]]




