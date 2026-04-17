---
title: "La importancia del tiempo en servidores Linux"
date: 2026-04-16
tags: [linux, servidores, tiempo, ntp, sysadmin]
---

# La importancia de mantener la hora en servidores

### Introduccion 
Cuando hablamos del tiempo en tecnología, un usuario promedio suele pensar que todo se reduce a cambiar la zona horaria para ver la hora correcta. Sin embargo, detrás de esto hay mucho más de lo que parece.

Una configuración incorrecta del tiempo en un sistema puede provocar problemas serios: desde la imposibilidad de acceder a ciertos sitios web —especialmente aquellos que dependen estrictamente de validaciones temporales— hasta fallas en autenticación, certificados caducados o errores en la comunicación entre servicios.

Si somos administradores de un servidor o de una aplicación web, este tema se vuelve aún más crítico. Las solicitudes que recibimos pueden provenir de distintas partes del mundo, y es fundamental registrar correctamente estos eventos en los logs. De lo contrario, podríamos enfrentarnos a inconsistencias, dificultades para depurar errores o incluso vulnerabilidades de seguridad.

En este artículo veremos por qué es tan importante mantener el tiempo correctamente configurado en nuestros sistemas y cómo podemos hacerlo de forma adecuada.


### Problemas por mala configuracion del tiempo
- Inconsistencias en logs y marcas de tiempo:
Los registros del sistema pueden no reflejar el orden real de los eventos. Por ejemplo, archivos recién creados pueden aparecer con fechas incorrectas, o accesos de usuarios pueden quedar fuera de secuencia, dificultando auditorías y análisis de incidentes.
- Fallos en sistemas distribuidos:
Cuando varios servidores deben comunicarse entre sí, una desincronización en el tiempo puede provocar retrasos, errores en la ejecución de tareas o incluso fallos totales en la coordinación entre servicios.
- Certificados inválidos:
Una hora incorrecta puede hacer que los certificados digitales parezcan expirados o aún no válidos, provocando la interrupción de servicios web y afectando directamente la experiencia del usuario.
- Ejecución incorrecta de tareas programadas:
Los trabajos programados (cron) pueden ejecutarse fuera de tiempo, no ejecutarse en absoluto o hacerlo en momentos inesperados, lo que puede impactar procesos críticos como respaldos o automatizaciones


### Zonas horarias
El planeta Tierra se divide en múltiples zonas horarias, que permiten estandarizar la hora en distintas regiones del mundo. Estas zonas están basadas en los meridianos, líneas imaginarias que recorren la Tierra de polo a polo.

El meridiano de referencia es el de Greenwich (0° de longitud), a partir del cual se define la hora base conocida como UTC (Tiempo Universal Coordinado). Todas las demás zonas horarias se calculan como una diferencia positiva o negativa respecto a este punto.

Por ejemplo, algunas regiones pueden operar en UTC-6 o UTC+1, dependiendo de su ubicación geográfica. Esto permite que cada zona mantenga una hora coherente con la posición del Sol, facilitando la organización global del tiempo.

En sistemas Linux, aunque podemos configurar una zona horaria local para mostrar la hora de forma entendible para los usuarios, internamente muchos servicios trabajan en UTC para evitar inconsistencias.

### ¿Qué significa longitud 0°?

La longitud 0° es el punto de referencia a partir del cual se mide la posición este-oeste en la Tierra. Esta línea imaginaria, conocida como el meridiano de Greenwich, atraviesa el Real Observatorio de Greenwich en Londres.

A partir de este meridiano, todas las ubicaciones del planeta se expresan en grados hacia el este (E) o hacia el oeste (W). Por ejemplo, países como México se encuentran al oeste de este punto, mientras que otros, como Japón, están al este.

Además de su uso geográfico, la longitud 0° tiene un papel fundamental en la medición del tiempo. Desde este punto se define el UTC (Tiempo Universal Coordinado), que sirve como base para establecer todas las zonas horarias del mundo.

En otras palabras, la longitud 0° funciona como la “línea base” tanto para ubicar lugares en el planeta como para organizar el tiempo a nivel global.



[Mas sobre el tiempo UTC](https://es.wikipedia.org/wiki/Tiempo_universal_coordinado)

[husos horarios (zonas horarias)](https://24timezones.com/mapa-husos-horarios)

Ahora que ya vimos la importancia y algunas consecuencias de mantener en orden los relojes de nuestros servidores, para evitar comportamientos anomalos o de alguna otra indole 

En linux, el tiempo del servidor se maneja con el comando 'timedatectl', este comando nos permitira saber la hora del servidor y moficiar esa fecha

Algunas de las opciones mas comunes son:

1. Mostrar la hora actual, la hora UTC, zona horaria y muestra si la sincronizacion esta activa, etc.

De igual manera podremos ver el archivo /etc/timezone, el cual tendra la zona horaria 

```
$ timedatectl


```

2. Zonas horarias disponibles. Estas zonas tambien estan disponibles en el directorio /usr/share/zoneinfo/

```
$ timedatectl list-timezones

```






Bibliografias 
---
https://www.iso.org/iso-639-language-code

https://es.quora.com/Por-qu%C3%A9-es-tan-importante-tener-correcta-la-hora-del-sistema-operativo

https://es.galsys.co.uk/about-NTP.html

https://www-masterclock-com.translate.goog/why-you-need-an-ntp-server.html?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc

https://www.appsignal.com/learning-center/why-should-my-app-and-server-use-UTC

https://serverfault.com/questions/685626/why-is-it-important-that-servers-have-the-exact-same-time

https://stackoverflow.com/questions/31031558/is-it-important-that-my-server-has-correct-locale-specific-timezone-set

https://macstadium.com/blog/explaining-time-zones-and-best-practices-for-configuring-time-on-servers

https://24timezones.com/mapa-husos-horarios

https://es.wikipedia.org/wiki/Tiempo_universal_coordinado

https://es.wikipedia.org/wiki/Reloj_at%C3%B3mico








