<template>
  <main v-if="joueurActif" :style="{ backgroundColor: joueurActif.color }">
   {{ joueurActif.id }}
   <!-- <button @click="changerJoueur">Changer de joueur</button> -->

  </main>
</template>
<script>
export default {
  data() {
    return {
      nombreJoueurs: 0,
      playerTurn: 0,
      couleurs: ["#FFADAD", "#FFD6A5", "#FDFFB6", "#CAFFBF", "#9BF6FF", "#A0C4FF", "#BDB2FF", "#FFC6FF"],
      couleurActuelle: "#FFADAD", // Couleur par défaut

      joueurs: [],
      joueurActifIndex: 0 // Index du joueur actif dans le tableau joueurs

    };
  },
  props: {
    nbrPlayers: {type: Number},
  },
  computed: {
    joueurActif() {
      return this.joueurs[this.joueurActifIndex];
    }
  },

  methods: {
    ajouterJoueur(nombreJoueurs) {
      console.log(this.nbrPlayers);
      this.joueurs = []
      for (let i = 0; i < nombreJoueurs; i++) {
        this.joueurs.push({
          id: i+1,
          nom: 'Joueur',  // Propriétés de chaque joueur, à personnaliser selon vos besoins
          color: this.couleurs[i]
        });
      }
      console.log(this.joueurs);
    },
    changerJoueur() {
      // Changer de joueur en incrémentant l'index du joueur actif
      this.joueurActifIndex = (this.joueurActifIndex + 1) % this.joueurs.length;
      this.sendActualPlayerToParent()
    },
    sendArrayToParent() {
      this.$emit('tableau-joueurs', this.joueurs);
    },
    sendActualPlayerToParent(){
      this.$emit('joueur-actif', this.joueurActif.id);
    }
  },
  watch: {
    nbrPlayers: function(nouvellesInfos) {
      this.ajouterJoueur(this.nbrPlayers)
      this.sendArrayToParent()
      this.sendActualPlayerToParent()
    }
  },
};
</script>
<style scoped>
main{
  padding: 0;
  margin: 0;
  width: 100%;
  height: 100%;
  border-radius: 10px;
  padding: 1em 2em;
  color: black;
}
</style>