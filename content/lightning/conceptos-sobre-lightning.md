---
title: Concpetos básicos sobre Lightning Network. 
date: 2022-05-24T11:35:41.496Z
extra:
  featured: true
  link: https://lightning.network/ 
  image: /media/conceptos.png
description: Definir conceptos importantes sobre <strong>Lightning Network.</strong>  
  <ul>   <li>En Bitcoin cuando se transfiere valor a todos en la cadena de bloques se le denomina transacción.</li>
  <li>En Lightning Network lo llamamos pagos.</li> </ul>
taxonomies:
  tags:
    - lightning 
---
### Conceptos básicos sobre Lightning Network. 

Hablar sobre Lightning Network es un tema muy extenso y requiere práctica, así que solo abarcaremos los conceptos necesarios para su comprensión, posteriormente conforme vayas aprendiendo irás conociendo más, esto ya dependerá de tu propio interés.
 
Antes que nada es importante diferenciar dos conceptos importantes: transacción y pago; en Bitcoin cuando se transfiere valor a todos en la cadena de bloques se le denomina transacción y en Lightning Network lo llamamos pagos, estos pagos se enrutan a través de los canales siguiendo una ruta.

Para hacer un “pago” con Lihtning Network no se utiliza la cadena de bloques y los pagos enviados a través de canales de pago se denominan pagos fuera de la cadena de bloques.

### ¿Qué es un nodo? 

Un nodo en Lightning Network es simplemente una aplicación de software que se ejecuta en una computadora y que participa dentro de la red comunicándose de igual a igual con otros nodos Lightning Network que crean la red también. Son monederos que envían pagos y reciben pagos y acceden a la cadena de bloques de Bitcoin para asegurar los fondos utilizados para los pagos. Más adelante veremos cómo funciona.

### ¿Qué es un canal de pago?

Los canales de pago son el componente principal de Lightning Network y son simplemente una conexión directa entre dos nodos que tienen una relación financiera, socios de canal y que funcionan a través de transacciones de apertura y cierre en la cadena de bloques.

#### ¿A qué se refiere el término relación financiera o transacción de financiación?

Cuando se crea una transacción de financiación, se crea un canal, en esta transacción que contiene una sola entrada se asigna una cantidad de fondos en millisatoshis y se envían a una dirección multifirma (2 de 2) en la cadena de bloques donde ambos socios del canal controlan ambas partes, es decir; ambos tienen una clave para esta dirección multifirma que han firmado y pueden hacer pagos con esta dirección multifirma dentro del canal sin hacer transacciones en la cadena de bloques. Esta transacción determinará el saldo del canal.

Cuando se abre un canal de Lightning Network el nodo que inicia la apertura puede agregar fondos, así que el saldo del canal pertenece al nodo que abrió el canal, creando con ello un canal desequilibrado, sin embargo existen canales de doble financiación donde ambos nodos aportan fondos en la transacción, así que el balance de canal se divide entre ambos nodos.

El primero canal de doble financiación que se abrió fue en el bloque 681753 a través de la implementación c-lightning en la transacción:

`91538cbc4aca767cb77aa0690c2a6e710e095c8eb6d8f73d53a3a29682cb7581`

La misma que puedes ver [aquí](https://blockstream.info/tx/91538cbc4aca767cb77aa0690c2a6e710e095c8eb6d8f73d53a3a29682cb7581)

#### Ahora veamos un caso práctico:

Alicia y Bob deciden abrir un canal de pago de `50k` por parte de ambos, así que se abrirá por la cantidad de `100k`, que será la cantidad que se asigne a esta dirección multifirma y será el saldo del canal.

Así que una vez confirmada la transacción en la cadena de bloques ellos estarán listos para comenzar a hacer pagos dentro del canal creando transacciones de compromiso firmadas por ambos cuantas veces quieran, es claro que estas transacciones serán determinadas por el saldo del canal. En este punto el estado de este canal es que Alicia tiene 50k de su lado y Bob también.

Una vez que el saldo dentro del canal se mueve de un lugar a otro, el estado cambiará y se invalidará, es decir; se comenzó con `50k` de cada lado del canal, si alguna de las partes envía por ejemplo 10k, el estado ahora será `40k/60k` y así por cada pago que se haga.

Con esta dirección multifirma se garantizará que ninguna de las dos partes será deshonesta al transmitir un estado anterior, la dirección multifirma devuelve los fondos a Alice y Bob de acuerdo con la cantidad de canal acordada.

#### ¿A qué se refiere el termino enrutamiento?

En Lightning Network los pagos se enrutan a través de uno o más canales de pago siguiendo un camino del remitente al destinatario.

#### Gracias.

En el siguiente artículo veremos más a detalle sobre `HTLC`(Hash Time-Locked Contracts).
