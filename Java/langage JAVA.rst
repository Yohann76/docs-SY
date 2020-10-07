Le langage JAVA
===================
`Java DOC <https://docs.oracle.com/en/java/>`_

`Cours Java OC  <https://openclassrooms.com/fr/courses/26832-apprenez-a-programmer-en-java>`_


Installation 
-------------------
`Télécharger l'environnement JAVA  <http://www.oracle.com/technetwork/java/javase/downloads/index.html>`_
`Télécharger Eclipse IDE  <https://www.eclipse.org/>`_

Pour developper avec java, il faut le JDK ( Java Dev Kit) + un IDE ( Eclipse, VS/CODE )


Utilité de JAVA 
-------------------

Syntaxe du langage 
-------------------

variables
::
    int temperatureSoleil;
    temperatureSoleil = 15600000; //La température est exprimée en kelvins
    float nombre;
    nombre = 2.0f;
    String text = "ABCDE";

Un hello World made in JAVA 
::

    package hello;

    /** Ceci est une implémentation du message traditionnel "Hello world!"
    * @author L'équipe Education d'OpenClassrooms
    */
    public class HelloWorld {

    /** Le programme commence ici */
        public static void main(String[] args) {
            System.out.println("Hello World!");
        }

    }

Executer un .java avec le terminal : 
    $ javac.exe hello∖HelloWorld.java
