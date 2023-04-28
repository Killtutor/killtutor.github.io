---
title: 'House Keeping 🧹🧽🧼✨'
date: 2023-04-28T12:00:00+00:00
draft: false
tags:
  - Servers
  - Housekeeping
  - healthy
categories:
  - servers
---

# Tools 🛠️
Vamos directo al grano, que herramientas son super utiles para mantener un ojo en tus servidores y mantenerlos saludables? aqui te va una lista y mas abajo vamos hablando de cada uno.

- [NCDU](https://dev.yorhel.nl/ncdu)
- [Health Check](https://healthchecks.io/)
- [HTOP](https://htop.dev/)
- [TMUX](https://github.com/tmux/tmux/wiki)


## NCDU 💾
Esta herramienta me parece la mejor para revisar en donde se esta gastando el espacio del disco duro en tu servidor. Es simplemente un analizador de espacio en disco, pero super ligero y completamente en la consola, me salvo 1 vez que no tenia nada de espacio en el disco y con los pocos KB que quedaban logre instalarlo y limpiar el servidor.
- Instalarlo es sencillo visita su pagina [NCDU](https://dev.yorhel.nl/ncdu) e instalalo como quieras, con un binario.. o con el manejador de paquetes de tu sistema operativo.
- Usarlo en sencillo.. puedes visitar su documentación [aqui](https://dev.yorhel.nl/ncdu/man)

como siempre lo uso para escanear todo el disco:
{{< highlight bash >}}
ncdu -q /
{{< /highlight >}}
Para salir de la interfaz de NCDU solo tienes que pulsar q en tu teclado.

## Health Check ❤️‍🩹🩺
Vigilar tus servidores no deberia ser un dolor de cabeza, por eso este sitio llega a ayudarnos a mantener un ojo en nuestros servidores mas criticos.
### Como funciona?
Entra a su [sitio web](https://healthchecks.io/) registrate y configura un check, un check es una direccion a la cual debes llamar cada cierto tiempo(el que configures) para establecer que todo esta funcionando perfecto, al momento que tu servidor no pueda cumplir con llamar al URL configurado healthCheck te deja saber notificandote por los medios que configures.

En resumen, healthcheck te da un Ping URL por cada check que configures, el servicio que quieres vigilar debe llamar constantemente al pingURL para notificar que todo bien, cuando no lo haga, algo anda mal y health check te notifica.

### Ejemplo de un healthCheck que uso en un servidor
Este healthCheck lo uso para verificar que seguimos conectados a un 3ero, el 3ero nos ofrecio un URL que nos responde 200 si todo funciona perfecto.
{{< highlight bash >}}
#!/bin/bash
StatusString=$(curl https://10.70.0.55/healthcheck -k)
echo $StatusString
if [[ $StatusString == *'"code": 200'* ]]; then
        wget --spider https://hc-ping.com/****-*****-******-*****-****
else
        echo negativo
fi
{{< /highlight >}}

## HTOP 🧐
Este servicio que en general lo traen instalados los servidores linux nos ofrece la posibilidad de observar el comportamiento del servidor, los procesos que lleva, el uso de la memoria, del procesador, etc.

