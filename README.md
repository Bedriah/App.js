# App.js
//This is my assignment regarding how to implement the Word Analyzer where the users put words in the text input and users click button "Analyze", then the result/output will calculate how many vowels, consonants and characters of the words.



import { StatusBar } from 'expo-status-bar';
import React, {Component}  from 'react';
import { StyleSheet, Text, TextInput, View, Button } from 'react-native';

export default class App extends Component {
//Declare the state for variable wordInput, newText, characters, vowels and consonants.
state = {
  wordInput: ' ',       //here is the variables that I declared when users enter the text inside the TextInput
  newText: '',          // declares the new text as string.
  characters: 0,        // declares the characters as a number.
  vowels: 0,            // declares the vowels as a number.
  consonants: 0,        // declares the consonants as a number.
};

onPress = () => {       //onPress for button "Analyze" to workout and display the result.
  this.setState({
      newText: this.state.wordInput,  //I will call the newText in the "Word" part where it will show the result after the user enter the input and click the "Analyze" button.
      characters: this.state.wordInput.length,    //calling the characters where it will read and calculate the number of words.
      vowels: this.state.wordInput.match(/[AaEeIiOoUu]/g).length,   //calling the vowels that match AEIOU words and count how many is the characters.
      consonants: this.state.wordInput.match(/[BbCcDdFfGgHhJjKkLlMmNnPpQqRrSsTtVvWwXxYyZz]/g).length, //calling the consonants that match BCDFGHJKLMNPQRSTVWXYZ words and count how many is the characters
    });
  };
  
  render() {
  return (
  <View style={styles.container}>
    <Text style={styles.title}> A Word Analyzer </Text>                                             // Just title at the top
    <Text style={styles.all}>{'\n'}Word</Text> 
    <TextInput style={styles.input} onChangeText={(wordInput) => this.setState({wordInput})}/>      // Text input where users will type their words in it.
    <Text style={styles.all}>Word                          : {this.state.newText}</Text>            // The output that display the words that user enter.
    <Text style={styles.all}>No. Of Consonants  : {this.state.consonants}</Text>                    // The output that count the consonants that users's enter.
    <Text style={styles.all}>No. Of Vowels          : {this.state.vowels}</Text>                    // The output that count the vowels for the words that user's enter.
    <Text style={styles.all}>No. Of Characters    : {this.state.characters}{'\n'}{'\n'}{'\n'}{'\n'}</Text>    // the output that count all characters of the words.
    <Button color="grey" onPress = {this.onPress} title ='Analyze'/>    // the button that once users enter will show the result
  </View>
  );
}
}

  
  //this is all the styles that needed for the container, title, all(for all text like "words, consonants, vowels, and characters") and input(for textInput).
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
  title:{
    fontWeight: 'bold',
    fontSize: 25,
    top: 50,
    textAlign: 'center',
  },
  all: {
    fontSize: 20,
    left: 30,
    top: 60
  },
  
  input: {
    fontWeight: 'bold',
    fontSize: 15,
    backgroundColor: 'lightgrey',
    width: 100,
    left: 210,
    top: 35,
  }
});

