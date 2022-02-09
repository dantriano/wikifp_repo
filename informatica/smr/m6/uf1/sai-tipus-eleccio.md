---
title: SAI: Tipus i elecció
description: 
published: true
date: 2021-10-10T00:20:48.659Z
tags: sai
editor: markdown
dateCreated: 2021-08-24T17:04:09.166Z
---

- :notebook_with_decorative_cover: **Cicle/Modul**: Sistemes MicroInformatics / M6. Seguretat informatica
- :calendar: **Durada**: 12h
- :computer: **Material necessari**:PC, Arduino, projector
- :busts_in_silhouette: **Agrupació**: Per treballar en grup o individualment

###
- [:cinema: Presentacions *Powerpoints i projeccions*](#presentacions) 
- [:orange_book: Apunts *Contingut de teoria*](#apunts)
- [:pencil: Exercicis *Repositori d'exercicis per prácticar*](#exercicis)
- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}


# :cinema: Presentacions
<p align="center"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSgQqLe1HacW-oR1NTJ26EY_09fK8ODo_8EhOnFdq8BX2uK16zSt79N4W4GMAFzemJ7uwzKQWKEm9hZ/embed?start=false&loop=false&delayms=60000" frameborder="0" width="700" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></p>

# :orange_book: Apunts
Los **sistemas de alimentación ininterrumpida (SAI)** son dispositivos de que permiten que en caso de fallo elecrtrico no se dañen los dispositivos conectados a causa de picos de tensión y ademas permite mantener el suministro electro durante un breve tiempo para que puedan apagarse los aparatos correctamente en caso de que se vaya la luz.

## Tipos de SAI
Podemos comprar 3 tecnologías de SAI:

- Sais Off-Line
- Sais Interactivos
- Sais OnLine

### Sais Off-Line

En un SAI Off-Line la corriente eléctrica está pasando sin ningún filtro a los dispositivos ya que no disponen de AVR integrado. El SAI únicamente empezará a funcionar cuando detecte un fallo de corriente, en ese momento, casi instantáneamente comenzará a suministrar la energía que ha ido almacenando en sus baterías. Estos Sais son solo recomendables para las zonas que disponen de una red estable ya que al no realizar ningún filtrado de la corriente, solo protegen ante una interrupción brusca de la corriente ( apagón eléctrico )

**Aplicaciones**: zonas con pocas perturbaciones y red eléctrica de buena calidad.

![esquema_sai_off-line.jpeg](/informatica/m6/esquema_sai_off-line.jpeg){.align-center}
<kbd>Imagen 01: Diagrama de funcionamiento de un SAI Off-Line.</kbd>{.text-center}
### Sais Interactivos
Un SAI Interactivo es parecido al SAI Off-Line pero incorpora un microprocesador que controla las fluctuaciones de la red en ±15%, regulando la tensión de salida (efecto Buck/Boos AVR Integrado), este proceso de filtrado y mejora continua de la corriente que llega a los dispositivos conectados al SAI se realiza sin que entren a funcionar las baterías, por lo que la protección con un SAI interactivo es mayor aún sin sufrir apagones. En el momento en que se detecta un corte de corriente empiezan a funcionar casi instantáneamente las baterías para evitar que el ordenador se apague. Debido a sus características técnicas y rango de precios, el SAI interactivo es el considerado como adecuado para equipos de gama baja y media.

**Aplicaciones**: Ordenadores gama media y baja, consolas de juegos, pequeños servidores de redes, equipos de oficina, etc.
![esquema_sai_interactivo_1_.jpeg](/informatica/m6/esquema_sai_interactivo_1_.jpeg){.align-center}
<kbd>Imagen 02: Diagrama de funcionamiento de un Interactivo</kbd>{.text-center}

### Sais OnLine
Por último está el SAI On-Line, que realiza una doble conversión de la energía eléctrica que recibe, transformándola en continua y después a alterna de nuevo, eliminando de esta manera todos los problemas que pueda tener. Un Sai On-Line siempre proporciona energía eléctrica directamente desde sus baterías mientras estas se van cargando de la red, y esto es lo que garantiza que la protección contra cualquier problema de la red eléctrica sea total. Debido a su alta fiabilidad, la tecnología On-Line ocupa el sector profesional en el mercado de SAIS y está generalmente destinada a proteger servidores, equipos industriales o cualquier instalación informática que por su importancia o coste necesite la seguridad de no verse afectados por problemas derivados de la red eléctrica.

**Aplicaciones**: servidores, clusters de equipos, y en general instalaciones informáticas críticas o imprescindible (redes de datos, servidores,telecomunicaciones, industria, etc.). Diagrama de funcionamiento de un Online
![esquema_sai_online.jpeg](/informatica/m6/esquema_sai_online.jpeg){.align-center}

<kbd>Imagen 03: Diagrama de funcionamiento de un SAI Online.
</kbd>{.text-center}

### ¿Qué tipo de sai debo elegir?
Una vez vistas las características generales de cada una de las tecnologías existentes, serán las particularidades de nuestra red eléctrica y la importancia o coste de los equipos que queramos proteger lo que nos debe indicar que típo de SAI es el más adecuado para nosotros.

**Sais Off-Line**: zonas estables, con pocas perturbaciones y red eléctrica de buena calidad. Orientado a pequeñas instalaciones.

**Sais Interactivos**: Ordenadores gama media y baja, consolas de juegos, pequeños servidores de redes, equipos de oficina. Recomendado para la mayoría de dispositivos.

**Sais On-Line**: Servidores, clusters de equipos, y en general instalaciones informáticas críticas o imprescindible (redes de datos, servidores,telecomunicaciones, industria, etc.).

## Potencia de los SAI
A la hora de elegir un SAI es importante conocer como funciona su calculo de potencia así como la potencia que consumiran nuestros dispositivos para saber el tiempo que se mantendrá encendidos en caso de apagón.

### ¿Qué capacidad de SAI necesito?
La unidad de “potencia aparente” que encontramos en los Sais es el Voltiamperio (Va) ya sea expresado en unidades (1000 Va) o en unidades de millar, el KiloVoltioampério (KVa), también llamado Kavea ( 1KVa = 1000 Va ) que es usado para Sais de potencia/capacidad medios-altos. Sin embargo, la mayoría de los aparatos que conectemos al Sai tendrán expresado su consumo en vatios (w), por lo que para poder realizar una estimación correcta del Sai que necesitamos, se incluye en las fichas de cada SAI una equivalencia de los Voltiamperios (Va) en vatios (W).

> La capacidad de un SAI es: 3000Va / 2400W
{.is-info}


Debido a posibles picos de consumo de los aparatos conectados al Sai, se recomienda siempre elegir un SAI con una capacidad de suministro un 20% mayor que el consumo que vamos a proteger. Tan solo necesitamos conocer la suma de los consumos en vatios de cada uno de los aparatos que necesitemos proteger y sumar a ese total un 20%, esa cantidad serán los vatios que nuestro Sai deberá ser capaz de suministrar. 

> Supongamos que necesitamos conectar al SAI un solo ordenador con un consumo máximo de 400W.
> 
> Total consumos de los aparatos a proteger por el SAI: **400W**
> 
>Total consumos + 20% : **480W**
>
>**El sai adecuado debería tener una capacidad de suministro de al menos 480W**
{.is-info}

En el siguiente cuadro se indican los consumos medios estimados de los dispositivos más frecuentemente conectados a un SAI, aunque existen demasiadas variables para poder indicarlas todas, puede ser una guía efectiva de consumos aproximados.
![cuadro_consumos_sai.jpeg](/informatica/m6/cuadro_consumos_sai.jpeg){.align-center}
<kbd>Imagen 4: Consumos aproximados de equipamiento más frecuente.</kbd>{.text-center}


### Mantenimiento de un SAI

- No sobrecargue el SAI. Se aconseja un máximo de un 70% de carga sobre la capacidad del SAI.
- No conectar dispositivos electrónicos domésticos como ventiladores, impresoras o Faxes. Podrían causar daños al SAI.
- Situar el SAI en un lugar protegido de la humedad, polvo y cambios extremos de temperatura.


> Podemos observar que no existen impresoras en el cuadro anterior, aún siendo dispositivos muy comunes. La razón es que las impresoras **NO deben ser NUNCA conectadas a un SAI**, ya que al encenderse o durante su funcionamiento pueden emitir grandes picos de corriente que podrían dañar al SAI.
{.is-warning}

### ¿Cuanto tiempo puedo mantener mis equipos encendidos con un SAI?
A este lapso de tiempo es lo que denominamos “Tiempo de autonomía de un SAI” y es variable dependiendo del modelo, capacidad de suministro, carga conectada..etc. Encontrarás una estimación de la autonomía de cada modelo en su ficha de producto. En este punto queremos indicarte que una buena práctica cuando existe un apagón eléctrico es aprovechar el tiempo que nos brindan los SAIS para grabar, ordenar y apagar adecuadamente los dispositivos conectados, intenta no “exprimir” al máximo el tiempo de autonomía de tu SAI, ya que si terminas por agotar la energía de las baterías podrías acabar sufriendo también un apagón del SAI.

### La confusión entre Watios (W) y Voltios-Amperios (VA) y el factor de potencia

La potencia consumida por un equipo de computación es expresada en watios (W) ó Voltios-Amperios (VA). La potencia en watios es la potencia real consumida por el equipo. Se denomina Voltios-Amperios a la “potencia aparente” del equipo, y es el producto de la tensión aplicada y la corriente que por él circula.

Ambos valores tienen un uso y un propósito. Los watios determinan la potencia real consumida desde la compañía de energía eléctrica y la carga térmica generada por el equipo. El valor en VA es utilizado para dimensionar correctamente los cables y los circuitos de protección.

En algunos tipos de dispositivos eléctricos, como las lámparas incandescentes, los valores en watios y en VA son idénticos. Sin embargo, para equipos de computación, los watios y los VA pueden llegar a diferir significativamente, siendo el valor en VA siempre igual o mayor que el valor en watios. La relación entre los watios y los VA es denominada “factor de potencia” y es expresada por un número (ejemplo: 0.7) ó por un porcentaje (ejemplo: 70%).

> El valor del consumo, en watios, para un ordenador, es típicamente 60 a 70% de su valor en VA
{.is-info}


Virtualmente todas las computadoras modernas, utilizan una fuente de alimentación de tipo conmutada con un gran condensador de entrada. Debido a las características de éstos convertidores, éstas fuentes de alimentación presentan un factor de potencia de 0.6 a 0.7 , tendiendo las computadoras personales a 0.6. Esto significa que los watios consumidos por un ordenador típico son aproximadamente el 60% de su consumo medido en VA.

Recientemente fue introducida al mercado un nuevo tipo de fuente de alimentación, llamada fuente conmutada con factor de potencia corregido. Para éste tipo de fuente, el factor de potencia es igual a 1. Este tipo de fuente es utilizado en grandes servidores, usualmente con consumos sobre sobre los 500 watios. La mayoría de las veces, no será posible para el usuario determinar el factor de potencia de la carga, y por lo tanto deberá asumir el peor caso cuando calcule la potencia necesaria para un equipo de protección.

### Los valores de potencia de un SAI
Un SAI (sistema de alimentación ininterrumpida) también tiene valores en watios y en VA y ninguno de ambos (ni watios, ni los VA) puede ser excedido.

En muchos casos, los fabricantes solamente publican la potencia en VA del SAI. Sin embargo, es un estándar en la industria, que su valor en watios es aproximadamente el 60% del valor en VA, ya que es éste el valor típico del factor de potencia de las cargas. Por lo tanto, como un factor de seguridad, se debe asumir que la potencia en Watios del SAI es el 60% del valor publicado en VA.

### Calculo de autonomia

Antes de analizar como calcular la autonomia de un SAI en función de los dispositivos conectados vamos a ver todos los conceptos que es importante tener en cuenta:

|Simbolo|Concepto|Descipción|
|---|---|---|
|V| Voltios | Es la tensión que ofrecen las baterías. Es una constante y no varia en función del numero de baterias conectadas|
|W|Energia Consumida|Es la cantidad de energia necesaria para que funcione un dispositivo. **Normalmente el 60% de su VA**|
|VA|Volt-Amper|La energia "aparente" necesaria para usar un dispositivo|
|Ah|Amper-Hora|Define el tiempo que proporciona una bateria a los dispositivos conectados|
|J|Julios| Cantidad de energia que puede proporcionar una bateria (1J=3600Ah)|
|Eff|Eficiencia| eficiencia del SAI (por norma, suele oscilar entre el 90% y el 98% dependiendo del SAI) |
|nBaterias|Numero de Baterias|El numero de baterias en un SAI |

### Calculo de autonomian
En las especificaciones encontramos algunas veces el tiempo de autonomía que tienen las baterías (entre 10min y 30 min). Pero en otras ocasiones nos dan el valor de la cantidad de energía que puede almacenar las baterías de un SAI. A partir de este valor Amper-hora(Ah) podemos extrapolar el tiempo que duran nuestras baterías.

Lo primero que tenemos que saber es que 1Ah es igual a 3600 Columbios(C) que es la unidad de energía en el Sistema Internacional (SI). Pero esto solo necesitamos saberlo para posteriormente hacer la conversión a Julios (J), que es la unidad para medir la energía eléctrica.

En las especificaciones de un SAI junto al Ah, tambien encontraremos la tensión (V) que proporcionan las baterias.

> SAI con Baterias de 2 X 12V 9Ah: Significa que tiene 2 baterias proporcionando 12V y con una acumulación de 9Ah de carga.
> Es decir es SAI proporciona 12V18Ah de corriente en bateria (Los voltios son constantes)

Para obtener los Julios (cantidad de energia electrica) que puede liberar la bateria deberemos de multiplicar los Voltios por los Columbus de las baterias (recordemos que 1AH=36000).

Una vez tenemos los Julios es facil calcular el tiempo que sobrevivirán las baterias cuando conectamos un dispositivo a ellas. Recordemos que los Wattios son la cantidad de energia consumida en 1 segundo. Es decir, la cantidad de Julios.

> Con una bateria de 100.000J podemos suministrar energia a un PC de 250W durante 6 minutos
> 100.000J/250W= 400s / 60 = 6.6m
{.is-info}

Tambien podemos mejorar la formula añadiendo el factor de eficiencia, es decir, la energía que se pierde debido al SAI. Para ello convertiremos los Wattios conectados al SAI (PCs) a su correspondiente potencia aparente VA.

> **Duración del SAI a carga máxima**
> ((nBaterias x V x Ah x Eff))/VA de los aparatos conectados) x 60 = X minutos de autonomia
{.is-info}

### Ejemplos de cómo puede ocurrir un error de cálculo

> Visita la web de http://www.danielclemente.com/consumo/ sobre cuánto gasta un ordenador.
{.is-success}


**Ejemplo 1**
Considere el caso de un SAI de 1000 VA. El usuario quiere alimentar 9 lámparas incandescentes de 100 watios (total 900 watios). Las lámparas tienen un consumo de 900 W ó 900 VA, ya que su factor de potencia es 1. Aunque el consumo en VA de la carga es de 900 VA, lo cual está dentro de las características del SAI, el equipo no podrá soportar esa carga. 

Esto se debe a que el consumo de 900 watios supera la potencia en watios del SAI, que es aproximadamente el 60% de los 1000 VA de la especificación, es decir 600 watios.

**Ejemplo 2**
Considere el caso de un SAI de 1000 VA. El usuario quiere alimentar un servidor de 900 VA con el SAI. El servidor tiene una fuente de alimentación con factor de potencia corregido, y por lo tanto tiene un consumo de 900 watios ó 900 VA. Aunque los VA consumidos por la carga son 900, lo cual está dentro de las especificaciones del SAI, no podrá soportar esa carga. 

Esto se debe a que los 900W de la carga superan la potencia en watios del SAI, que es aproximadamente el 60% de los 1000 VA de la especificación, es decir 600 watios.


> **Queremos alimentar dos PC de 250W durante 5 minutos con un SAI de12V18h. Será suficiente?**
> 
> 18Ah*3600C*12V = 777600 Julios
> 
> 777600J / (250W+250W) / 60 = 25 minutos
> 
> **Resposta**
> Si, será suficiente ya que proporciona 25 minutos de autonomia con dos PC de 250W cada uno.
{.is-success}

# :pencil: Exercicis

## Teorics
1. [Cerca informació sobre tipus de SAI](SAI-ejercicios-tipos)
1. [Calcular potencies per a un SAI](SAI-ejercicios-calcular-potencies)


## Practicas

1. [Puzzle tipos de SAI](puzzle-tipos-de-sai)
1. [Elecció de SAI a una oficina](eleccion-sai-oficina)
1. [Instal·lacio i monitorització del software d'un SAI](instalacion-monitorizacion-sai)
