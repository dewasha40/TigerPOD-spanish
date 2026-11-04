> **Nota:** Esta traducción conserva exactamente los comandos, las rutas, los nombres técnicos y el código del proyecto.

# TigerPOD

[![Licencia: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-blue.svg)](LICENSE)

**Un reproductor de CD para bobinas.**

El TigerPOD es un lector y grabador **NFC / RFID de escritorio de código abierto para carretes de filamento de impresión 3D**, construido a partir de dos lectores básicos USB y una carcasa impresa en 3D. Coloca una bobina de filamento y el ordenador leerá su chip TigerTag: material, marca, color, temperaturas y cantidad restante. Para escribir (codificar) una etiqueta, basta con colocar la bobina. Sin apuntar ni buscar la etiqueta.

![El TigerPOD, impreso en todos los colores, cada uno con un carrete de filamento](assets/lineup/TigerPOD-lineup-9.jpg)

![El TigerPOD leyendo una bobina en Tiger Studio](assets/TigerPOD-demo.gif)

<sub>▶ Clip de mayor calidad: [TigerPOD-demo.mp4](assets/TigerPOD-demo.mp4)</sub>

> **Admite aproximadamente el 99 % de las bobinas de 1 kg**, ya sean bobinas maestras de plástico, de cartón, de plástico no reutilizables o de recambio. Basta con colocarlas en el Pod.

