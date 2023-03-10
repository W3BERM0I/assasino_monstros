<template>
  <div class="historico">
    <p v-for="(at, index) in ataques" :key="index" class="registro" :class="at.jogador">{{ at.jogador.toUpperCase()  }} ATINGIU {{ at.jogador == 'Monstro' ? 'JOGADOR' : 'MONSTRO' }} COM {{ at.pontos }} PONTOS.</p>
  </div>
</template>

<script>
export default {
  props: {
    ataques: {
      required: true,
      type: Array,
    },
  }
}
</script>

<style>
.historico {
  width: 95vw;
  min-height: 10vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-items: center;
  padding: 30px 0;
}

.registro {
  width: 98%;
  height: 25px;
  color: white;
  text-align: center;
  padding-top: 5px;
  margin: 3px;
}

.Jogador {
  background: #0000ff62;
}

.Monstro {
  background: #ff00007e;
}
</style>