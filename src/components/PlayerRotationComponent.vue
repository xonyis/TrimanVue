<template>
  <main :style="{ backgroundColor: couleurActuelle }">
    <ul>
      <li v-for="joueur in joueurs" :key="joueur.id">{{ joueur.nom }} {{ joueur.id }}</li>
    </ul>
    <button @click="changerCouleur">test</button>
  </main>
</template>
<script>
export default {
  data() {
    return {
      nombreJoueurs: 0,
      couleurs: ["#FFADAD", "#FFD6A5", "#FDFFB6", "#CAFFBF", "#9BF6FF", "#A0C4FF", "#BDB2FF", "#FFC6FF"],
      couleurActuelle: "#FFADAD", // Couleur par défaut

      joueurs: [],
      
    };
  },
  props: {
    nbrPlayers: {type: Number},
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

    changerCouleur() {
      // Choisir une couleur aléatoire dans le tableau
      const nouvelleCouleur = this.couleurs[Math.floor(Math.random() * this.couleurs.length)];
      // Mettre à jour la couleur actuelle
      this.couleurActuelle = nouvelleCouleur;
    }
  },
  watch: {
    nbrPlayers: function(nouvellesInfos) {
      this.ajouterJoueur(this.nbrPlayers)
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
}
</style>