<template>

    <web-view :source="{uri:'https://invoicemanager.ro/'}" />  

</template>

<script>
import firebase from 'firebase';
import { WebView } from "react-native-webview";

 var firebaseConfig = {
    apiKey: "AIzaSyD92XYKrF6SbhcLoUTpjPaBUx9HxyPw",
    authDomain: "invoicemanager-a542d.firebaseapp.com",
    databaseURL: "https://invoicemanager-a542d.firebaseio.com",
    projectId: "invoicemanager-a542d",
    storageBucket: "invoicemanager-a542d.appspot.com",
    messagingSenderId: "758688562180",
    appId: "1:758688562180:android:19e6c4a66b124727"
  };

//const app = firebase.initializeApp(firebaseConfig);
  const provider = new firebase.auth.GoogleAuthProvider();

var FirebaseTokenGenerator = require("firebase-token-generator");
var tokenGenerator = new FirebaseTokenGenerator("<YOUR_FIREBASE_SECRET>");
var token = tokenGenerator.createToken({uid: "1", some: "arbitrary", data: "here"});


export default {
  data: function() {
    return{
      token
    }
  },
  name: "myComponent",
  components: {
    "web-view": WebView
  },
  methods: {
    signInWithGoogle() {
      firebase.auth().signInWithRedirect(provider);
    }
  }
}

</script>