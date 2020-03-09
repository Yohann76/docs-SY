ReactNative ( Base de React fait par Facebook ) 
===================

Info : 
-------------------

Base de code pour IOS et Android ( a quelques modification préte ) 
React Native permet de developper des application cross-platforms en javascript 

Nous avons obligatoirement besoin de Node.js / Expo et un editeur de texte 


Initialisation : 
-------------------

pré-requis:

- Installer node.js
- nécésite "expo-cli", demande de téléchargement lors de la création de l'appli ou cette commande :
::
    npm install -g expo-cli

- Instalation de l'appplication android "expo" pour avoir le rendu sur le telephone ( connecter au méme réseau wii-fii ) 

Créer son App : 
-------------------

1. Avec npm ( fournis avec node.js ) : 
::

    npm install create-react-native-app -g
    create-react-native-app TestReact ( pour une version de React Sans utiliser les composants telephone ) 
    cd TestReact
    npm start ( donne un QR code ) 


2. Avec expo ( recomander ) 
::
    expo init MonProjet ( commande ) 
    choisir "blank" a minimal app as clean as an empty canvas
    cd MonProjet
    npm start ( donne un QR code  et envoie l'app sur le server Node.js)  


adresse : 
http://localhost:19002/ ( QR Code à cette adresse ) 
Dans cette adresse nous pouvons voir le QR code, les tests , méme chose que dans le terminal 

Scanner le QR Code avec l'application Expo ( sur android )  

Une seul commande a taper pour passer d'une CRNA ( create-React-Native-App donc sans composant telephone  ) 
A une app React Native avec du code natif ( qui utilise les composant telephone -> lampe torche ) 
::
    Commande ? 


Architecture 
-------------------
Créer un dossier "Components" A la racine pour ranger les composants
Components/Search.js

Créer un dossier "Helpers" pour avoir de la data par exemple 
Helpers/filmsData.js

Ne pas oublier d'importer les composants :
::

    import React from 'react'
    import { StyleSheet, View, TextInput, Button , Text,FlatList } from 'react-native'

Style 
-------------------
::

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

ET 
::

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
::

    export default Search

Rendre un composant 
::

  render() {
    return (
        <Search/>
    )
  }

Suite..







