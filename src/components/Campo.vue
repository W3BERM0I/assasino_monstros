<template>
  <div class="campo">
    <Jogador :jogador="player1"/>
    <Jogador :jogador="player2"/>
  </div>
</template>

<script>
import Jogador from './Jogador.vue';
export default {
  components: {
    Jogador,
  },
  props: {
    player1: {
      required: true,
      type: Object,
    },
    player2: {
      required: true,
      type: Object,
    },
  },
  data() {
    return {
    }
  } 
  }
</script>

<style scoped>
.campo {
  width: 95vw;
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
}
</style>