**Contenido:** [El primero de su tipo](#el-primero-de-su-tipo) · [Por qué existe](#por-qué-existe) · [Electrónica y diseño libres](#electrónica-y-diseño-libres) · [Una estación NFC universal](#más-que-tigertag-una-estación-nfc-universal) · [Comparativa de ecosistemas](#comparativa-de-los-ecosistemas-rfid-para-filamento) · [Construye uno](#construye-uno) · [Compra el kit](#o-compra-el-kit) · [El ecosistema](#el-ecosistema-que-lo-rodea) · [Lee una etiqueta con tu propio código](#lee-una-etiqueta-con-tu-propio-código) · [Preguntas frecuentes](#preguntas-frecuentes) · [Colabora](#colabora) · [Licencia](#licencia)

## El primero de su tipo

Hasta donde sabemos, **el TigerPOD es el primer lector/grabador NFC/RFID a escala de carrete de su tipo**; nadie había hecho esto antes. Fue imaginado por **Benoit Michaut**, un fabricante francés apasionado por la impresión 3D desde 2015, en **2023, junto con la creación del protocolo de código abierto TigerTag**: basta con colocar **dos lectores NFC USB estándar y económicos**, uno a cada lado de un soporte para bobinas impreso en 3D. Así se pueden leer y escribir a la vez los dos chips de una bobina de filamento. No hace falta una placa electrónica personalizada, un lector propietario ni un chip dedicado.

Eso convierte la codificación de chips NFC de un carrete (normalmente un proceso industrial cerrado) en algo que cualquiera puede construir en su escritorio por el precio de dos lectores básicos. El objetivo no es el dispositivo, es **democratizar RFID para filamento** a través del protocolo abierto [**TigerTag**](https://github.com/TigerTag-Project/TigerTag-RFID-Guide) para que cualquier fabricante, marca o impresor pueda adoptarlo libremente.

### De la fábrica a la mesa de la cocina

Esta es la parte importante. El TigerPOD es el **primer dispositivo de consumo para identificar materiales en la impresión 3D**: lleva al escritorio una capacidad que antes estaba reservada a la industria.

|  | Antes del TigerPOD | Después del TigerPOD |

|---|---|---|

| **¿Quién podría codificar chips de materiales?** | Sólo grandes fabricantes | Cualquiera, en casa |

| **Lo que hizo falta** | Codificadores industriales, hardware propietario, herramientas cerradas, contratos con proveedores | Dos lectores básicos USB y una impresión 3D |

| **Habilidades requeridas** | Especialista | Ninguno: sin electrónica ni soldadura |

| **Costo** | Gastos de capital | El precio de dos lectores baratos |

Hoy en día, en casa y por muy poco dinero, **cualquiera puede leer un chip, escribir uno nuevo, cambiar lo que ya tiene y limpiarlo nuevamente**. Antes de esto, esa tecnología estaba reservada a las grandes industrias. Ese cambio, no la carcasa de plástico, es lo que realmente es el TigerPOD.

Y funciona **para filamento, en Dual NFC** (ambos chips de un carrete a la vez) en **carretes estándar de cualquier marca**, con **cualquier tecnología de chip que admita el ACR122U** (MIFARE, NTAG y otros). No es el ecosistema de un solo proveedor: todos ellos.

<sub>*(Desarrolladores: eso es completo **CRUD** (crear, leer, actualizar, eliminar) en una etiqueta NFC.)*</sub>

¿Nuevo en RFID para filamento? Comience con la [**TigerTag Guía RFID**](https://github.com/TigerTag-Project/TigerTag-RFID-Guide): la especificación abierta y el registro público detrás del Pod.

## Por qué existe

El Pod se imaginó por primera vez para **programación masiva en fábricas de filamentos de terceros**. El encargo era exigente: una manera de codificar bobinas que sea **barata, fácil de construir localmente y duplicable en grandes cantidades al menor costo posible**, sin renunciar a ninguna capacidad. Con lectores básicos y una carcasa impresa, el **costo de desarrollo es esencialmente cero**: un Pod se puede producir en cualquier parte del mundo, localmente y en cantidad.

El ACR122U es intencionado: es un lector extremadamente común, **fácil de encontrar en cualquier lugar por muy poco dinero**. Y no hay nada que aprender: **sin conocimientos de electrónica, sin soldadura, sin dificultades**. Imprime la carcasa, introduce dos lectores: un niño de cinco años podría montar un TigerPOD.

Desde ese origen en la fábrica, luego **llevamos el Pod a todos** con el lanzamiento de la aplicación de escritorio [**Tiger Studio Manager**](https://github.com/TigerTag-Project/TigerTag-Studio-Manager): la misma potencia de codificación en el escritorio de cualquier fabricante, no solo en una línea de producción.

Esta es la premisa fundamental de un proyecto de código abierto que es **neutral e agnóstico, no vinculado a ningún fabricante de impresoras ni a ninguna marca de filamentos**. La cuestión es poner el máximo valor en manos de todos y ofrecer una ruta realmente de bajo coste para los usuarios **en todo el planeta**.

Por eso también funciona con **todos los NTAG, hasta el pequeño NTAG 213**: optimizamos cada byte del chip para empaquetar la mayor cantidad de datos en el menor espacio. Y debido a que un chip TigerTag es una etiqueta NFC estándar, **cualquier teléfono con un lector NFC puede leerlo**, por lo que puede leer *y escribir* chips TigerTag con nada más que un teléfono inteligente, sin necesidad de Pod.

## Electrónica y diseño libres

No hay silicio personalizado en un TigerPOD, y ese es el punto:

- **Dos [lectores ACR122U compatibles con NFC](https://amzn.to/4vok3d7)**: hardware básico, vendido en todas partes y por todos.

- **Una única carcasa impresa con 3D** con dos ranuras: desliza un ACR122U en cada lado.

Sin montaje, sin tornillos, sin cableado.

- **Un divisor** (2× USB-B → 1× USB-C) para que todo sea un cable ordenado.

<p> <img src="assets/TigerPOD-reader-acr122u.jpg" alt="ACR122U-compatible USB NFC reader" width="200"> <img src="assets/TigerPOD-reader-acr122u.jpg" alt="ACR122U-compatible USB NFC reader" width="200"> <img src="assets/TigerPOD-splitter.jpg" alt="2-to-1 USB splitter" width="200"> </p>

<sub>Las tres partes que utilizamos: dos [lectores compatibles con ACR122U](https://amzn.to/4vok3d7) + un [divisor USB](https://amzn.to/4plgsv8): dos lectores van en cada unidad.</sub>

### ¿Por qué dos chips y dos lectores?

La configuración recomendada es **dos chips NFC por carrete y dos lectores NFC**: un chip a cada lado del carrete, un lector frente a cada chip:

- **Sin apuntar.** Cualquiera que sea la forma en que coloques el carrete, siempre habrá un chip delante de un

lector. Nada que hacer fila.

- **Twin Tag permanece sincronizado.** Con un lector en cada lado, el Pod lee y escribe

**ambos chips a la vez**: el par permanece en bytes idénticos y su inventario cuenta con un carrete, no con dos etiquetas.

Un solo chip y un solo lector aún funcionan, pero se pierde la comodidad de colocar y usar (debe presentar el lado etiquetado) y la sincronización automática de Twin Tag.

Cualquier [NTAG 213/215/216](https://amzn.to/3TzxGc7) funciona. Nada es propietario, nada llama a casa.

### Es un concepto, no un producto fijo.

Si lo quitamos, el TigerPOD es una idea: **dos lectores ACR122U uno frente al otro, mantenidos a la distancia adecuada mediante un soporte impreso 3D.** Eso es todo.

La carcasa que publicamos simplemente sostiene un **una bobina estándar de 1 kg**, pero **la forma es tuya para cambiarla**. Rediseña el soporte para otro formato de bobina, otro objeto o un uso completamente diferente, y sigue siendo un Pod. Sólo importan los dos lectores enfrentados; el titular que los rodea es un detalle de implementación. Mézclalo y [comparte lo que haces](CONTRIBUTING.md).

Hicimos exactamente eso nosotros mismos: ahora hay **dos carcasas para imprimir**, el mismo concepto de dos lectores:

<img src="assets/TigerPOD-mini.jpg" align="right" width="230" alt="The compact TigerPOD Mini reading a bobina">

- **[TigerPOD Mini](https://makerworld.com/fr/models/3190348-tigerpod-mini-for-openbobina-tigertag-rfid-filament)** — *recomendado.* Una carcasa rediseñada y más compacta: **imprime más rápido**, **utiliza menos filamento**, ocupa **menos espacio en el escritorio** y **enruta los cables por el interior** (gestión de cables integrada). Los mismos dos lectores ACR122U uno frente al otro, leen y escriben etiquetas **TigerTag** y **OpenSpool** (NDEF). Es simplemente un Pod mejor que el original.

- **[TigerPOD (original)](https://makerworld.com/fr/models/1289152-tigertag-io-open-bobina-pod-for-rfid-filament)** — la primera carcasa, del tamaño de un carrete estándar de 1 kg.

Ambos son el mismo Pod debajo de la piel: elige el que mejor se adapte a tu escritorio.

<br clear="right">

<sub>▲ El TigerPOD Mini: un lector vertical a cada lado, cables escondidos en el interior.</sub>

Y como lo imprimes tú mismo, **viene en cualquier color que cargues.** El mismo Pod, tu filamento:

<p> <img src="assets/pods/TigerPOD-red.jpg" width="108" alt="Red TigerPOD"> <img src="assets/pods/TigerPOD-orange.jpg" width="108" alt="Orange TigerPOD"> <img src="assets/pods/TigerPOD-yellow.jpg" width="108" alt="Yellow TigerPOD"> <img src="assets/pods/TigerPOD-green.jpg" width="108" alt="Green TigerPOD"> <img src="assets/pods/TigerPOD-cyan.jpg" width="108" alt="Cyan TigerPOD"> <img src="assets/pods/TigerPOD-blue.jpg" width="108" alt="Blue TigerPOD"> <img src="assets/pods/TigerPOD-purple.jpg" width="108" alt="Purple TigerPOD"> <img src="assets/pods/TigerPOD-pink.jpg" width="108" alt="Pink TigerPOD"> <img src="assets/pods/TigerPOD-gold.jpg" width="108" alt="Gold TigerPOD"> <img src="assets/pods/TigerPOD-copper.jpg" width="108" alt="Copper TigerPOD"> <img src="assets/pods/TigerPOD-silver.jpg" width="108" alt="Silver TigerPOD"> <img src="assets/pods/TigerPOD-grey.jpg" width="108" alt="Grey TigerPOD"> <img src="assets/pods/TigerPOD-black.jpg" width="108" alt="Black TigerPOD"> <img src="assets/pods/TigerPOD-white.jpg" width="108" alt="White TigerPOD"> <img src="assets/pods/TigerPOD-glow.jpg" width="108" alt="Glow-in-the-dark TigerPOD"> </p>

<sub>A algunos de los colores en los que se ha impreso, además de marrón, leche, verde pastel y gris claro en [`assets/pods/`](assets/pods).</sub>

Y haga lo que haga su filamento, el Pod también lo hace: seda, galaxia, mármol, brillo en la oscuridad:

<p> <img src="assets/pods/TigerPOD-silk-red.jpg" width="108" alt="Silk red TigerPOD"> <img src="assets/pods/TigerPOD-silk-pink.jpg" width="108" alt="Silk pink TigerPOD"> <img src="assets/pods/TigerPOD-silk-yellow.jpg" width="108" alt="Silk yellow TigerPOD"> <img src="assets/pods/TigerPOD-silk-blue.jpg" width="108" alt="Silk blue TigerPOD"> <img src="assets/pods/TigerPOD-silk-black.jpg" width="108" alt="Silk black TigerPOD"> <img src="assets/pods/TigerPOD-silk-gold.jpg" width="108" alt="Silk gold TigerPOD"> <img src="assets/pods/TigerPOD-silk-copper.jpg" width="108" alt="Silk copper TigerPOD"> <img src="assets/pods/TigerPOD-silk-silver.jpg" width="108" alt="Silk silver TigerPOD"> <img src="assets/pods/TigerPOD-galaxy-purple.jpg" width="108" alt="Galaxy purple TigerPOD"> <img src="assets/pods/TigerPOD-marble.jpg" width="108" alt="Marble TigerPOD"> <img src="assets/pods/TigerPOD-rainbow-linear.jpg" width="108" alt="Linear rainbow TigerPOD"> <img src="assets/pods/TigerPOD-rainbow-multi.jpg" width="108" alt="Multicolour rainbow TigerPOD"> <img src="assets/pods/TigerPOD-glow-green-dark.jpg" width="108" alt="Green glow-in-the-dark TigerPOD, lights off"> <img src="assets/pods/TigerPOD-glow-blue-dark.jpg" width="108" alt="Blue glow-in-the-dark TigerPOD, lights off"> <img src="assets/pods/TigerPOD-glow-red-dark.jpg" width="108" alt="Red glow-in-the-dark TigerPOD, lights off"> </p>

<sub>Los originales de resolución completa se encuentran en [`assets/pods/hd/`](assets/pods/hd) y los recortes PNG transparentes (sin fondo) en [`assets/pods/cutout/`](assets/pods/cutout).</sub>

## Más que TigerTag: una estación NFC universal

El Pod **no está bloqueado con el protocolo TigerTag**. Se trata, literalmente, de dos lectores PC/SC estándar en un soporte con forma de carrete: **cualquier cosa que un ACR122U pueda hacer, el Pod puede hacerlo.**

**Tú controlas el chip por completo.** Lee lo que hay en una etiqueta, escribe algo nuevo en ella, cambia lo que ya está ahí y bórralo para dejarlo en blanco. El Pod hace las cuatro cosas: sin calle de un solo sentido, sin escritura única, sin bloqueo de proveedor. *(Desarrolladores: eso es completo **CRUD**: crear, leer, actualizar, eliminar).*

Para ser precisos en cuanto al alcance, eso significa control total de lectura/escritura/borrado **para filamento, en NFC dual** (ambos chips de un carrete manejados juntos) en **carretes de filamento estándar**, en **cualquier marca** y **cualquier tecnología de chip que admita el ACR122U** (MIFARE, NTAG y el resto). No son carretes de una sola marca. Ninguna familia de chips. Cualquiera de ellos.

**Un lector/grabador universal.** El ACR122U maneja mucho más que NTAG. Cubre **ISO 14443 Tipo A y B**, **MIFARE** (Classic 1K/4K, Ultralight, DESFire), **FeliCa**, **Topaz/Jewel** y **NFC Tipos de etiquetas de foro 1 a 4**. Todo lo que puedas leer o escribir con un ACR122U, podrás leerlo o escribirlo en el Pod.

**Nunca bloqueado, infinitamente reutilizable.** Un TigerTag **nunca está bloqueado contra escritura**. Cuando un carrete esté listo, borre y reescriba sus chips como TigerTags nuevos, tantas veces como desee.

**Dé una segunda vida a los chips de bobina al final de su vida útil.** Reciclelos para convertirlos en algo completamente diferente: reprograme un NTAG como una simple etiqueta **NDEF** y utilícelo para **automatización del hogar, objetos conectados, transferencia de Wi-Fi, una URL, una tarjeta de presentación**: cualquier caso de uso de NFC que desee. Y podrás volver a convertirlo en un TigerTag cuando quieras. El Pod escribe **en ambos sentidos**. El chip es un activo reutilizable, no un embalaje de un solo uso: **cero residuos electrónicos**.

## Comparativa de los ecosistemas RFID para filamento

La mayoría de los fabricantes de impresoras etiquetan sus carretes. Casi todos cierran la etiqueta. Aquí está el paisaje y dónde se encuentra TigerTag:

| Ecosistema | viruta | ¿Puedes escribir tu propia etiqueta? | Android | iOS |

|---|---|---|:---:|:---:|

| **TigerTag** | NTAG 213 / 215 / 216 | **Sí** — nunca bloquear, borrar y reescribir para siempre | ✅ | ✅ |

| [Lienzo Elegoo](https://github.com/ELEGOO-3D/ELEGOO-RFID-Tag-Guide) | NTAG213 | Sí, sin cifrado, sin contraseña, documentado públicamente | ✅ | ✅ |

| [Anycubic ACE](https://help.simplyprint.io/en/article/all-about-nfc-rfid-for-filament-bobinas-bambu-openprinttag-creality-qidi-anycubic-more-19luyni/) | NTAG215/216 | Sí | ✅ | ✅ |

| [Laboratorio de Bambú](https://github.com/Bambu-Research-Group/RFID-Tag-Guide) | MIFARE Clásico 1K | **No**: los datos están cifrados *y* firmados por RSA; la impresora rechaza cualquier etiqueta sin firma válida | ⚠️ | ❌ |

| [Creality CFS](https://help.simplyprint.io/en/article/the-creality-material-standard-nfcrfid-for-the-creality-cfs-1crrofa/) | MIFARE Clásico 1K | No oficialmente: propietario e indocumentado; sólo las herramientas comunitarias de ingeniería inversa pueden hacerlo | ⚠️ | ❌ |

| [Caja QIDI](https://help.simplyprint.io/en/article/the-qidi-material-standard-nfcrfid-for-the-qidi-box-ns0c8d/) | MIFARE Clásico 1K | No oficialmente: formato propietario | ⚠️ | ❌ |

| [Mesero U1](https://snapmakeru1-extended-firmware.pages.dev/rfid_support) | MIFARE Clásico 1K | **No** — propietario + firma RSA, solo etiquetas oficiales | ⚠️ | ❌ |

<sub>✅ funciona · ⚠️ solo en teléfonos Android cuyo chipset NFC es compatible con MIFARE Classic (un chipset de la familia NXP; no está garantizado en todos los dispositivos Android) · ❌ imposible: Apple no expone MIFARE Classic a aplicaciones, en ningún iPhone.</sub>

No confíe en nuestra palabra sobre la división: dos proyectos independientes lo resuelven de la misma manera.

[**OpenRFID**](https://github.com/suchmememanyskill/OpenRFID), una biblioteca de terceros que analiza etiquetas de filamentos de todas las marcas principales, enruta Bambu Lab, Creality, QIDI y Snapmaker a través de su ruta *autenticada MIFARE Classic* (se requieren claves), mientras que Elegoo, Anycubic y **TigerTag** pasan por su *NTAG* simple. ruta: sin claves, sin autenticación.

[**xbobina**](https://github.com/xperiments/xbobina), un administrador de bobina compatible con Bambu Lab, Creality CFS, Anycubic ACE Pro y TigerTag, publica su propia tabla de capacidades. Esta es **su tabla, no la nuestra**; no escribimos ni una línea:

| Formato | Tipo de etiqueta | Legible | Escribible | Metadatos adicionales |

|---|---|:---:|:---:|:---:|

| **TigerTag** | NTAG 213/215/216 | ✅ | ✅ | ✅ |

| Oficial de BambuLab | MIFARE 1K | ✅ | ❌ | ❌ |

| Creality CFS | MIFARE 1K | ✅ | ✅ | ❌ |

| Anycubic ACE PRO | NTAG 213/215/216 | ✅ | ✅ | ❌ |

<sub>Fuente: [xbobina — formatos admitidos](https://github.com/xperiments/xbobina/blob/main/docs/vendors/vendors.md)</sub>

Bambu Lab es el único que no se puede escribir. Y TigerTag es el único formato en esa tabla que admite **lectura, escritura *y* metadatos adicionales**.

TigerTag se implementa en ambos proyectos, junto con los grandes, por personas que no tienen ningún interés en ellos.

De esa mesa se caen dos cosas.

**El bloqueo es criptográfico, no físico.** Un chip MIFARE Classic 1K es perfectamente regrabable, pero Bambu Lab y Snapmaker firman su carga útil, por lo que la impresora rechaza una etiqueta que usted escribe. El chip que tienes en la mano está bien; el ecosistema simplemente no lo aceptará. TigerTag no firma nada que no puedas reproducir ni bloquea nada: la etiqueta sigue siendo tuya.

**MIFARE Classic bloquea tu teléfono.** Apple no permite que las aplicaciones se comuniquen con las etiquetas MIFARE Classic, por lo que **ningún iPhone puede leer una etiqueta de carrete Bambu, Creality, QIDI o Snapmaker**, nunca. Eso excluye aproximadamente la mitad de los teléfonos del planeta, de forma permanente, según la política de plataforma. Incluso en Android no es un hecho: MIFARE Classic es una tecnología NXP, y los teléfonos cuyo chipset NFC no es de esa familia tampoco pueden leerlo.

**Así que elegimos NTAG a propósito.** Esta es la razón por la que TigerTag se basa en NTAG y no en MIFARE: **todos los teléfonos inteligentes NFC leen un NTAG, sin restricciones, sin lista blanca de aplicaciones, sin permiso de proveedor**, tanto Android como iPhone. Una etiqueta que cualquiera puede leer con el dispositivo en su bolsillo no es un ecosistema de proveedores; es un **estándar público y universal**. Ese era el punto.

<sub>Un límite honesto: OpenPrintTag de Prusa usa NXP ICODE SLIX (ISO 15693), una familia que el ACR122U no cubre; esas etiquetas están fuera del rango del Pod.</sub>

## Construye uno

1. Imprime una carcasa: la compacta

[**TigerPOD Mini**](https://makerworld.com/fr/models/3190348-tigerpod-mini-for-openbobina-tigertag-rfid-filament) (recomendado) o el [original](https://makerworld.com/fr/models/1289152-tigertag-io-open-bobina-pod-for-rfid-filament), ambos en MakerWorld. Consulte [Dos carcasas para imprimir](#más-que-tigertag-una-estación-nfc-universal).

2. Consigue dos [lectores compatibles con ACR122U] (https://amzn.to/4vok3d7), en cualquier tienda que desee

(y algunas [etiquetas NTAG 213/215/216](https://amzn.to/3TzxGc7) para escribir).

3. Introduce un lector en cada ranura: sin tornillos, sin pegamento ni cableado.

4. Conecta ambos a su computadora (el divisor lo convierte en un solo cable, pero dos puertos también funcionan).

5. Instala [Tiger Studio](https://github.com/TigerTag-Project/TigerTag-Studio-Manager) —

detecta los lectores automáticamente.

### Lista de materiales

Precios aproximados, obtenidos por separado: su millaje variará según la tienda y la región.

| Parte | Cantidad | Aprox. precio | Notas |

|---|---|---|---|

| [Lector NFC compatible con ACR122U](https://amzn.to/4vok3d7) | 2 | ~15–25€ cada uno | Uno por lado del carrete |

| [NTAG 213/215/216 etiquetas](https://amzn.to/3TzxGc7) | 1 paquete | ~10–20€ | Dos fichas por carrete; un paquete etiqueta muchos carretes |

| 3D-carcasa impresa | 1 | sólo filamento | [Imprimirlo](https://makerworld.com/fr/models/1289152-tigertag-io-open-bobina-pod-for-rfid-filament) usted mismo |

| [Divisor USB (2× USB-A F → 1× USB-A M)](https://amzn.to/4plgsv8) | 1 | ~5–10€ | Opcional: dos puertos USB también funcionan |

### Compatibilidad del lector

El ACR122U habla sobre **PC/SC** (PC/SC es el estándar de tarjeta inteligente a nivel de sistema operativo que implementa cada lector de esta clase). Debido a que el Pod se basa en PC/SC en lugar de en un controlador de proveedor, la misma configuración se ejecuta en todos los sistemas operativos de escritorio y cualquier biblioteca de PC/SC puede controlarlo:

- **Windows**: reconocido de fábrica; el servicio PC/SC (`SCardSvr`) se envía con

Ventanas. Si un controlador "ayudante" de emulación de tarjetas secuestra el lector, elimínelo para que el dispositivo aparezca como un lector PC/SC simple.

- **macOS**: funciona con la pila PC/SC integrada (`pcscd`); no se necesita ningún controlador adicional.

- **Linux** — instale PC/SC y el controlador ACS/CCID, p.e.

`sudo apt install pcscd libacsccid1`, luego asegúrese de que el servicio `pcscd` se esté ejecutando.

## O compra el kit

El kit electrónico en [la tienda](https://shop.tigertag.io/collections/tigertag-rfid-maker) cuesta menos que comprar las mismas piezas usted mismo, los lectores llegan con el logotipo oficial del proyecto y financia el estándar:

- [Paquete TigerPOD: 2 lectores + divisor](https://shop.tigertag.io/products/tigertag-player-bundle-2pcs-spliter)

- [Lector único](https://shop.tigertag.io/products/tigertag-player)

- [Divisor solo](https://shop.tigertag.io/products/tigertag-splitter)

El paquete es **solo electrónica**: dos lectores con el logotipo oficial y el divisor. Todavía debes [imprimir el carcasa TigerPOD](https://makerworld.com/fr/models/1289152-tigertag-io-open-bobina-pod-for-rfid-filament) tú mismo y deslizar los lectores. Construir todo a partir de partes genéricas no es un camino menor: es el mismo Pod. Eso es lo que significa un protocolo abierto.

## El ecosistema que lo rodea

![El sistema TigerTag: TigerPOD, la aplicación de escritorio Tiger Studio y la aplicación móvil comparten un solo carrete](assets/TigerPOD-hero-system.png)

| | |

|---|---|

| **El protocolo** | [TigerTag-RFID-Guide](https://github.com/TigerTag-Project/TigerTag-RFID-Guide): la especificación y el registro público (CC-BY-4.0, concesión de implementación irrevocable) |

| **Tiger Studio** | [Aplicación de escritorio](https://github.com/TigerTag-Project/TigerTag-Studio-Manager) (MIT): inventario, impresoras y la conexión con el Pod |

| **SDK** | [JS](https://github.com/TigerTag-Project/TigerTag-SDK-JS) · [Python](https://github.com/TigerTag-Project/TigerTag-SDK-Python) (Apache-2.0) |

| **Comunidad** | [Discordia](https://discord.gg/3Qv5TSqnJH) |

En un teléfono no necesitas ningún Pod: la aplicación móvil utiliza el propio NFC del teléfono. El Pod es el NFC del escritorio.

## Lee una etiqueta con tu propio código

TigerTag almacena todo **en el chip**: sin búsqueda, sin red. La lectura son siempre los mismos dos pasos, sea cual sea el idioma:

1. **Consigue los bytes sin procesar** de la etiqueta con cualquier biblioteca NFC: el **UID de 7 bytes** y el

**memoria de usuario, páginas `0x04`–`0x27`** (36 páginas × 4 bytes = **144 bytes**).

2. **Descodifique sin conexión** entregándolos al SDK TigerTag — `fromPages(uid, payload)` en

JS, `from_pages(uid, payload)` en Python. El SDK devuelve material, marca, color, temperaturas, peso y (opcionalmente) verifica la firma.

El SDK nunca toca al lector: usted trae los bytes y él los analiza. Así que lo emparejas con cualquier biblioteca NFC que se ajuste a tu plataforma:

| Plataforma | Biblioteca NFC | Notas |

|---|---|---|

| **Escritorio — Nodo/Electrón** | [`nfc-pcsc`](https://www.npmjs.com/package/nfc-pcsc) | Qué utiliza Tiger Studio para controlar los lectores ACR122U del Pod a través de PC/SC |

| **Escritorio — Python** | [`nfcpy`](https://nfcpy.readthedocs.io) o [`pyscard`](https://pyscard.sourceforge.io) (PC/SC) | `pyscard` coincide directamente con la ruta PC/SC de ACR122U |

| **Android** | `MifareUltralight` / `NfcA` (integrado) | `readPages(4)`, cuatro páginas a la vez |

| **iOS** | Core NFC (`NFCTagReaderSession`) | Lectura sin procesar de MiFare de las páginas 4 a 39 |

| **Flutter** | [`flutter_nfc_kit`](https://pub.dev/packages/flutter_nfc_kit) | `transceive` el comando NTAG `READ` (`0x30`) |

| **Arduino/ESP32** | [`MFRC522`](https://github.com/miguelbalboa/rfid) | `MIFARE_Read` página por página, UID de envío + carga útil a través de serie |

En los repositorios del SDK se encuentran ejemplos ejecutables de copiar y pegar para cada uno: [JS](https://github.com/TigerTag-Project/TigerTag-SDK-JS/blob/main/examples/integrate_nfc_sdk.js) · [Python](https://github.com/TigerTag-Project/TigerTag-SDK-Python/blob/main/examples/integrate_nfc_sdk.py).

### Prueba el Pod con el entorno de pruebas integrado

Ambos SDK incluyen un **patio de juegos** (un pequeño servidor local más una página web) para que puedas probar un Pod sin escribir ningún código primero:

- **[SDK de JS](https://github.com/TigerTag-Project/TigerTag-SDK-JS)** — `npm install ws nfc-pcsc`

luego `npm run playground` y abra `http://localhost:7432/tools/playground.html`. Se conecta directamente al ACR122U a través de PC/SC y envía **eventos de tarjeta en vivo** a la página: coloque un carrete en el Pod y observe cómo se decodifica en el navegador.

- **[SDK de Python](https://github.com/TigerTag-Project/TigerTag-SDK-Python)** — ejecutar

`python3 tools/server.py` y abra la misma página para inspeccionar y diferenciar cargas útiles.

Es la forma más rápida de confirmar que sus lectores sean vistos y que sus etiquetas se analicen correctamente.

## Preguntas frecuentes

**¿Puedo usar solo un lector?** Sí, pero pierde la comodidad de colocar y usar y la sincronización automática de Twin Tag; consulte [Por qué dos chips y dos lectores](#es-un-concepto-no-un-producto-fijo).

**No se detecta mi lector.** Asegúrese de que sea un lector genuino compatible con ACR122U (PC/SC). En Linux, inicie el servicio `pcscd` e instale el controlador CCID. Desenchufe/vuelva a enchufar una vez, luego reinicie Tiger Studio.

**NTAG 213 vs 215 vs 216: ¿cuál?** Se diferencian sólo en la memoria: 213 (~144 B), 215 (~504 B), 216 (~888 B). Cualquiera de ellos posee un registro TigerTag; Elija 215/216 si desea más espacio libre. Los tres trabajan en el Pod.

**¿Qué carretes encajan?** Aproximadamente el **99 % de los carretes de 1 kg**, independientemente del tipo: los carretes maestros de plástico, los carretes de cartón, los carretes de plástico no reutilizables y los recambios se colocan en el Pod.

**¿Puedo reutilizar las etiquetas?** Sí, las TigerTags nunca se bloquean. Bórrelos y reescríbalos como nuevos TigerTags indefinidamente, o conviértalos en una etiqueta NDEF simple para otro uso NFC (domótica, objetos conectados, una URL, una tarjeta de presentación) y viceversa. El chip es un activo reutilizable, no un envase desechable.

**¿Puedo usar el Pod para trabajos que no sean TigerTag NFC?** Sí. Son dos lectores ACR122U estándar, por lo que pueden leer, escribir, reescribir y borrar cualquier cosa que admita un ACR122U (CRUD completo, en términos de desarrollador): ISO 14443 A/B, MIFARE (Classic, Ultralight, DESFire), FeliCa, Topaz/Jewel y NFC Tipos de foro 1–4. El Pod es una estación de lectura/escritura universal NFC que tiene forma de carrete.

**¿Necesita Internet?** No. El Pod lee y escribe localmente; nada llama a casa.

## Apoya el proyecto

TigerSystem es un proyecto comunitario personal de código abierto, creado y mantenido en su tiempo libre. Todo sigue siendo gratis; Si te ahorra uno o dos carretes, puedes respaldarlo:

- ☕ [Cómprame un café](https://buymeacoffee.com/benoitl)

- ❤️ [Ko-fi](https://ko-fi.com/tigersystemio)

- 💙 [PayPal](https://paypal.me/tigersystemio)

El soporte va para el mantenedor: nunca es necesario, siempre se agradece.

## Colabora

Se aceptan versiones modificadas de la carcasa, fotos de montaje, correcciones de documentos y traducciones; consulte [CONTRIBUTING.md](CONTRIBUTING.md).

## Licencia

La documentación en este repositorio es **CC-BY-4.0** (ver [LICENCIA](LICENSE)). El nombre y el logotipo TigerTag son marcas comerciales de TigerTag Corp; términos de uso en [TRADEMARK.md](https://github.com/TigerTag-Project/TigerTag-RFID-Guide/blob/main/TRADEMARK.md).

`assets/` también incluye el kit oficial de íconos "Tiger": variantes neutrales (sin texto) y marcadas con "TIGER TAG", cada una enviada como composiciones desbordadas (se muestran tal como están), contenidas y cuadradas (para contextos enmascarados como favicons redondos o íconos adaptativos). Se aplican los mismos términos de marca registrada: las pautas de uso completas se encuentran en [brand/README.md](https://github.com/TigerTag-Project/TigerTag-RFID-Guide/blob/main/brand/README.md) del repositorio de protocolo principal.

Sitio web: [tigersystem.io](https://tigersystem.io) · Tienda: [shop.tigertag.io](https://shop.tigertag.io/collections/tigertag-rfid-maker)

Preguntas, asociaciones, prensa: [tigertag@tigertag.io](mailto:tigertag@tigertag.io)

### Material para prensa

La prensa y los socios pueden utilizarlos, en [CC-BY-4.0](LICENSE) (crédito TigerTag):

| | |

|---|---|

| **Fotos de héroe/alineación** | [`assets/lineup/`](assets/lineup): la línea completa de Pod, ideal como imagen de portada |

| **Fotos del producto** | [`assets/pods/`](assets/pods) — 34 Pods individuales, uno por color y acabado |

| **El sistema** | [`TigerPOD-hero-system.png`](assets/TigerPOD-hero-system.png) — Pod + aplicación de escritorio + aplicación móvil |

| **El Mini** | [`TigerPOD-mini.png`](assets/TigerPOD-mini.png) — el modelo Mini compacto (PNG transparente) |

| **En uso** | [`TigerPOD-demo.mp4`](assets/TigerPOD-demo.mp4) · [`TigerPOD-demo.gif`](assets/TigerPOD-demo.gif) |

| **Piezas** | [`TigerPOD-reader-acr122u.jpg`](assets/TigerPOD-reader-acr122u.jpg) · [`TigerPOD-splitter.jpg`](assets/TigerPOD-splitter.jpg) |

Cada imagen viene en tres formatos: un JPG optimizado para la web, un original de resolución completa en `hd/` y un PNG transparente sin fondo en `cutout/`.

---

<sub>Algunos enlaces de hardware anteriores son enlaces de afiliados de Amazon: como asociado de Amazon, TigerTag gana con compras que califican, sin costo adicional para usted. Ayuda a financiar el protocolo abierto.</sub>

Agentes <sub>AI y LLM: un resumen legible por máquina de este proyecto se encuentra en [llms.txt](llms.txt).</sub>