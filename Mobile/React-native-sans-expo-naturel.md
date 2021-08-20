.. index::
   single: ReactNative

Expo
===================

Info :
-------------------
Sans expo, il n'y a plus d'application pour tester, il faut alors se débrouiller autrement.


Ejection d'une application expo  :
-------------------

[Cours OC](https://openclassrooms.com/fr/courses/4902061-developpez-une-application-mobile-react-native/4959616-formalisez-votre-application-pour-utiliser-les-composants-du-device)


Configuration d'environnement sans expo :
-------------------------------------------


Sans expo, il faut lancer la commande suivante pour tester l'application, avec un téléphone branché en USB, ou un simulateur android studio :

    react-native run-android

Notez qu'il faudra installer java, un SDK, ainsi que la platform-tools.

Configurer les variable d'environnement ( avec les bons fichiers ) :

- JAVA_HOME : C:\Program Files\Java\jdk-15.0.2
- ANDROID_SDK_ROOT : C:\Users\sacha\AppData\Local\Android\Sdk
- add path : C:\Program Files\Android\platform-tools
- add path : C:\Users\sacha\AppData\Local\Android\Sdk
