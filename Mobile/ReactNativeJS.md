## ReactNative ( Base de React fait par Facebook )

Info :

React native permet le développement d'application avec l'écosysteme react.

pré-requis:

- Installer node.js
- nécésite "expo-cli", demande de téléchargement lors de la création de l'appli ou cette commande :


    npm install -g expo-cli

- Instalation de l'appplication android "expo" pour avoir le rendu sur le telephone ( connecter au méme réseau wii-fii )

Créer son App :


1. Avec npm : Le Natif  :


    npm install create-react-native-app -g
    create-react-native-app TestReact ( pour une version de React Sans utiliser les composants telephone )
    cd TestReact
    npm start ( donne un QR code et lance le serveur node.js )


2. Avec expo : la CRNA ( recommandé au début )

    expo init MonProjet ( commande pour créer le projet )
    choisir "blank" a minimal app as clean as an empty canvas
    cd MonProjet
    nnpm start ( donne un QR code et lance le serveur node.js , resultat disponible sur l'app expo )

Architecture


Créer un dossier "Components" A la racine pour ranger les composants
Components/Search.js

Créer un dossier "Helpers" pour avoir de la data par exemple
Helpers/filmsData.js

Ne pas oublier d'importer les composants :


    import React from 'react'
    import { StyleSheet, View, TextInput, Button , Text,FlatList } from 'react-native'

Style



    render() {
        return (
            <View style={styles.main_container}>
                <TextInput style={styles.text_input} placeholder='Titre du film'/>
                <Button style={styles.button} title='Rechercher' onPress={() => {}}/>
                <FlatList
                    data={films} // import FilmItem
                    keyExtractor={(item) => item.id.toString()}
                    renderItem={({item}) =>
                        <FilmItem
                            film={item}
                        />}
                />
            </View>
        )
    }

Le style ( Aprés la class )



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

Ne pas oublié d'exporter un composants en fin de fichier

    export default Search

Rendre un composant


    render() {
      return (
          <Search/>
      )
    }

Utilisé une API
API/Name_apiAPI.js ( exemple ) :


    // API/TMDBApi.js

    const API_TOKEN = "7f0c884269f18433248fb9bf049b54f2";

    export function getFilmsFromApiWithSearchedText (text) {
        const url = 'https://api.themoviedb.org/3/search/movie?api_key=' + API_TOKEN + '&language=fr&query=' + text
        return fetch(url)
            .then((response) => response.json())
            .catch((error) => console.error(error))
    }

    export function getImageFromApi (name) {
        return 'https://image.tmdb.org/t/p/w300' + name
    }



Gestion de Librairies

Pour installer une librairie il faut Stopper le serveur Node.js avec ctrl + C

A la racine du projet dans le terminal :


    $ npm install --save react-navigation

[React Naviguation](https://reactnavigation.org/docs/getting-started/)  Pour avoir une bonne naviguation


Le --save permet d'enregistrer la librairie dans le package.json , ainsi sur un autre ordinateur, on peux installer les dépendances avec :


    $ npm install

Relancer le serveur avec :


    $ npm start


Préparer pour les stores



[Lien OC](https://openclassrooms.com/fr/courses/4902061-developpez-une-application-mobile-react-native/4959626-preparez-votre-application-pour-les-stores-apple-et-google/)
[React Naviguation](https://reactnavigation.org/docs/getting-started/)
[Lien OpenclassRooms](https://openclassrooms.com/fr/courses/4902061-developpez-une-application-mobile-react-native/4959616-formalisez-votre-application-pour-utiliser-les-composants-du-device/)
