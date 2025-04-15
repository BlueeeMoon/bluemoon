---
title: Conceptos clave. 
date: 2025-04-14T11:35:41.496Z
extra:
  featured: true
  link: https://bitcoin.org
  image: /media/conceptos-bitcoin.png
description: Conceptos clave acerca de <strong>Bitcoin</strong>
  <ul>   <li>¿Qué es una dirección de Bitcoin</li>
  <li>¿Qué es una UTXO?</li>
  <li>¿Qué es un nodo?</li> </ul>
taxonomies:
  tags:
    - bitcoin
---

---
Veremos algunas definiciones que considero importantes comprender para poder comenzar con **Bitcoin**. Las definiciones más específicas y técnicas las puedes encontrar en el siguiente [enlace](https://bitcoinops.org/en/topics/).
Para comenzar existen algunas definiciones que son indispensables conocer. Cuando comiences a utilizar **Bitcoin** necesitarás una Wallet, la cual generará una dirección, alguien que te envie **bitcoin** o adquirirlos, con estos puntos importantes podemos aprender otros más.

---

### Bitcoin y bitcoin.

Cuando estamos hablando del protocolo como tal usamos la letra mayúscula al inicio de la palabra **Bitcoin** y si estamos hablando de la moneda, usamos la palabra con minúscula al inicio **bitcoin**.

> "La unidad monetaria se llama bitcoin con b minúscula, y el sistema se llama Bitcoin, con B mayúscula."
> **Mastering Bitcoin**. Autor: [Andreas M. Antonopoulos, David A. Harding](https://github.com/bitcoinbook/bitcoinbook/blob/develop/ch01_intro.adoc#:~:text=Tip,capital%20B.)


Ahora que ya podemos diferenciar una de otra veamos lo que tenemos pendiente con el primer párrafo. Si vas a adquirir **bitcoin** necesitarás una dirección. 

---

### ¿Qué es una dirección?

Una dirección en el protocolo de **Bitcoin** es una cadena alfanumérica que ha pasado por un proceso computacional para ser creada. Es como un número de cuenta donde puedes recibir **bitcoin** y se ve así:

` bc1pp7w6kxpj5lzgm28pmuhezwl0vjdlcrthqukll5gn9xuqfq1n673smy8m67 `

Esta dirección es un identificador que dentro del protocolo de **Bitcoin** es una **llave pública**. Veremos esto más adelante. Ahora te preguntarás: ¿cómo gastar esos **bitcoin**?, vamos al apartado siguiente. 

---

### Llave privada y llave privada.

Ya que tenemos nuestra número de cuenta (dirección), necesitaremos algo así como una contraseña para desbloquear ese **bitcoin** que nos han enviado. Esa contraseña es una **llave privada**. ¡Qué maravilloso, hemos llegado a los conceptos de **llaves privadas** y **llaves públicas**!

La **llave privada** es el primer paso en la creación de una dirección en **Bitcoin**. Esta llave es simplemente un número aleatorio de 256 bits, generado de manera segura usando una fuente de entropía criptográfica.

A partir de la **llave privada** se genera la **llave pública**. Este proceso se hace utilizando una operación matemática que toma la **llave privada** y la transforma en una **llave pública** de 512 bits (64 bytes).

Estos conceptos no los veremos de manera técnica en este documento puesto que es solo para definiciones generales. 

Ahora que ya sabemos lo que es una dirección (se obtiene de la **llave pública**) y que la necesitaremos para recibir **bitcoin** veamos cómo se genera esa dirección. Para ello vamos definir lo que es una **wallet**. 

---

### Wallet.

Una **wallet** es una aplicación que entiende el protocolo de **Bitcoin**, es como un monedero físico en el mundo real, sin embargo, éste es virtual. Algunos consideran que en vez de llamarse monedero, tendría que llamarse **llavero** ya que no contiene monedas sino llaves. Esta aplicación es la que nos genera la dirección. Una wallet te genera un par de claves:

> - <span style="color: #9858b0;"> **Claves privadas**: Permiten gastar los **bitcoin**.</span>
> - <span style="color: #9858b0;"> **Claves públicas**: Se derivan de las claves privadas como mencionamos anteriormente.</span>

Ahora, ¿dónde obtenemos una walllet, monedero o llavero?

Este recurso es muy útil para comenzar a estudiar sobre **Bitcoin**, además tienen el apartado de [monederos]( https://bitcoin.org/es/elige-tu-monedero?step=1).

---

### Tipos de Wallets.

Existen dos tipos importantes de wallets: 

> - <span style="color: #9858b0;"> **Software**: Se conectan a internet, así que la puedes descargar en el móvil o en el ordenador. </span>
> - <span style="color: #9858b0;"> **Hardware**: Se conoce como monedero frío y no se conecta a internet, sino que es un dispositivo que almacena todas las claves privadas, así que es ideal para almacenar **bitcoin**.</span>

---

### Criptografía asimétrica.

Arriba vimos los conceptos de llaves privadas y llaves públicas. **Bitcoin** utiliza criptografía de clave pública para la creación de llaves. Vamos a ver rápido como funciona. La criptografía de clave pública es un método para encriptar datos con dos claves diferentes relacionadas matemáticamente:

> - <span style="color: #9858b0;"> **La llave pública** se deriva de la **llave privada** y está disponible para que cualquiera pueda utilizarla. De esta **llave pública** se obtiene la dirección de **Bitcoin**.</span>

Debido al uso de dos claves en lugar de una, la criptografía de clave pública también se conoce como **criptografía asimétrica**.

El siguiente diagrama ejemplifica de manera sencilla como funciona la **criptografía asimétrica** con nuestros chicos favoritos. 

![criptografiaAsimetrica](https://raw.githubusercontent.com/BlueeeMoon/bluemoon/master/static/images/criptografiaAsimetrica.jpeg)

En este [enlace podrás saber más](https://cmapscloud.ihmc.us/rid=1SZ5JRZW9-2KTPSQ-1RF/PKC-resumen.pdf).

---

### Funciones hash.

Ya que hemos visto esto del par de llaves es importante comprender lo que es una función **hash criptográfica**. Esto es simplemente una función matemática que mediante un algoritmo al recibir datos de entrada te devuelve un rango de salida finito. Si tienes por ejemplo una obra completa de algún libro, al aplicarle este algoritmo criptográfico obtendrás una salida de tamaño fijo que representa esta obra completa de tu libro favorito quizás. 

En una función hash la salida:

> - <span style="color: #9858b0;"> No permite regresar a la entrada original, a esto se le llama **unidireccional**.</span>
> - <span style="color: #9858b0;"> No hay límite de entrada de datos, es decir, puedes ingresar una oración o una novela de mil páginas y siempre las salida será de tamaño fijo, esto dependerá de la función que uses, en este caso, será de 256 bits que es lo que se ocupa en **Bitcoin**, **SHA256**.</span>
> - <span style="color: #9858b0;"> Además si cambias culaquier dato de entrada la salida del hash será diferente, a esto se le llama **dispersión**.</span>

El siguiente diagrama hace una pequeña representación de lo anterior. 

![funcionHash](https://raw.githubusercontent.com/BlueeeMoon/bluemoon/master/static/images/funcionHash.jpeg)

Existen varios tipos de funciones hash, el que nos interesa es el **SHA256** que es el utilizado en **Bitcoin**. Si quieres saber más sobre él [aquí](https://emn178.github.io/online-tools/sha256.html) hay un recurso muy lindo con el que puedes jugar.  

El algoritmo **SHA256** se utiliza en **Bitcoin** para muchas cosas, entre ellas:

> - <span style="color: #9858b0;"> **Minado**: es usado en el proceso de prueba de trabajo para encontrar un bloque válido.</span>
> - <span style="color: #9858b0;"> **Transacciones**: Se usa para la creación de direcciones, así como para firmar y verificar las transacciones.</span>
> - <span style="color: #9858b0;"> **Integridad de la cadena**: asegura la integridad de cada bloque mediante el cálculo de los hashes de los bloques anteriores.</span>
> - <span style="color: #9858b0;"> **Árboles Merkle**: permite calcular las raíces Merkle que garantizan que las transacciones no han sido alteradas.</span>

Estos conceptos los veremos más adelante. Seguimos con la función **hash**.

---

### Firmas digitales.

Ahora que hemos visto un poco acerca de las funciones hash podemos pasar a ver lo que es una **firma digital**. En **Bitcoin** se utilizan las firmas digitales para comprobar la propiedad de los fondos. Una **firma digital** es como firmar un documento donde se esta verificando la autenticidad del firmante. 

En la criptografía de **clave asimétrica** la firma digital funciona de la siguiente manera:

![firmaDigital](https://raw.githubusercontent.com/BlueeeMoon/bluemoon/master/static/images/firmaDigital.jpeg)

Aquí puedes saber [más](https://bitcoin.org/files/bitcoin-paper/bitcoin_es.pdf) acerca de esto.

---

### Bloque.

Antes de comenzar a definir la cadena de bloques es necesario comprender que es un bloque en **Bitcoin**. Un bloque es una estructura de datos que contiene transacciones. Más adelante veremos que es una transacción. Las transacciones dentro de los bloques son validadas con funciones matemáticas que auntentican que el protocolo de **Bitcoin** sea correcto. 

Una vez que estás transacciones son agregadas, el bloque se une a una cadena de bloques previos que de igual manera contienen las transacciones que se han hecho a lo largo de la historia de **Bitcoin.**

Es importante mencionar que los bloques están encadenados por medio de un hash, este hash se obtiene al aplicarlo a esta estructura de datos. Cada bloque es referido por el bloque anterior en la cadena. 

Si deseas profundizar en este [enlace](https://github.com/bitcoinbook/bitcoinbook/blob/275c4eb8eab8800c6adc39f8def8e8f8fa356a57/ch11_blockchain.adoc#structure-of-a-block) podrás hacerlo.

---

### Bloque génesis.

Antes de comenzar con la definición de la cadena de bloques veamos lo que es el bloque génesis. El bloque génesis es el primer bloque del libro mayor, este bloque tiene una particularidad muy importante, está codificado estáticamente dentro del protocolo de **Bitcoin** Core, lo que significa que no puede ser modificado. 

El bloque génesis no se generó mediante la minería como los otros bloques, veremos el concepto de minería en dos apartados más, sino que está hardcodeado en el código fuente de **Bitcoin**. Esto significa que sus datos (hash, transacciones, timestamp, etc.) están definidos directamente en el código de **Bitcoin** Core y no se obtienen de la red ni de una base de datos.

> "Cada nodo siempre conoce el hash y la estructura del bloque génesis, la fecha fija de su creación e incluso la transacción individual que contiene."
> **Mastering Bitcoin.** Autor: [Andreas M. Antonopoulos, David A. Harding](https://github.com/bitcoinbook/bitcoinbook/blob/275c4eb8eab8800c6adc39f8def8e8f8fa356a57/ch11_blockchain.adoc#the-genesis-block)


En resumen el bloque génesis es el ancla o el eslabón desde donde inica la cadena o el libro mayor.

#### Importancia del bloque génesis:

> - <span style="color: #9858b0;">Es el punto de inicio inmutable de la cadena de bloques de Bitcoin.</span>
> - <span style="color: #9858b0;">Su codificación estática lo hace resistente a modificaciones malintencionadas.</span>
> - <span style="color: #9858b0;">Representa el nacimiento de Bitcoin y está ligado a la crisis financiera de 2008.</span>
> - <span style="color: #9858b0;">El bloque génesis no puede verlo nadie ya que los nodos no pueden llegar a él, si deseas verlo lo pudes hacer con su hash que es público.</span>

Vamos ahora con la cadena de bloques. 

---

### Cadena de bloques.


Ahora que ya vimos lo que es un bloque podemos comprender mejor la cadena de bloques. La cadena de bloques o el libro mayor, llamado así porque actúa como un registro contable que documenta todas las transacciones realizadas en la red de **Bitcoin**.

Este registro es público, es decir, todo el mundo puede verlo y como vimos en el apartado anterior los bloques están vinculados al anterior mediante un hash, formando una cadena, por eso el nombre de **cadena de bloques**.

---

### Bloque huérfano.

Veamos rapido lo que es un **bloque huérfano** antes de pasar a lo siguiente pues es importante saber sobre él. También es conocido como bloque abandonado, es un bloque que ha sido minado correctamente pero no se encuentra en la cadena principal de bloques, cuando los mineros intentan resolver un bloque, y esto se da en muchas partes en todo el mundo, puede suceder que alguien resuelva primero el acertijo criptográfico. Estos bloques son válidos, pero debido a la naturaleza competitiva de la minería, solo uno de los bloques encontrados en el mismo tiempo puede ser parte de la cadena principal.

Aunque esto puede ser confuso ya que el bloque en realidad si tiene un padre como se muestra en esta imagen.

Para saber más de como están los bloques actualmente [aquí](https://fork.observer/).

![huerfano](https://raw.githubusercontent.com/BlueeeMoon/bluemoon/master/static/images/huerfano.jpeg)

---

### Minería.

Ahora que vimos lo que es un bloque, la cadena que se forma con estos bloques, y además vimos a grandes rasgos como están estructurados, podemos ver como se llenan con esta información y qué pruebas y procesos se hacen para validarla. Para ello es importante comprender que es la minería y cuál es su función dentro de **Bitcoin**. 

Uno de los pilares más importantes dentro del protocolo de **Bitcoin** es la minería ya que con ella se alcanza el consenso descentralizado, no hay una autoridad central que regule esto, así que es fantástico.

Un minero en **Bitcoin** es un software que tiene como objetivo resolver un problema basado en un algoritmo hash criptográfico, ha esto se le llama PoW (Proof-Of-Work) por sus siglas en inglés, prueba de trabajo que veremos más adelante. 

Cuando el minero ha resuelto el desafío, recibe una recompensa y el derecho a registrar las transacciones en la cadena de bloques, siendo esto la base del modelo de seguridad de **Bitcoin**.

Lo que hacen los mineros es recoger las transacciones que han sido previamente validadas en base al protocolo de **Bitcoin** por parte de los nodos, estás transacciones son obtenidas de un espacio de memoria llamado **mempool** que todos los nodos tienen y que previamente fueron transmitidas por la red. Una vez que eligen las transacciones de su propia mempool comienzan con el desafío mencionado anteriormente y si logran resolverlo estás transacciones quedan registradas en el bloque en curso, y el bloque es agregado al libro mayor, con ello el minero obteniene la recompensa de bloque y las tarifas que se pagaran por ellas. 

La recompensa de bloque la veremos en el sigueinte punto, y posteriormente veremos acerca de las transacciones.

---

### Recompensa de bloque.

La recompensa de bloque es un incentivo que reciben los mineros por realizar un esfuerzo computacional significativo. Este incentivo es **bitcoin** recien acuñado o monedas nuevas y las tarifas que se pagan por las transacciones. 

Cada 210,000 bloques tras el bloque génesis la cantidad máxima de **bitcoin** nuevos disminuye, esto es aproximadamente cada cuatro años, definido en el mismo protocolo. Esto comenzó así.

> - <span style="color: #9858b0;"> 50 **bitcoin** por bloque en enero de 2009.</span>
> - <span style="color: #9858b0;"> 25 **bitcoin** por bloque, en noviembre de 2012.</span>
> - <span style="color: #9858b0;"> 12.5 **bitcoin** en julio de 2016.</span>
> - <span style="color: #9858b0;"> 6.25 **bitcoin** en mayo de 2020.</span>

En base a lo anterior esto irá disminuyendo hasta aproximadamente el año 2140, lo que significa que ya no se emitirán nuevos **bitcoin**.

Además de obtener esta recompensa, los mineros obtienen tarifas de las transacciones, ya que estás puede incluir una comisión en forma de excedente de **bitcoin** entre las entradas y salidas. En el futuro cuando la recompensa disminuya las ganancias mineras provendrá de las comisiones.

---

### Prueba de trabajo.

Existe un protocolo llamado PoW (Proof-Of-Work) por sus siglas en inglés, es utilizado en la minería de **Bitcoin**. Este protocolo se utiliza en redes distribuidas como **Bitcoin**. Se llama prueba de trabajo porque el protocolo requiere un esfuerzo computacional por parte del cliente, **minero**; es decir, implica la resolución de un problema criptográfico.

El protocolo define que los mineros deben ajustar un valor llamado **nonce** (lo veremos en el siguiente apartado) y calcular el hash del bloque con un algoritmo criptográfico específico, el **SHA-256** (Secure Hash Algorithm 256-bit) para hacer un hash valido que cumpla con ciertas condiciones establecidas por la dificultad de la red.

Este hash debe ser menor que un valor objetivo denominado **objetivo de dificultad** o **target difficulty** determinado por la dificultad en ese momento. Este campo numérico se usa como control para evitar que los datos sean manipulados.

Los mineros prueban diferentes valores de **nonce** hasta que el hash que generan sea menor que el valor objetivo. Este proceso es completamente aleatorio. Cuando un minero encuentra una solución válida, se transmite al resto de la red. El bloque propuesto se considera válido si cumple con los criterios del protocolo.

La dificultad del problema está ajustada de forma que, en promedio, los mineros tarden 10 minutos en encontrar una solución a este problema. Esto se ajusta cada **2016 bloques**, es decir, cada dos semanas, dependiendo de cuán rápido o lento sea el proceso de minería. Cuanto mayor sea la dificultad, más potencia computacional será necesaria para encontrar un hash válido.

> **Cynthia Dwork** y **Moni Naor** propusieron la idea de [PoW](https://www.geeksforgeeks.org/blockchain-proof-of-work-pow/) y más tarde **Satoshi Nakamoto** la aplicaron en el documento **Bitcoin** en 2008.

Este diagrama explica como funciona.

![pow](https://raw.githubusercontent.com/BlueeeMoon/bluemoon/master/static/images/pow.jpeg)

---

### Nonce

Veamos lo que es el campo **nonce**. El nonce es un campo aleatorio utilizado **una sola vez** de 4 bytes (32 bits), lo que significa que puede contener valores enteros sin signo en el rango de 0 a 4,294,967,295 (que es 2^32−1).

Lo que querrá hacer el minero es añadir bloques de transacciones al libro mayor, como lo vimos en la PoW, para ello construyen el encabezado del bloque que básicamente es el resumen de todos los datos. 


> - <span style="color: #9858b0;">Versión.</span>
> - <span style="color: #9858b0;">Hash del bloque.</span>
> - <span style="color: #9858b0;">Raiz de Merkle.</span>
> - <span style="color: #9858b0;">Tiempo.</span>
> - <span style="color: #9858b0;">Bits.</span>
> - <span style="color: #9858b0;">Nonce.</span>

Cuando los mineros construyen el encabezado del bloque el único dato que cambia es el nonce, esto para obtener un hash distinto con los mismos datos de entrada. El objetivo es encontrar el hash que empiece con cierta cantidad de ceros por debajo de un cierto valor, que lo vimos arriba.

**Nota**: Con el incremento de la dificultad en la minería, los mineros también utilizan otros campos como: ExtraNonce que se encuentra dentro del scriptSig de la transacción coinbase para generar más combinaciones.

---

### Árbol de Merkle y raíz de Merkle.

Al parece ibamos a avanzar con el tema de las transacciones, pero seguramente te preguntaste acerca de la **raíz de Merkle** y del **árbol de Merkle**. Este concepto fue introducido por [Ralph C. Merkle](https://es.wikipedia.org/wiki/Ralph_Merkle) y es una estructura de datos utilizada en criptografía y en sistemas de archivos distribuidos como **Bitcoin.**

Primero veamos el **Árbol de Merkle**. Este describe una estructura de datos ramificados, generalmente se muestran al revés con la **raíz** en la parte superior y las **hojas** en la parte inferior, son binarios que contienen hashes criptográficos. Se usa para verificar la integridad y consistencia de grandes conjuntos de datos de manera eficiente.

La **Raíz de Merkle** es el hash final que se obtiene en la parte superior del **árbol de Merkle** después de calcular todos los hashes en los niveles inferiores. Es un identificador único de todo el conjunto de datos. Si un solo dato cambia, la raíz cambia, lo que permite verificar la integridad de los datos sin necesidad de almacenarlos todos.

Vamos con **Bitcoin**. Las transacciones en **Bitcoin** residen en el cuerpo de un bloque, lo cual forma un **árbol de Merkle**. Este árbol es una estructura binaria completa, interconectada por punteros hash. Ahora imagina un árbol, las hojas serían como los nodos de este árbol, y cada nodo padre surge de la combinación del hash **SHA-256** de sus dos nodos hijos.

Para ello, se realiza el hash de los nodos hijos y se concatenan los resultados obtenidos para calcular los nodos padres. Esta metodología se repite capa por capa de forma ascendente. Esta estructura de datos criptográfica reduce la necesidad de transmisión de datos y agiliza la complejidad computacional.

En la imagen de arriba se ven cuatro transacciones abajo, A,B,C y D que serían las hojas (nodos), en cada transacción se aplica un doble hash con el algoritmo **SHA256**

` Hash de Tx A = SHA256(SHA256(Tx A)). `

En seguido los pares consecutivos de hojas se resumen en un nodo padre concatenando los dos hash y combinándolos. 

` Hash de TxA y Hash de TxB = SHA256(SHA256(HA + HB)). `

Continuando el proceso hasta que solo exista un nodo en la parte superior (raiz) almacenandose en el encabezado del bloque un hash de 32 bytes. Así es como se resumen las transacciones.


El valor hash que resume todas las transacciones en la **raíz de Merkle.**

![raizMerkle](https://raw.githubusercontent.com/BlueeeMoon/bluemoon/master/static/images/raizMerkle.jpeg)

---

### Objetivo de dificultad

No podemos dejar pasar este punto súper importante acerca de como se hace el ajuste de dificultad que vimos en el apartado de **minería**, más bien vamos definir como funciona esto.

Es un ajuste que se hace para regular la dificultad de la minería, con ello se asegura que los bloques se sigan minando aproximadamente cada 10 minutos. Se produce cada 2016 bloques (aproximadamente cada dos semanas), en función del tiempo que tardaron en minarse esos últimos 2016 bloques.

Para ello se utiliza un campo llamado **target** que es un número de 256 bits que define el valor máximo que puede tener un hash válido para que un bloque sea aceptado. Cuanto más bajo sea el target, más difícil es encontrar un hash menor que ese valor, y por lo tanto, mayor es la dificultad.

> Si la red está generando bloques en un periodo inferior a los diez minutos, la dificultad de minado aumenta y si por el contrario los bloques se están generando de manera más lenta, la dificultad de minado disminuye.

Y luego lo más bonito, cuando se produce este ajuste, la reasignación de la dificultad se produce de forma automática y en cada nodo independientemente. Así que cada dos semanas ~ todos los nodos reorientan la dificultad de PoW. 

En resumen.

> - <span style="color: #9858b0;">El Target Adjustment (ajuste del objetivo) se refiere al cambio del target (objetivo de hash) de la prueba de trabajo **PoW**.</span>
> - <span style="color: #9858b0;">La dificultad es una forma de expresar este cambio de **target**.</span>

---

### Hashrate.

La tasa de hash es una métrica relacionada con el proceso de minar **Bitcoin**. Esta métrica representa la cantidad de procesos que un equipo puede realizar por segundo para resolver el rompecabezas criptográfico.

Si la tasa de hash es alta puede existir una mayor probabilidad de resolver el acertijo criptográfico, lo que aumenta las posibilidades del minero de recibir una compensación por procesar transacciones.

---

### Transacciones.

Ahora si podemos pasar a las transacciones, una transacción es una estructura de datos que representa el movimiento de **bitcoin** de una dirección a otra dentro de la red. Técnicamente, una transacción es un conjunto de entradas y salidas, asegurado criptográficamente mediante firmas digitales y validado por los **nodos** de la red. Existe una base de datos en cada **nodo completo** de **Bitcoin** que nos dice quien controla cierta cantidad de **bitcoin**. Lo de los nodos lo veremos más adelante. 

Las transacciones lo que hacen es desbloquear y bloquear **bitcoin** por medio de criptografía. Vamos a profundizar un poco más. Cuando se crea una transacción, es decir, cuando envias **bitcoin** a alguien, se crea una salida, esta salida contiene la llave **pública** que vimos en el apartado de criptografía, recordarás que la dirección contiene esta llave, y esta dirección fue creada por el emisor, así que cuando reciba los **bitcoin** los podrá desbloquear con su llave **privada** correspondiente a la clave **pública** creando una **firma digital**. 

> No te preocupes de como se hace internamente puesto que esto lo hacen las wallets o los nodos si es que usarás o estás ejecutando ya uno. 

**Estructura de una transacción en Bitcoin.**

| Campo              | Tamaño (bytes) | Descripción                                                                    |
|--------------------|----------------|--------------------------------------------------------------------------------|
| Versión            | 4              | Número de versión de la transacción.                                           |
| Flag (opcional)    | 2 			  | Solo en SegWit (0x0001)														   |
| Conteo de Entradas | 1 - 9          | Número de entradas (inputs) en la transacción, codificado en formato VarInt.   |
| Entradas (Inputs)  | Variable       | Lista de entradas, cada una con los campos descritos a continuación.           |
| Conteo de Salidas  | 1 - 9          | Número de salidas (outputs) en la transacción, codificado en formato VarInt.   |
| Salidas (Outputs)  | Variable       | Lista de salidas, cada una con los campos descritos a continuación.            |
| Testigos (opcional)| Variable       | Solo en SegWit, contiene firmas y pruebas de autenticidad
| Locktime           | 4              | Tiempo de bloqueo (opcional) que especifica cuándo puede ser añadida al bloque.|


Para que una transacción sea válida se debe cumplir con lo siguiente

> - <span style="color: #9858b0;">Las firmas deben ser correctas.</span>
> - <span style="color: #9858b0;">No debe haber doble gasto.</span>
> - <span style="color: #9858b0;">Los BTC gastados deben ser menores o iguales a los disponibles.</span>
> - <span style="color: #9858b0;">La estructura de la transacción debe cumplir las reglas de consenso.</span>

---

### Transacción coinbase. 

En la parte de minería mencionamos algo acerca de la transacción **coinbase**. Esta transacción es la primera transacción en un bloque y es colocada por el minero cuando construye un bloque, cuando el incentivo por resolver el acertijo matemático se le otorque, será a esta transacción. Las salidas de esta transacción coinbase serán nuevos **bitcoin** recien acuñados.

Características de la Transacción Coinbase

> - <span style="color: #9858b0;">Es la primera transacción en un bloque.</span>
> - <span style="color: #9858b0;">No tiene entradas válidas (no gasta UTXOs).</span>
> - <span style="color: #9858b0;">Genera nuevas monedas y recoge las tarifas de transacción.</span>
> - <span style="color: #9858b0;">El minero puede incluir datos arbitrarios en el campo de **coinbase**.</span>

La cantidad de **bitcoin** en una coinbase transaction se calcula como. 

` Recompensa = Subsidio + Tarifas de Transacción. `

Donde

> - <span style="color: #9858b0;">Subsidio **bitcoin** nuevos generados (inicialmente 50 **bitcoin**, actualmente 6.25 **bitcoin**).</span>
> - <span style="color: #9858b0;">Tarifas Acumulación de las comisiones de todas las transacciones del bloque.</span>

> **Satoshi Nakamoto** incluyó este mensaje como crítica al sistema financiero tradicional. **The Times 03/Jan/2009 Chancellor on brink of second bailout for banks**.
>
> **Bitcoin** impone una regla para evitar problemas con los **bloques huérfanos** y asegurar que las recompensas de minería sean legítimas antes de gastarse. Deben transcurrir 100 bloques (~16.6 horas en promedio) antes de poder usar esos **bitcoin**.

---

### Entradas y salidas. 

Veamos ahora lo que son las **entradas** y las **salidas** de una transacción. 

Cuando recibes **bitcoin** generas una dirección a donde los fondos te llegaran, en esa dirección es tu clave pública. Cuando quieras gastarlos, tendrás que desbloquearlos con tu **clave privada** firmándola. Así mismo la persona que te envia ese **bitcoin** desbloquerá los saldos que tiene con su llave privada. Este proceso es repetitivo cuando se crean transacciones, es decir, se generan entradas y salidas. 

Lo veremos con Alicia y Bob como ejemplo para que quede más claro. 

Alicia al recibir **bitcoin** tendrá una **entrada** y Bob al enviarlos tendrá una **salida**. 

Las salidas están bloquedas con un **scriptsig** que veremos en el siguiente apartado, por ahora solo quedate con que es un script de código que sirve para verificar la firma de la persona que recibirá los **bitcoin**. Estás salidas contienen una cantidad de **bitcoin** especifica (imagina que es una moneda de $20) y un bloqueo. 


**Nota**: si esta salida contiene una cantidad exacta, y tienes que enviar una cantidad menor a la contenida, se crearán varias salidas, como si dieras la moneda de $20 y se te regresara cambio.

 
> - <span style="color: #9858b0;">Cada **entrada** de una transacción refiere a un Unspent Transaction Output (UTXO) anterior. [Aquí](https://blueeemoon.github.io/bluemoon/bitcoin/utxo/) hay una infografía por si quieres saber más.</span>
> - <span style="color: #9858b0;">Cada **entrada** tiene un scriptSig que incluye la firma del remitente o txinwitness en el caso de SegWit.</span>
> - <span style="color: #9858b0;">Cada **salida** especifica cuánto **bitcoin** se envía y a quién.</span>
> - <span style="color: #9858b0;">Cada **salida** tiene un scriptPubKey que especifica las condiciones para gastar los bitcoin.</span>

---

### Bitcoin Script.

**Bitcoin** utiliza un sistema de script (códigos), [Bitcoin Script](https://en.bitcoin.it/wiki/Script) para las transacciones. Una moneda en **Bitcoin** está bloqueada con condiciones bajo las cuales se puede gastar. Las condiciones de bloqueo están codificadas con una clave ScriptPubKey. La prueba de desbloqueo está codificada en un scriptSig. Ambos forman un script completo y valido.

Cuando Bob desea gastar algunos **bitcoin**, debe proporcionar una transacción de **entrada** con un ScriptSig que incluye su firma y su clave pública. La red de **Bitcoin** combinará el ScriptSig de la **entrada** con el ScriptPubKey de la **salida** y ejecutará el script combinado para verificar la validez de la transacción.

Básicamente sería así:

> - <span style="color: #9858b0;">ScriptSig: script de desbloqueo, que requiere de una clave pública y una firma digital.</span>
> - <span style="color: #9858b0;">ScriptPubKey: script de bloqueo, que contiene un hash de clave pública, también denominada dirección.</span>

---

### Tipos de Transacciones.

**Bitcoin** permite múltiples tipos de transacciones según el ScriptPubKey utilizado:

> - <span style="color: #9858b0;">P2PKH (Pay-to-PubKey-Hash): Pago a una dirección estándar.</span>
> - <span style="color: #9858b0;">P2SH (Pay-to-Script-Hash): Para scripts más complejos (multisig, contratos).</span>
> - <span style="color: #9858b0;">SegWit (P2WPKH, P2WSH): Mejora la eficiencia y reduce fees.</span>
> - <span style="color: #9858b0;">Taproot (P2TR): Implementado en 2021 con Schnorr signatures.</span>

Si quieres profundizar más sobre los tipos de transacciones en este [enlace](https://ieeexplore.ieee.org/document/10477780) seguro aprenderás un montón. 

---

#### Gracias.

**Espero que esta información sea de utilidad.**


