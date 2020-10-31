Turtle.py
=================

Librairies pour faire des shémas et de la géométrique
S"éxécute sur une nouvelle fenetre dans le web

function pré-défini

Nettoyer l'écran :
::

  turtle.clear()  #Efface les dessins du crayon
  turtle.reset()  #Fait de même et réinitialise le crayon

Avancer et reculer :
::

  turtle.forward(turtle.window_width()/3)  #Avance d'un tiers de la largeur de la fenêtre
  turtle.backward(turtle.window_width()/2)  #Recule de la moitié de la largeur de la fenêtre
  turtle.bk(50)  #Recule de 50px
  turtle.fd(0)  #Avance de 0px, donc n'avance pas

Se déplacer
::

  turtle.goto(100, 100)  #Position (100, 100)
  turtle.setx(20)  #Position(20, 100)
  turtle.sety(-80)  #Position(20, -80)
  turtle.home()  #Position(0, 0) (équivalent à turtle.goto(0, 0))

Lever ou baisser le crayon :
::

  turtle.up()  #Lève le crayon
  turtle.forward(150)  #Avance de 150px sans tracer
  turtle.down()  #Abaisse le crayon
  turtle.backward(50)  #Recule de 50px en traçant

Changer la taille du traçage :
::

print(turtle.pensize())  #Affiche '1'
turtle.pensize(5.5)  #Modifie la largeur du traçage
print(turtle.pensize())  #Affiche '5.5'

Changer l’angle
::

  turtle.setup()  #Initialise la fenêtre
  print(turtle.heading())  #Affiche 0.0 : le crayon pointe vers le point bleu : Est
  turtle.left(90)  #Pointe vers le point jaune : Nord
  turtle.right(270)  #Pointe vers le point vert : Ouest
  turtle.setheading(0)  #Pointe de nouveau vers le point bleu
  turtle.setheading(-90)  #Pointe à l'opposé du point jaune : Sud
  print(turtle.heading())  #Affiche '270.0'
  angle = turtle.towards(0, 90)
  print(angle)  #Affiche '90.0'
  turtle.setheading(angle)  #Angle : 90.0
  turtle.forward(90)  #Position : (0, 90); Angle : 90.0
  turtle.goto(0, 90)  #Position : (0, 90); Angle : 0.0

Figure simples :
::

  #Un exemple de triangle équilatéral
  longueur_cote = 200
  turtle.forward(longueur_cote)  #1er côté
  turtle.left(360/3)  #Angle
  turtle.forward(longueur_cote)  #2ème côté
  turtle.left(360/3)  #Angle
  turtle.forward(longueur_cote)  #3ème côté

  #Un exemple de carré
  longueur_cote = 200
  for i in range(4):
      turtle.forward(longueur_cote)  #Côté
      turtle.left(90)  #Angle

  #Un exemple d'octogone
  longueur_cote = 100
  for i in range(8):
      turtle.forward(longueur_cote)  #Côté
      turtle.left(360/8)  #Angle

Utiliser les cercles :
::

  turtle.circle(120)  #Trace un cercle de rayon 120px
  turtle.circle(70, 180)  #Trace un demi-cercle de rayon 70px
  turtle.circle(90, steps = 8)  #Trace un octogone de longueur 90px
  turtle.circle(40, 180, 4)  #Trace la moitié d'un octogone de longueur 40px

les points :
::

  turtle.dot(100, 'red')  #Imprime un point rouge d'un diamètre de 100px
  turtle.dot(50, 'yellow')  #Imprime un point jaune d'un diamètre de 50px
  turtle.dot(25)  #Imprime un point noir d'un diamètre de 25px


Remplir une figure d'une couleurs  :
::

    turtle.color('green')
    turtle.up()
    turtle.goto(x, 400)
    turtle.down()

    turtle.fillcolor('grey') # background color
    turtle.begin_fill() # begin color

    turtle.forward(300) #Forward turtle by 150 units ( width )
    turtle.left(90) #Turn turtle by 90 degree
    turtle.forward(600) #Forward turtle by 80 units ( height )
    turtle.left(90) #Turn turtle by 90 degree
    turtle.forward(300) #Forward turtle by 150 units ( width )
    turtle.left(90) #Turn turtle by 90 degree
    turtle.forward(600) #Forward turtle by 80 units ( height )
    turtle.left(90) #Turn turtle by 90 degree

    turtle.end_fill() # end color


Ecrire :
::

    turtle.write(str) qui écrit la chaîne de caractères donnée à la position courante
    turtle.write(str, True) qui érit et déplace la tortue à la fin du texte écrit.
    turtle.write("hello")
