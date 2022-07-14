---
title: Flujo de vida de un canal de pago. 
date: 2022-05-24T11:35:41.496Z
extra:
  link: https://lightning.network/ 
  image: /media/flujo.png
description: Descripción del <strong>flujo de vida</strong> de un canal de pago.  
  <ul>   <li>Apertura de un canal de pago.</li>
  <li>¿Por qué usar la red de Lightning Network.</li> </ul>
taxonomies:
  tags:
    - lightning 
---
### Flujo de vida de canal de pago.

Veamos el flujo de vida de un canal de pago para comprender mejor este concepto.

1. Se añade un nuevo peer antes de abrir un canal de pago para tener una comunicación.
   * `lncli connect <PUBKEY>@<HOST>:<PORT>`
2. Ya que se tiene un peer conectado se inicia con el proceso de apertura de canal donde se especificará la cantidad que desea comprometer y una cantidad que le gustaría dar a la otra parte como estado de compromiso inicial.
   * `lncli openchannel --node_key=<ID_PUBKEY> --local_amt=<CANTIDAD>`
3. Se debe esperar la confirmación en la cadena de bloques.
4. El canal se puede cerrar si alguna de las partes así lo desea.
   * `lncli closechannel --funding_txid=<funding_txid> --output_index=<output_index>`

### ¿Cómo se hace una apertura de canal?

#### El proceso sería el siguiente.

Se realiza una transacción en la cadena de bloques para depositar los fondos en una salida de firma múltiple con la cantidad que desee que contenga el canal y este proceso implica que se tengan que pagar tarifas de transacción para abrirlo, a este concepto se le conoce como: <strong>transacción de financiamiento.</strong>

Una vez que la transacción se haya transmitido a la cadena de bloques, el canal de pago quedará abierto y listo para ser utlizado.

### ¿Por qué utilizar Lightning Network?

Con Lightning Network puedes hacer pagos instantáneos sin tener que esperar confirmaciones, ya que los fondos se liquidan en segundos, puedes utilizarlo para hacer compras como utilizas normalmente el efectivo; cafés, restaurantes, libros, bares.... además Lightning Network puede ser utilizado en terminales de puntos de venta, (existen muchas implementaciones para esto), en transacciones entre dispositivos de usuarios, o en cualquier lugar donde se necesiten pagos rápidos.

#### Micropagos.

Se pueden abrir nuevos mercados con la posibilidad de los micropagos. Lightning Network permite enviar fondos desde 0,00000001 de bitcoin sin riesgo de custodia. La cadena de bloques de Bitcoin impone actualmente un tamaño mínimo de salida cientos de veces mayor, y una tarifa fija por transacción que hace que los micropagos sean poco prácticos. Lightning Network permite pagos mínimos.

Si eres una persona que apenas está empezando con Lightning Network y deseas conectar tu canal a nodos aquí hay un enlace donde puedes conectarlos, son canales recomendados para poder enrutar de forma segura ya que son nodos que llevan bastante tiempo en línea, además de tener un nivel elevado de prestigio dentro de la red.

Finalmente si quieres saber más acerca de Lightning Network [aquí](https://lightning.network/lightning-network-paper.pdf) puedes encontrar el documento de oficial.

#### Gracias.

Espero sea de utilidad. 
