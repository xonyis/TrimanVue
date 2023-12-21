<script>
export default {
  data() {
    return {
      nombreJoueurs: null, // Remplacez cela par le nombre réel de joueurs
      joueurActuel: 0,
      tableauJoueurs: []
    };
  },
  props: {
    nbrPlayers: Number,
    },
  
  methods: {
    initialiserTableauJoueurs() {
        this.nombreJoueurs = this.nbrPlayers 
      this.tableauJoueurs = Array.from({ length: this.nbrPlayers }, (_, index) => `Joueur ${index + 1}`);
    },
    passerAuJoueurSuivant() {
        this.initialiserTableauJoueurs(); // faut l'initialiser dans les methode pas avant 

      this.joueurActuel = (this.joueurActuel + 1) % this.nombreJoueurs;
    }
  }
};
</script>
<template>
    <main>
        <div class="header"><h2>C'est au tour de :</h2> <p>{{ nbrPlayers}}</p></div>
        <span>Joueur {{ joueurActuel + 1 }}</span>
        <button @click="passerAuJoueurSuivant">Passer au Joueur Suivant</button>
    </main>
</template>
<style scoped>
main {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.header {
    display: flex;
    justify-content: space-between;
    width: 100%;
}

.header p {
    font-size: 1.5em;
}

span {
    font-size: 2em;
}
</style>