## React Native ( react cross-platform )

Info :
-------------------
React Native permet de developper des application cross-platforms en javascript

Pré-requis
- Node
- Expo ou device


Initialisation :
-------------------

pré-requis:

- Installer node.js
- nécésite "expo-cli", demande de téléchargement lors de la création de l'appli ou cette commande :

    npm install -g expo-cli

- Instalation de l'appplication android "expo" pour avoir le rendu sur le telephone ( connecter au méme réseau wii-fii )

Créer son App :
-------------------

1. Avec npm ( fournis avec node.js ) :


    npm install create-react-native-app -g
    create-react-native-app TestReact ( pour une version de React Sans utiliser les composants telephone )
    cd TestReact
    npm start ( donne un QR code et lance le serveur node.js )

2. Avec expo ( recomandé )

    expo init MonProjet ( commande pour créer le projet )
    choisir "blank" a minimal app as clean as an empty canvas
    cd MonProjet
    nnpm start ( donne un QR code et lance le serveur node.js , resultat disponible sur l'app expo )



Gestion assets
-------------------

- icone
- Screen1, Screen2, Screen3
- Bannière


Pour inclure des images dans l'application, il faut faire un fichier _image.js, une constante objet qui possède toute les images. puis dans le code du composant, il faudra appeler { img.nameimage }

Architecture de l'application
-------------------
- Components : dossier des composants ( a refactoriser dès que possible
- Stores : Modèle et base de donnée
- utils : service annexe ( get, petite function )
- assets : image et icon
- nodes_module : librairie

Classes des composants
-------------------



Le style du composant
-------------------


    const styles = StyleSheet.create({
        main_container: {
            flex: 1,
            marginTop: 20,
            backgroundColor: 'white',
        },
        text_input: {
            marginTop: 70,
            marginBottom: 15,
            marginLeft: 20,
            marginRight: 20,
            height: 50,
            borderColor: '#000000',
            borderWidth: 1,
            paddingLeft: 5,
        },
        button: {
            backgroundColor: 'green',
            marginRight: 50,
        },
    })

Utiliser flexbox pour styliser les view et les arrangements..


Faire une requete
----------------------


     const url = 'xxxxx'
     return fetch(url)
         .then((response) => response.json())
         .catch((error) => console.error(error))



State et props
--------------------

This.state()
This.setstate()

Exporter l'app en APK
-------------------

[Docs Expo](https://docs.expo.io/distribution/building-standalone-apps/)

configure app.json


    {
   "expo": {
    "name": "Your App Name",
    "icon": "./path/to/your/app-icon.png",
    "version": "1.0.0",
    "slug": "your-app-slug",
    "ios": {
      "bundleIdentifier": "com.yourcompany.yourappname",
      "buildNumber": "1.0.0"
    },
    "android": {
      "package": "com.yourcompany.yourappname",
      "versionCode": 1
    }
   }
 }




    expo build:android -t apk

Récuperer la keystore ( indispensable pour les MAJ )



    expo fetch:android:keystore


puis publier sur play store ( avec bannière, icone, screen, description,...



[Lien OC](https://openclassrooms.com/fr/courses/4902061-developpez-une-application-mobile-react-native/4959626-preparez-votre-application-pour-les-stores-apple-et-google/)
[React Naviguation](https://reactnavigation.org/docs/getting-started/)
[Lien OpenclassRooms](https://openclassrooms.com/fr/courses/4902061-developpez-une-application-mobile-react-native/4959616-formalisez-votre-application-pour-utiliser-les-composants-du-device/)
