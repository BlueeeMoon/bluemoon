---
title: ¿Qué es un Watchtowers?
date: 2022-05-24T11:35:41.496Z
extra:
  link: https://lightning.network/ 
  image: /media/watchtower.png
description: Entre las tecnologías que hace que Lightning Network sea más eficiente se encuentran los <strong>Watchtowers</strong>   
  <ul>   <li>Son nodos que vigilan las transacciones asociadas a un canal de pago</li>
  <li>Identifican acciones maliciosas o accidentales en caso de que un nodo este fuera de línea.</li>
  <li>Transmiten el estado válido del canal sin necesidad de que los dos actores estén en línea.</li> </ul>
taxonomies:
  tags:
    - lightning 
---
### Lightning Network 

Para comprender mejor que es Lightning Network debo explicar de forma resumida cómo funciona Bitcoin.

Bitcoin se ejecuta en la parte superior de un libro de contabilidad llamado cadena de bloques que es básicamente una gran lista de transacciones, un registro permanente y compartido en toda la red de Bitcoin y describe los movimientos del mismo en cada bloque.

El proceso para agregar transacciones (hacer una transferencia de valor en la red de Bitcoin, es decir; enviar Bitcoin de una dirección a otra) a estos bloques se llama minería, donde los mineros (computadoras que ejecutan un software especial de minería) compiten con otros mineros para resolver un acertijo matemático y agregar dichas transacciones. A estos mineros se les paga una tarifa por este procesamiento.

### Diseño de Lightning Network. 

Debido a los incentivos que se deben pagar a los mineros para procesar transacciones de costo menor y al tiempo de demora se diseñó Lightning Network.

Conforme se crean más transacciones, se congestiona la red y los usuarios deben pagar tarifas más altas para que su transacción se confirme en el siguiente bloque. 

Estás transacciones son relativamente lentas, se tardan aproximadamente una hora debido a que cada transacción es vista, validada y almacenada por cada computadora participante, esto genera una gran cantidad de datos difíciles de escalar. Una vez que los bloques están "llenos", el exceso de transacciones se deja en espera para ser procesadas en el siguiente bloque, para que las transacciones entren en el primer bloque muchos usuarios aumentarán las tarifas que están dispuestos a pagar.

Con el panorama anterior sería más difícil que las personas pudieran ocupar la red todos los días para el intercambio de bienes y servicios debido a la demora de transacciones y al costo de las transacciones.

### Resolviendo el problema de escalabilidad 

Para resolver esta congestión de datos se creó Lightning Network que propone una nueva red, una <strong>segunda capa</strong>, donde se pueden realizar pagos entre usuarios de igual a igual, sin la necesidad de publicar una transacción en la cadena de bloques de Bitcoin para cada pago. Los usuarios pueden pagarse entre sí en Lightning Network tantas veces como quieran sin incurrir en tarifas en cadena.

La red Lightning Network es descentralizada también, los pagos se envían a través de una red de canales de micropagos (microtransacciones) digitales que utilizan contratos inteligentes, conocidos como canales de pago cuya transferencia de valor ocurre fuera de la cadena de bloques. Lightning Network es una red segura de participantes que pueden realizar transacciones de forma rápida, de gran volumen, segura, privada, sin confianza y sin permiso. 

### Creación de Lightning Network

En febrero de 2015, Joseph Poon y Thaddeus Dryja propusieron una posible solución al problema de escalabilidad de Bitcoin, con la publicación de "The Bitcoin Lightning Network: pagos instantáneos escalables fuera de la cadena". En mayo del 2015 el desarrollador del kernel de Linux, Rusty Russell, se unió a Blockstream para comenzar la primera implementación de Lightning Network. Esta implementación esta escrito en el lenguaje de programación c (`c-lightning`) más tarde se le uniría Christian Decker, un desarrollador de Bitcoin.

Previó a esto Rusty Russell escribió una serie de tres artículos para educar a la gente sobre Lightning Network: aquí puedes ver estos [artículos](https://rusty.ozlabs.org/?p=467)

Este evento fue fundamental para Lightning Network pues después de ser solo un concepto se convirtió en una realidad, desde entonces la red brinda a Bitcoin un mundo de posibilidades, incluida la mejora de la privacidad, la velocidad y la escala.

### Privacidad en Lightning Network.

Cabe mencionar que las transacciones son públicas dentro de la cadena de bloques, en cambio en la red de Lightning Network las transacciones no son vistas por nadie.

### Componentes de Lightning Network.

Antes de ver los conceptos básicos de Lightning Network es importante saber cómo funciona y que tipo de implementaciones son las más importantes y más utilizadas.

Como mencioné anteriormente Lightning Network es la cadena subyacente de Bitcoin y crea transacciones de apertura y cierre de canales dentro de la cadena de bloques, es una red P2P donde los nodos se agregan como pares para poder comunicarse por medio de una conexión cifrada dentro de la red de canales de pago.

Para que pueda haber una interacción con la cadena de bloques, `bitcoind` o `btcd`, dependiendo el caso, es utilizado.

#### Nota: Estos conceptos son de Bitcoin y es importante comprenderlos para entender Lightning. 

El componente principal que utiliza el software de Lightning es `lncli` y `lnd` (Lightning Network Daemon) el primero permite crear una serie de operaciones sobre los canales de pago como abrir y cerrar canales, enviar pagos, generar facturas, entre otros, el segundo abre una interfaz para conduciral primero.

Además Lightning Network utiliza el protocolo `gRPC` para interactuar con `lnd`, `gRPC` es una versión mejorada de RPC, ambos protocolos son protocolos de llamada a procedimientos remotos (Remote Procedure Call) y se utiliza para comunicarse con clientes como `lncli`, es de código abierto y puede ejecutarse en cualquier entorno.

Cuando se está ejecutando un nodo de Lightning Network tú puedes ver la lista completa de comandos útiles en línea de comando con la siguiente instrucción:

```
lncli –help
```

O si quieres saber de algún comando en particular esta otra instrucción te puede ayudar:

```
lncli <command> --help
```

Finalmente se pueden utilizar servicios `REST` en Lightning para la comunicación entre la red de Lightning y aplicaciones.

Utilizar lncli dependerá de la implementación que se esté ejecutando, existen tres que son las más importantes en este orden:

* LND: es una implementación completa escrita en Go
* C-Lightning: una implementación compatible con las especificaciones en c.
* Eclair: es una implementación de Scala.
* Lightning Peach Daemon: es una implementación parcial en Rust, lpd.
* ptarmigan: Implementación de BOLT de Lightning Network.
* Rust Lightning: es una biblioteca Bitcoin Lightning escrita en Rust.
* lit - LN node software.
* lightning-onion - Micropagos enrutados de cebolla para la LN.
* ptarmigan - Implementación de LN en C++ compatible con BOLT.

Una vez que hemos visto cómo interactúan los componentes de Lightning Network, el software y las interfaces y las implementaciones podemos adentrarnos un poco más con los conceptos básicos.

#### Gracias.

En el siguiente artículo veremos más a detalle sobre los nodos y canales de pago.
