Python
===================
`Docs Python`_

.. _`Docs Python`: https://docs.python.org/fr/3/

Variable
===========
::

    a = 1

Condition
===========
::

    if os.path.exists(path):
            # Delete old app/static/img/diagram.svg
            os.remove(path) # specifying the path of the file for delete old diagram

Boucle
===========
::

    for nodes in rectangle:
        #node left
        turtle.goto(n,m)
        turtle.down()
        turtle.color('blue')
        turtle.circle(25) #50 good
        #turtle.circle(50, 180)  #Trace un demi-cercle de rayon 70px
        turtle.up()


Debug
===========

print("je suis un label")
print(var)
