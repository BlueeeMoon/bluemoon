---
title: El problema de los generales bizantinos. 
date: 2024-08-06T11:35:41.496Z
extra:
  link: https://es.wikipedia.org/wiki/Problema_de_los_generales_bizantinos
  image: /media/mineria.png
description: Comprender el problema de los generales biznatinos.
  <ul> <li>¿Qué es un fallo bizantinos?</li>
  <li>¿Cómo lo resolvió Satoshi Nakamoto?</li>
  <li>Prueba de trabajo</li>
  </ul>
taxonomies:
  tags:
    - bitcoin
---

### El problema de los generales bizantinos. 

Es un problema fundamental en el campo de la informática, específicamente en el estudio de los sistemas distribuidos y la tolerancia a fallos y es crucial en el diseño de sistemas distribuidos, ya que muchos sistemas modernos están compuestos por múltiples nodos que deben coordinarse para funcionar correctamente. Fue hecho por **Robert Shostak** y desarrollado con **Leslie Lamport** y **Marshall Pease en 1982**.

Una de las soluciones más conocidas al problema de los generales bizantinos es el algoritmo de consenso bizantino **(Byzantine Fault Tolerance, BFT)**. Este tipo de algoritmos permite que los sistemas distribuidos lleguen a un consenso a pesar de la presencia de fallos bizantinos, es decir, fallos en los que los componentes pueden comportarse de manera arbitraria o maliciosa.

**Bitcoin** no utiliza directamente el modelo clásico de tolerancia a fallos bizantinos **(BFT)** en su algoritmo de consenso. En cambio, utiliza un enfoque diferente conocido como Prueba de Trabajo **(Proof of Work, PoW)**.

#### Lo podemos representar con la siguiente analogía:

Imaginemos una antigua ciudad griega Bizancio que quiere ser atacada por un grupo de generales que tienen su campamento con sus respectivas tropas en distintos puntos rodeándola, pondremos como ejemplo que son siete, así que la mejor manera de atacarla es que lo hagan al mismo tiempo.

Esto implica que todos se pongan de acuerdo, es decir; que lleguen a un "consenso", así que cada general podría mandar un mensaje por medio de un mensajero a otro campamento con las instrucciones para el ataque, sin embargo, este mensajero podría ser un traidor o la información podría ser interceptada.

Así que tenemos seis generales con su campamento cada uno.

```
 El campamento 1 manda a un mensajero al campamento 2 con el mensaje: Atacar al amanecer, 5:00 am
 El campamento 2 manda a un mensajero al campamento 3 con el mensaje: Atacar al amanecer, 5:00 am
 El campamento 3 manda a un mensajero al campamento 4 con el mensaje: Atacar al amanecer, 5:00 am
 El campamento 4 manda a un mensajero al campamento 5 con el mensaje: Retirarse al amanecer, 5:00 am
 El campamento 5 manda a un mensajero al campamento 5 con el mensaje: Retirarse al amanecer, 5:00 am
 El campamento 6 manda a un mensajero al campamento 5 con el mensaje: Retirarse al amanecer, 5:00 am
```

Como puedes darte cuenta el mensaje que envía el campamento 4 al 5 no es correcto, así que aquí ya no podría suceder el ataque cortinado.

Ahora esta analogía la llevaremos a los sistemas informáticos, específicamente a **Bitcoin.**

La siguiente ilustración representa a los generales como nodos alrededor de una ciudad (el libro mayor), con algunos generales honestos (marcados con un **check verde**) y algunos traidores (marcados con una **X roja**). Cada general está conectado con líneas de comunicación. 

También se muestra un minero con un pico resolviendo la **Prueba de Trabajo** para proponer un nuevo bloque de transacciones, destacando la importancia de la regla de la mayoría para la aceptación del bloque.

![bizantinos](https://raw.githubusercontent.com/BlueeeMoon/bluemoon/master/static/images/bizantinos.png)

El problema de los generales bizantinos no se había resuelto hasta la llegada de **Bitcoin**, especificamente hasta que lo resolvió Satoshi Nakamoto. Como sabes el software de **Bitcoin** es libre, así que puedes descargarlo. Todas las personas que ejecutan este software tienen una copia exacta de la cadena de bloques de manera local en sus computadoras. Con esto podemos deducir que si un nodo envía un mensaje a la red es validado y por ende todos los demás nodos tiene la misma información. 

Con lo mencionado acerca de los generales que podrían tener un mensajero traidor o malicioso se refiere a que los nodos podrían transmitir información errónea, quizás que falle un algoritmo y se produzca un error, de comunicación, o en su defecto sí exista un nodo malicioso. Así que la clave para solucionar este fallo es el consenso, es decir; una comunicación asertiva.

#### ¿Cómo se hace esto?

Se hace a partir de definir un conjunto de reglas aplicables a todos, en las cuales se identifica a cada nodo de forma inequívoca.

Cuando **Bob** hace una transacción cada nodo empieza a compilar esta transacción en un estado de ***transacción no confirmada***.
Esta transacción pasa por un proceso de minería: **la prueba de trabajo**, verificando que el hash de la transacción sea correcto, si lo es lo incluye en el bloque. 
La transacción pasa del estado ***transacción no confirmada*** a ***transacción confirmada*** para cada nodo. 
Con esto podemos estar seguros de que la transacción sea tomada como valida y llegar al consenso. 

Así que en **Bitcoin** las reglas son iguales para todos.

#### Gracias.

Espero sea de utilidad esta información.
