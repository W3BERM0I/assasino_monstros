<template>
  <div v-show="!emJogo" class="controle">
    <button @click="emJogo = !emJogo" type="button" class="botoes iniciar">INICIAR NOVO JOGO</button>
  </div>
  <div v-show="emJogo" class="controle">
    <button @click="ataque()" type="button" class="botoes ataque">ATAQUE</button>
    <button @click.prevent="especial" class="botoes especial">ATAQUE ESPECIAL</button>
    <button @click.prevent="curar" class="botoes curar">CURAR</button>
    <button @click.prevent="desistir" class="botoes desistir">DESISTIR</button>
  </div>
</template>

<script>
export default {
  props: {
    emJogo: {
      required: true,
      type: String,
    },
  },
  data() {
    return {
    }
  },
  methods: {
    ataque() {
      this.$emit("ataque")
    },
    especial() {
      this.$emit("especial")
    },
    curar() {
      this.$emit("curar")
    },
    desistir() {
      this.$emit("desistir")
    },
  }
}
</script>

<style>
.controle {
  width: 95vw;
  height: 12vh;
  display: flex;
  align-items: center;
  justify-content: center;
  
  box-shadow: 0 0 5px 3px rgba(0, 0, 0, 0.2);
  border-radius: 10px;
}

.botoes {
  border: none;
  padding: 9px;
  border-radius: 10px;
  margin-right: 15px;
}

.iniciar {
  background-color: rgb(111, 0, 255);
  color: white;
}

.ataque {
  background-color: rgb(224, 5, 5);
  color: white;
}

.especial {
  background-color: orange;
}

.curar {
  background-color: green;
  color: white;
}

.desistir {
  background-color: rgb(180, 177, 177);
}

</style>