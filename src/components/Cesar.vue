<template>
  <div>
    <input type="text" v-model="message" placeholder="Texto a encriptar">
    <button type="button" name="button" @click="encrypt">ENCRIPTAR</button>
    <button type="button" name="button2" @click="decrypt">DESENCRIPTAR</button>
    <h2>{{displayMessage}}</h2>
  </div>
</template>

<script>
export default {
  data () {
    return {
      message: "",
      alphabet: ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"],
      //cesar: ["D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "Ñ", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "A", "B", "C"],
      encryptedMessage: "",
      displayMessage: ""
    }
  },
  methods: {
    encrypt: function () {
      this.encryptedMessage = this.message;
      this.message = "";
      var alphabet = this.alphabet;
      var messageLength = this.encryptedMessage.length;
      var uppercasedMessage = this.encryptedMessage.toUpperCase();
      this.encryptedMessage = "";
      for(var i=0; i<messageLength; i++) {
        var char = uppercasedMessage.substr(i,1);
        if(char == "Ñ") {
          char = "N";
        }
        var position = alphabet.indexOf(char);
        if(char == " ") {
          this.encryptedMessage += " ";
        }
        else if(char == "X") {
          this.encryptedMessage += "A";
        }
        else if(char == "Y") {
          this.encryptedMessage += "B";
        }
        else if(char == "Z") {
          this.encryptedMessage += "C";
        }
        else {
          this.encryptedMessage += alphabet[position+3];
        }
      }
      this.displayMessage = this.encryptedMessage;
    },
    decrypt: function () {
      var alphabet = this.alphabet;
      var messageLength = this.encryptedMessage.length;
      var uppercasedMessage = this.encryptedMessage.toUpperCase();
      this.encryptedMessage = "";
      for(var i=0; i<messageLength; i++) {
        var char = uppercasedMessage.substr(i,1);
        if(char == "Ñ") {
          char = "N";
        }
        var position = alphabet.indexOf(char);
        if(char == " ") {
          this.encryptedMessage += " ";
        }
        else if(char == "A") {
          this.encryptedMessage += "X";
        }
        else if(char == "B") {
          this.encryptedMessage += "Y";
        }
        else if(char == "C") {
          this.encryptedMessage += "Z";
        }
        else {
          this.encryptedMessage += alphabet[position-3];
        }
      }
      this.displayMessage = this.encryptedMessage;
    }
  },
  mounted() {

  }
}
</script>

<style>
</style>
