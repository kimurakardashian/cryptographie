<template>
  <div>
    <input type="text" name="" v-model="message">
    <button type="button" name="button" @click="encrypt">asdasd</button>
    <button type="button" name="button2" @click="decrypt">amor mio</button>
    <h2>{{displayMessage}}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "",
      encryptedMessage: "",
      numbers: true,
      polyArray: [
        ["0", "1", "2", "3", "4", "5"],
        ["1", "A", "B", "C", "D", "E"],
        ["2", "F", "G", "H", "I", "K"],
        ["3", "L", "M", "N", "O", "P"],
        ["4", "Q", "R", "S", "T", "U"],
        ["5", "V", "W", "X", "Y", "Z"]
      ],
      displayMessage: ""
    }
  },
  methods: {
    encrypt: function () {
      this.encryptedMessage = this.message;
      var numbers = this.numbers;
      var array = this.polyArray;
      var arrayLength = array.length;
      var messageLength = this.encryptedMessage.length;
      var uppercasedMessage = this.encryptedMessage.toUpperCase();
      this.encryptedMessage = "";
      var x, y = 0;
      for(var i=0; i<messageLength; i++) {
        var char = uppercasedMessage.substr(i,1);
        if(char === " ") {
          this.encryptedMessage += " ";
          continue;
        }
        if(char == "Ñ") {
          char = "N";
        }
        if(char == "J") {
          char = "I";
        }
        for(var j=0; j<arrayLength; j++) {
          for(var k=0; k<arrayLength; k++) {
            if(char == array[j][k]) {
              //console.log("CHAR: " + char + "\nARRAY: " + array[j][k]);
              array[j].indexOf(char);
              x = array[j][0];
              //console.log( j + " " + k);
              y = array[0][k];
              if(!numbers) {
                if(array[j][0] == "1") {
                  x = "A";
                }
                if(array[j][0] == "2") {
                  x = "B";
                }
                if(array[j][0] == "3") {
                  x = "C";
                }
                if(array[j][0] == "4") {
                  x = "D";
                }
                if(array[j][0] == "5") {
                  x = "E";
                }
                if(array[0][k] == "1") {
                  y = "A";
                }
                if(array[0][k] == "2") {
                  y = "B";
                }
                if(array[0][k] == "3") {
                  y = "C";
                }
                if(array[0][k] == "4") {
                  y = "D";
                }
                if(array[0][k] == "5") {
                  y = "E";
                }
              }
              this.encryptedMessage += x + y;
            }
          }
        }
      }
      this.displayMessage = this.encryptedMessage;
      this.message = "";
    },
    decrypt: function () {
      var x = "";
      var y = "";
      var encryptedMessage = this.encryptedMessage;
      var messageLength = encryptedMessage.length;
      var isOdd = "";
      var sp = false;
      var count = 0;
      this.encryptedMessage = "";
      for(var i=0; i<messageLength; i++) {
        //isOdd = i%2;
        var char = encryptedMessage.substr(i,1);
        if(char == " ") {
          this.encryptedMessage += " ";
          continue;
        }
        count ++;
        if(count == 2) {
          if(char == "A" || char == "1") {
            y = 1;
          }
          if(char == "B" || char == "2") {
            y = 2;
          }
          if(char == "C" || char == "3") {
            y = 3;
          }
          if(char == "D" || char == "4") {
            y = 4;
          }
          if(char == "E" || char == "5") {
            y = 5;
          }
        }
        else {
          if(char == "A" || char == "1") {
            x = 1;
          }
          if(char == "B" || char == "2") {
            x = 2;
          }
          if(char == "C" || char == "3") {
            x = 3;
          }
          if(char == "D" || char == "4") {
            x = 4;
          }
          if(char == "E" || char == "5") {
            x = 5;
          }
        }
          //this.message += this.polyArray[x][y];
          if(count == 2) {
            this.encryptedMessage += this.polyArray[x][y];
            count = 0;
          }
      }
      this.displayMessage = this.encryptedMessage;
    }
  }
}
</script>

<style>
</style>
