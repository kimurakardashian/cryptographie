<template>
  <div id="app">
    <div class="menu" v-if="menu">
      <div class="btn-container">
        <a class="btn" href="#" @click.prevent="enter('cesar')">Criptosistema Cesar</a>
        <a class="btn" href="#" @click.prevent="enter('poly')">Criptosistema Polybius</a>
      </div>
    </div>
    <a href="#" @click.prevent="ret" v-if="!menu">REGRESAR</a>
    <component v-if="!menu" v-bind:is="comp"></component>
  </div>
</template>

<script>
import cesar from './components/Cesar.vue';
import poly from './components/Polybius.vue';

export default {
  components: {
    cesar:cesar,
    poly:poly
  },
  name: 'app',
  data () {
    return {
      menu: true,
      comp: ''
    }
  },
  methods: {
    enter: function (payload) {
      this.comp = payload;
      this.menu = false;
    },
    ret: function () {
      this.comp = '';
      this.menu = true;
    }
  }
}
</script>

<style scoped>
*{font-family:"Press Start 2P";}
.menu{width:100vw;height:100vh;display:flex;justify-content:center;align-items:center;background-color:black;}
.btn-container{width:60vw;height:40vh;display:flex;flex-direction:column;justify-content:space-around;;align-items:center;}
.btn{color:white;font-size:2em;text-decoration:none;}

</style>
