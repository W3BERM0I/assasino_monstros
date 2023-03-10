<template>
  <div class="jogadorFull">
    <p class="nome">{{jogador.nome}}</p>
    <div class="progressBarFull">
      <span class="progressBar" :style="[{width: jogador.vida + '%'}, {background: jogador.vida < 30 ? '#ff00007e' : 'green'}]"></span>
    </div>
    <p class="vida">{{jogador.vida}}%</p>
  </div>
</template>

<script>
export default {
  props: {
    jogador: {
      required: true,
      type: Object,
    },
  }
}
</script>

<style scoped>
.jogadorFull {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.nome {
  font-size: 2rem;
  margin: 20px;
}

.vida {
  margin-top: 0;
  margin-bottom: 10px;
}

.progressBarFull {
  border: 1px solid black;
  min-width: 35vw;
  height: 25px;
  margin: 0;
  display: flex;
}

.progressBar {
  height: 100%;
}
</style>