## Python

[Docs Python](https://docs.python.org/fr/3/)

## Variable et dictionnaire



    a = 1

    dico = {clé 1:valeur 1, clé 2:valeur 2}
    dico = dict(clé 1=valeur 1, clé 2=valeur 2)
    print dico
    {clé 1: valeur 1, clé 2: valeur 2}

## Condition

    if os.path.exists(path):
            # Delete old app/static/img/diagram.svg
            os.remove(path) # specifying the path of the file for delete old diagram
    elsif:
      print("elsif")
    else:


    # On fait un test pour savoir si a est comprise dans l'intervalle allant de 2 à 8 inclus

    a = 5
    if a >= 2:
        if a <= 8:
            print("a est dans l'intervalle.")
        else:
            print("a n'est pas dans l'intervalle.")
    else:
        print("a n'est pas dans l'intervalle.")

## Boucle

    for nodes in rectangle:
        #node left
        turtle.goto(n,m)
        turtle.down()
        turtle.color('blue')
        turtle.circle(25) #50 good
        #turtle.circle(50, 180)  #Trace un demi-cercle de rayon 70px
        turtle.up()

## fonction

    def nameFunction():
        i = 5
        return i

## Mannipuller les chaines de charactére

    txtLabel[0:25] # prend les 25 premieres lettres, si négatif = partant de la fin
    txtLabel[25:50] # prend les lettres entre 25 et 50 ?

## Debug

    print("je suis un label")
    print(var)

## Lever une erreur


    if i - 2 > nbLabel:
    else:
        try:

        except:
            pass


## Opérateur logique et comparaison

comparaison

    ==	x == y	Égal	0 (faux)
    !=	x != y	Non égal	1 (vrai)
    >	x> y	Plus grand que	0
    <	x < y	Plus petit que	1
    >=	x >= y	Plus grand ou égal à	0
    <=	x <= y	Plus petit ou égal à	1
    is	x is y	est le même objet	0
    is not	x is not y	n'est pas le même objet	1

Opérateur logique


    ( )	de gauche à droite	parenthèses
    + -	de gauche à droite	singulier
    / %	de gauche à droite	multiplicatif
    + -	de gauche à droite	additif
    < <= > >=	de gauche à droite	relationnel
    == !=	de gauche à droite	égalité
    and	de gauche à droite	ET logique booléen
    or	de gauche à droite	OU logique booléen exclusif
    not		NON logique
    = += -= *= /= %=	de droite à gauche	affectation
