## React Navigate component


importer le systeme de routage:

    import * as React from 'react';
    import { NavigationContainer, useRoute } from '@react-navigation/native';
    import { createStackNavigator } from '@react-navigation/stack';
    import Game from "./components/xxxxxx";
    import MultiGame from "./components/xxxxxx";
    import Img from './assets/images/_image';
    import Buttons from './components/Layout/Buttons';
    import 'localstorage-polyfill';

dans app.js, définir les routes

    /* Function for routing */
    function ConfigurationScreen({ navigation }) {
      return (
        <Configuration navigation={navigation}/>
      );
    }

    /* Function for routing */
    function GameScreen({ navigation }) {
      return ( <Game navigation={navigation}/> );
    }

    /* Function for routing */
    function MultiGameScreen({ navigation }) {
      return ( <MultiGame navigation={navigation}/> );
    }

    /* Function for routing */
    function EndGameScreen({ navigation }) {
      const route = useRoute();
      const { result } = route.params;
      return ( <EndGame navigation={navigation} result={result}/> );
    }

    const Stack = createStackNavigator();

    /* routing system */
    function App() {
      return (
        <NavigationContainer>
          <Stack.Navigator headerMode="none" initialRouteName="Home">
            <Stack.Screen name="Home" component={HomeScreen} />
            <Stack.Screen name="Configuration" component={ConfigurationScreen} />
            <Stack.Screen name="Game" component={GameScreen} />
            <Stack.Screen name="MultiGame" component={MultiGameScreen} />
            <Stack.Screen name="EndGame" component={EndGameScreen} />
          </Stack.Navigator>
        </NavigationContainer>
      );


Naviguer d'une vue a l'autre dans les composants :

    onPress={() => navigation.push(NameRenderView)}
