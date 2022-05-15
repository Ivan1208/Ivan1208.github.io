---
layout: single
title: Generador de contraseñas escrito en python
date: 2022-05-15
classes: wide
header:
  teaser: #/assets/images/slae32.png
categories:
  -python
  -herramientas
  -redes
tags:
  -python3
     
---

Muy buenas , esta es una herramienta la cual genera contraseñas a traves de diccionrarios aleatorios , esta herramienta puede servir para hacer ataques de fuerza bruta a algun usuario

```
    



    import random


    def main():
       n = [random.randint(8 , 15)]
       list_numbers = [random.randint(1 , 100000)for i in range(random.choice(n))]
       list_numbers = str(list_numbers)
       list_words = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
       list_characters = ["|" , "#" , "$" , "%" , "/" , "*" , "!"]
       n_p = (input("press [ENTER]  //:"))
       add_w = random.choice(list_words) +  random.choice(list_words) + random.choice(list_words) + random.choice(list_words) + random.choice(list_words) + random.choice(list_words)
       add_w2 = random.choice(list_words) +  random.choice(list_words) + random.choice(list_words) + random.choice(list_words) + random.choice(list_words) + random.choice(list_words)
       add_n = random.choice(list_numbers) +  random.choice(list_numbers) + random.choice(list_numbers) + random.choice(list_numbers) + random.choice(list_numbers) + random.choice(list_numbers)
       add_n2 = random.choice(list_numbers) +  random.choice(list_numbers) + random.choice(list_numbers) + random.choice(list_numbers) + random.choice(list_numbers) + random.choice(list_numbers)
       add_c = random.choice(list_characters) +  random.choice(list_characters) + random.choice(list_characters) + random.choice(list_characters) + random.choice(list_characters) + random.choice(list_characters)
       add_c2 = random.choice(list_characters) +  random.choice(list_characters) + random.choice(list_characters) + random.choice(list_characters) + random.choice(list_characters) + random.choice(list_characters)

       c = (add_w + add_n + add_c)
       c2 = (add_w2 + add_n2 + add_c2)



      print("The first password is" , c)
      print("The second password is" , c2)

     continue_ = True
     while continue_ == True:
        menu()
        main()
     eocp = int(input("to close the programm press 0 //:"))
     if eocp == 0:
        continue_ = False
     else:
        continue_ = True
'''

para descargar esta herramienta pueden ir a mi github -> Ivan1208 que aparece en el icono de la izquierda.
