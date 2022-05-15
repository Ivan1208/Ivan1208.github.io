---
layout: single
title: Creador de directorios de trabajo "htb" con bash
date: 2022-05-15
classes: wide
header:
  teaser: #/assets/images/slae32.png
categories:
  -bash
  -herramientas
  
tags:
  -hacking
---


Hola buenas , esta es una herramienta muy sencilla pero muy util , esta programada en bash y su funcion es la de crear de manera automatica
los directorios basicos de trabajo para resolver maquinas.



```

      #!/usr/bin/bash
      mkdir exploits
      mkdir info 
      mkdir nmap


'''

como veis el codigo es muy sencillo , para poder implementarla a vuestra consola debeis crearos un archivo (nombre.sh) 
en mi caso mkt.sh dentro de dicho archivo debeis introducir el codigo 
una vez que tengais el archivo creado tenemos que moverlo hacia /bin , esto es para que lo podamos ejecutar en cualquier directorio
lo que tenemos que hacer es lo siguiente:

'''

     sudo mv /tu_directorio/mkt.sh /usr/bin/
'''

con esto conseguimos que en cualquier momento podamos ejecutar el archivo sin necesidad de estar en su carpeta.
