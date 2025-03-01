---
title: Canales zombies. 
date: 2025-02-27T11:35:41.496Z
extra:
  featured: true
  link: https://github.com/lightninglabs 
  image: /media/zombi.png
description: Canales <strong>zombies</strong>  
  <ul>   <li>Guía para recuperar canales en estado zombie.</li>
  </ul>
taxonomies:
  tags:
    - lightning 
---


Guía de recuperaciòn de canales zombies. Esta guía te ayudará a este proceso paso a paso.

### Requisitos Previos

Antes de comenzar con la configuración, asegúrate de tener los siguientes requisitos previos:

- Haber leído este [repositorio](https://github.com/lightninglabs/chantools/blob/master/doc/zombierecovery.md)
- Palabras semilla de ambos pares.
- Estar en contacto con el par o pares de tus canales (en este punto ya habrán negociado un estado de cierre de los canales.)
- Tener el archivo de coincidencia **json**, en el documento viene como obtenerlo. 

Formato:

```json

{
    "node1": {
        "identity_pubkey": "03xxxxxx",
        "contact": "contact information for node 1, not needed by chantools itself"
    },
    "node2": {
        "identity_pubkey": "03yyyyyy",
        "contact": "contact information for node 2, not needed by chantools itself"
    },
    "channels": [
        {
            "short_channel_id": "61xxxxxxxxxxxxx (optional, numerical channel ID, can be found on 1ml.com)",
            "chan_point": "<txid>:<output_index> (also called channel point on 1ml.com)",
            "address": "bc1q...... (the channel's output address on chain, find out by looking up the channel point on a block explorer)",
            "capacity": 123456
        }
    ]
}

```

## Paso 1: Instalar Chantools 

1. Visita el [repositorio oficial de chantools](https://github.com/lightninglabs/chantools)
2. Selecciona la versión adecuada para tu sistema operativo.
3. Sigue las intrucciones e instala.
4. Verifica la instalación con: `chantools --help`

```
This tool provides helper functions that can be used rescue
funds locked in lnd channels in case lnd itself cannot run properly anymore.
Complete documentation is available at
https://github.com/lightninglabs/chantools/.

Usage:
  chantools [command]

```

# Nota: 

**Ambos nodos deben hacerlo.**

## Paso 2: Archivo json

1. Crear/subir el archivo **json** en algún directorio de tu preferencia.
2. `cd /tmp`
3. Colocar el contenido del **json** recibido `vi match.json` 
4. Generar una dirección de Bitcoin, en mi caso use [PyBlock](https://github.com/curly60e/pyblock) para hacerla (puedes generarla como desees)
3. Una vez que tengas la dirección ejecutar la siguiente instrucción (reemplazar bc1xxx por tu dirección): 

```
chantools zombierecovery preparekeys --payout_addr bc1xxx --match_file /tmp/match.json
```

# Nota: 

**Ambos nodos deberán hacerlo.**

## Paso 3: Validar archivos y preparar tarifa.

1. Cuando se ejecuta la instrucción `chantools zombierecovery..` se genera un directorio llamado `results` en la ubicación donde te encuentras.
2. Accede al directorio `cd results`
3. Ver el contenido `ls -lart`
3. El directorio creo un archivo con el siguiente formato `preparedkeys-year-month-day-nodepuykey.json`

# Nota: 

**Ambos nodos deberán hacerlo.**


## Paso 4: Juntar archivos json.

1. Asegúrate de que tu par haya ejecutado el paso anterior. 
2. Alguno de los dos tendrá que compartir su archivo **json**.
3. Una vez que tenga alguno de los dos los archivos, deberá colocarlo en el directorio `results`.


## Paso 5: Crear oferta

1. Seguramente ya verificaron la [guía](https://github.com/lightninglabs/chantools/blob/master/doc/zombierecovery.md#read-me-first) donde deciden la forma de dividir el saldo del canal entre tú y tu par. 
2. Una vez que tomada la decisión, alguno de los dos deberá ejecutar la siguiente instrucción, el que tenga ambos archivos:


```
chantools zombierecovery makeoffer \
	--node1_keys preparedkeys-year-month-day-nodepuykey1.json \
	--node2_keys preparedkeys-year-month-day-nodepuykey2.json \
	--feerate 15
```

3. Te pedirá tus palabras semillas:


```
Input your 24-word mnemonic separated by spaces:

```
4. Si usas una frase para tus palabras semillas deberás introducirla, sino simplemente enter.

```
Input your cipher seed passphrase (press enter if your seed doesn't have a passphrase):

```
5. Te mostrará un mensaje como el siguiente: `Found keys for channel..` esto dependerá de los canales que vayas a recuperar.
6. Si son tres canales por ejemplo, te mostrará tres bloques de dialogo donde tendrás que poner la cantidad de sats, no te preocupes, es muy intuitivo ya que muestra los siguientes datos:

```
Channel f006..................................................:1 (1 of 3):
        Capacity: "cantidad" sat
        Funding TXID: https://blockstream.info/tx/ f006............................................
        Channel info: https://1ml.com/channel/ "short_channel_id"
        Channel funding address: "La dirección con la que se abrio el canal"
		
How many sats should go to you ("dirección") before fees?: cantidad 

Will send:
        cantidad sats to our address ("dirección") and
        0 sats to the other peer's address ("dirección").
		
```
7. Solo tendrás que colocar la cantidad. Esto se mostrará 3 veces ya que en este caso son tres canales.
8. El resultado será un PSBT **(_transacción de bitcoin parcialmente firmada_)** firmado.

```
Done creating offer, please send this PSBT string to
the other party to review and sign (if they accept):
cHNidP8BAPYCAAAABWkfV1KJwCjcd+llYjb4UyM0nCLIn7X1FfRQOOc1........

```

## Paso 5: Firmar PSBT por parte de la contraparte. 

1. El par tendrá que firmar el PSBT.
2. Envía la cadena hexadecimal obtenida para que la firme el par. 

```
chantools zombierecovery signoffer \
	--psbt <offered_psbt_base64>
```

3. Una vez ejecutada la instrucción anterior, le pedirá las palabras semillas.

```
Input your 24-word mnemonic separated by spaces:

```

4. Si usa una frase para sus palabras semillas deberá introducirla, sino simplemente enter.

```
Input your cipher seed passphrase (press enter if your seed doesn't have a passphrase):

```

5. Posteriormente mostrará el siguiente mensaje:


```
The PSBT contains the following proposal:

        Close 3 channels:
        Channel 0 ("chan_point":1), capacity "cantidad" sats
        Channel 1 ("chan_point":1), capacity "cantidad" sats
        Channel 2 ("chan_point"), capacity "cantidad" sats
       
        Send "cantidad" sats to address "dirección generada en pasos anteriores"

        Total fees: "cantidad" sats

Do you want to continue?
Press <enter> to continue and sign the transaction or <ctrl+c> to abort:
Success, we counter signed the PSBT and extracted the final
transaction. Please publish this using any bitcoin node:


```

## Paso 5: Transmitir transacción.

1. Después de ejecutar `chantools zombierecovery signoffer...` el resultado será una transacción que no ha sido enviada a la red.
2. Se verá como esto: `02000000000105691f575289c028dc77e9656236f85323349c22c89fb5f515f45038e735e806f0010...`

3. Cualquiera de los dos pares podrá enviar la transacción a la red con el comando siguiente:


```
 bitcoin-cli sendrawtransaction 02000000000105691f575289c028dc77e9656236f85323349c22c89fb5f515f45038e735e806f0010... 

```

3. El resultado será el ID de la transacción.

```
4d8c3f8239b63db649fd789f95ac5f.........

```
4. Puedes verificar la transacción en cualquier explorador de bloques o en tu propio nodo.
5. Ahora solo debes esperar a que sea confirmada.
6. Una vez que pase esto, el saldo deberá estar de vuelta. 

# Nota: 

**Los datos como: cantidad, chan_point, dirección,.., sustituyen los valores reales.**

¡Gracias! Si tienes alguna pregunta o sugerencia, no dudes en comunicármelo.
