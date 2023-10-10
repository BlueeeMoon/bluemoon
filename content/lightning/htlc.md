---
title: HTLC (Hash Time-Locked Contracts). 
date: 2022-05-24T11:35:41.496Z
extra:
  link: https://lightning.network/ 
  image: /media/time.png
description: En Lightning los pagos enrutados están habilitados por <strong>(HTLC).</strong> 
  <ul>   <li>Estos contratos permiten que se puedan enrutar pagos a través de multiples saltos.</li>
  <li>Estos contratos constan de dos partes importantes.</li> 
  <li>La verificación del hash y la verificación del tiempo de vencimiento.</li></ul>
taxonomies:
  tags:
    - lightning 
---
### HTLC (Hash Time-Locked Contracts). 

¿Qué sucede si se requiere enviar (enrutar) pagos a una persona con la que no se esté conectada directamente?

En Lightning los pagos enrutados están habilitados por Contratos Hashed Timelock `(HTLC)`, estos contratos permiten que se puedan enrutar pagos a través de multiples saltos para enviarlos a cualquier persona dentro de la red que no esté conectada directamente a tu canal permitiendo que exista un único sistema financiero global interconectado, con estos contratos de pago condicionado un usuario de la red, por ejemplo Alicia, puede enviar a Carol Bitcoin si ella revela la imagen (secreto) previa a un hash específico.

Cabe mencionar que estos contratos constan de dos partes importantes: la verificación del hash y la verificación del tiempo de vencimiento.

#### Veamos cómo es esto.

Imaginemos que Alicia quiere enviar un pago a Dave de 2000 satoshis, sin embargo Alicia no tiene un canal directo conectado hacia él, pero si tiene una ruta por donde llegar, un canal que conecta con Carol, Bob y Dave.

Así que el pago se puede hacer sin ningún problema a través de una ruta. En este tipo de casos es cuando se ocupan los contratos HTLC donde se utilizan dos tipos de bloqueos.

```
hash –lock: bloqueado hasta que presente el valor de un secreto.
time-lock: bloqueado hasta que el tiempo establecido se cumpla.
```

Veremos cómo funcionan más adelante, en la siguiente imagen podemos ver la situación de este pago para comprender los contratos HTLC.

#### Situación: Alicia tiene un canal con Carol, Carol con Bob y Bob con Dave.

De acuerdo a esta imagen podemos ver la ruta que llevaría hacer el pago a Dave, antes de comenzar con el flujo de pago definiremos algunas variables:

```
R = secreto, también se conoce como preimagen y son solo los datos que se utilizan como entrada para una función hash.
H = hash del secreto R.
```
![Financiación](/media/financiacion.png)

* Alice enviará un pago de `2000` sats a Dave, lo primero que hace es notificarle que quiere enviárselos.
* Entonces Dave creará un número aleatorio llamado secreto R que no muestra a nadie, luego, calculará el hash de este secreto dando como resultado a H.

```
Nota: Este hash será compartido a lo largo de los canales, es decir; siempre será el mismo.
```
* Dave le envía a Alicia el Hash del secreto, ósea H.
* Alice entonces crea un contrato `HTLC` con ese hash H por la cantidad de 2002 sats y además agrega un bloqueo `(time-lock)` de tiempo establecido en 5 bloques.

```
Nota: los 3 sats adicionales se pagaran a los otros peers que ayuden a enrutar el pago y esa cantidad de 2003 sats quedará bloqueada en el contrato HTLC hasta que se encuentre R.
```
* Alicia le dice a Carol: "Te pagaré si puedes encontrar el secreto R en los próximos 5 bloques", y firma una transacción que sólo Carol puede canjear con conocimiento del Hash del secreto `H(hash -lock)`, y después sólo es canjeable por Alice.
* Entonces Carol sabe que puede enviar los fondos a Bob si Bob encuentra el secreto `R`, utiliza el hash de Alicia y crea un contrato `HTLC` por la cantidad de 2001 sats y le dice Bob: "Te pagaré si puedes producir la preimagen de H en los siguientes 4 bloques", ósea el secreto `R`.
* Una vez que Bob encuentre `R`, Carol podrá desbloquear los fondos y cobrar la parte que le corresponde. Bob con conocimiento del secreto `R`, hace lo mismo, usa ese hash para crear un contrato `HTLC` por la cantidad de 2001 sats para enviárselo a Dave, y como Dave tiene el conocimiento de R puede desbloquear los 2000 sats y Bob cobrar la parte que le corresponde. 

![Financiación](/media/flujo-pago.png)

#### Así que con el flujo de información anterior tenemos.

* Solo la persona que conozca el secreto R o preimagen que generó el hash H podrá usar el pago.
* Si el secreto no se revela a tiempo y no se utilizó el pago, se pueden reocupar los fondos.
* Los saldos de los canales han cambiado.
* Cada uno de los participantes gano 1 sat por enrutar el pago.

Dejaré algunos enlaces donde pueden profundizar un poco más acerca de este tema:

1. [LND Overview and Developer Guide](https://dev.lightning.community/overview/)
2. [Visualizing HTLCs and the Lightning Network’s Dirty Little Secret](https://medium.com/@peter_r/visualizing-htlcs-and-the-lightning-networks-dirty-little-secret-cb9b5773a0) 
3. [Mastering the Lightning Network](https://github.com/lnbook/lnbook)

#### Gracias.

Hemos visto de forma resumida cómo funcionan los contratos HTLC veamos cual es el flujo de un canal de pago en el siguiente artículo. 

