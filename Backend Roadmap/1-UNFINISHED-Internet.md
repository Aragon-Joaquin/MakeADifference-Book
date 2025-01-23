#backend

> **Tabla de contenidos:**
- [[#Breve Introducción]]
- [[#Como funciona el internet]]
- [[#Glosario]]

# ==🔨ARTICLE IN CONSTRUCTION ==
---

## Breve Introducción

Antes de ir directamente a _"¿Que es el internet?"_ me gustaría definir el concepto de una **red**.

Una **red** es un grupo de computadoras (o cualquier otro dispositivo) que mantienen una conexión mediante un medio que lo hace posible. Por ejemplo, imagínate tu propia casa:
Probablemente tengas una o mas de una computadora, celular, consola o cualquier otro dispositivo electrónico que requieran de una *red* para que estos logren enviarse información del uno al otro. Al igual que tu vecino, que es probable que tenga una red de algunos dispositivos similares a los tuyos.
Todas estas redes unidas **forman el Internet**.

## Como funciona el internet

A un nivel superficial, el internet funciona conectando dispositivos entre si utilizando un **conjunto de protocolos estandarizados** que estos definen como va a ser intercambiada la información entre dispositivos y priorizar que los datos se transmitan de forma confiable y segura.

Cuando envías información a través del internet, esta misma es dividida en pequeños trozos llamados **"paquetes"** que son enviados desde tu dispositivo a tu **router[[#Router|*]]** para que luego este se encargue de como entregar esta información.

Para asegurar que estos paquetes sean enviados y recibidos correctamente, el internet usa una variedad de protocolos, como por ejemplo el **Protocolo de Internet (IP)** y el **Protocolo de transmisión de control (TCP)**.
El IP es el encargado de *enrutar[[#_Enrutar_|*]]* los paquetes mientras que el TCP se asegura que estos han sido transmitidos en el orden y forma correcta.

Además de estos protocolos, existen muchos mas que probablemente hayas oído anteriormente como el **Sistema de Nombres de Dominio (DNS)**, **Protocolo de Transferencia de Hipertexto (HTTP)**, **Capa de Sockets Seguros (SSL)**, entre otros.
Estos protocolos, como desarrolladores, tenemos que entenderlos ya que son fundamentalmente cruciales en nuestro trayecto para desarrollar software confiable y seguro.

## ☣ AUN TRABAJANDO EN ESTO...


---
## Glosario: 
##### > *Router*:
Explicando de una manera sencilla, los routers permiten guiar los datos del dispositivo que contienen información sobre el emisor, el tipo de dato (interacción web, archivo, etc...), dirección IP y su destino y el router tratara de leer esta capa, prioriza con que dato trabajar primero y elige la mejor ruta y protocolo para este. 
No confundir con _modem_.

##### > _Enrutar_:
En pocas palabras, selecciona las rutas para que los paquetes lleguen a su destino.