<template>
  <main class="allGame">
    <Campo :player1="player1" :player2="player2" class="secoes"/>
    <AcoesVue class="secoes" :emJogo="emJogo" @ataque="ataqueJogador()" @especial="especial()" @desistir="desistir" @curar="curar"/>
    <historico :ataques="ataque" class="secoes" />
  </main>
</template>

<script >
import AcoesVue from './components/Acoes.vue';
import Campo from './components/Campo.vue';
import Historico from './components/Historico.vue';

export default {
  components: {
    Campo,
    AcoesVue,
    Historico
  },
  data() {
    return {
      emJogo: false,
      ataque: [],
      player1: {
        nome: 'Jogador',
        vida: 100,
      },
      player2: {
        nome: 'Monstro',
        vida: 100,
      },
      random: 0,
    }
  },
  methods: {
    ataqueJogador() {
      this.random = this.gerarNumEntre(8);
      this.player2.vida -= this.random
      this.ataque.push( {jogador: 'Jogador', pontos: this.random} )

      this.random = this.gerarNumEntre(12);
      this.player1.vida -= this.random
      this.ataque.push( {jogador: 'Monstro', pontos: this.random} )
      this.verificaGanhador()
    },
    especial() {
      this.random = this.gerarNumEntre(12);
      this.player2.vida -= this.random
      this.ataque.push( {jogador: 'Jogador', pontos: this.random} )

      this.random = this.gerarNumEntre(8);
      this.player1.vida -= this.random
      this.ataque.push( {jogador: 'Monstro', pontos: this.random} )

      this.verificaGanhador()
    },
    curar() {
      this.random = this.gerarNumEntre(12);
      this.player1.vida += this.random
      this.ataque.push( {jogador: 'Jogador', pontos: this.random} )

      this.random = this.gerarNumEntre(8);
      this.player1.vida -= this.random
      this.ataque.push( {jogador: 'Monstro', pontos: this.random} )

    },
    desistir() {
      this.player1.vida = 100
      this.player2.vida = 100
      this.ataque = []
      this.emJogo = !this.emJogo;
    },
    verificaGanhador() {
      if(this.player1.vida <= 0) {
        if(this.player1.vida < this.player2.vida) {
        alert("Não foi dessa vez, por favor tente novamente")
        this.desistir()
        return
       }
      }

      if(this.player2.vida <= 0) {
        alert("Parabens, você ganhou!!!")
        this.desistir()
        return
      }
    },
    gerarNumEntre(max) {
      return (Math.floor(Math.random() * (max - 4 + 1)) + 4);
    }
  }
  }
</script>

<style scoped>
.allGame {
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 25px;
}

.secoes {
  box-shadow: 0 0 5px 3px rgba(0, 0, 0, 0.2);
  border-radius: 10px;
}
</style>
