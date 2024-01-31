<template>
  <main>
    <ul>
      <li v-for="joueur in joueurs" :key="joueur.id">{{ joueur.nom }} {{ joueur.id }}</li>
    </ul>
    <button @click="ajouterJoueur">test</button>
  </main>
</template>
<script>
export default {
  data() {
    return {
      nombreJoueurs: 0,

      joueurs: [],
    };
  },
  props: {
    nbrPlayers: {type: Number},
  },
  methods: {
    changerJoueur(nouveauJoueur) {
      // Logique pour changer le joueur actif
      console.log('Changer de joueur vers', nouveauJoueur);
      // Mettez en œuvre la logique de changement de joueur ici
    },

    ajouterJoueur(nombreJoueurs) {
      console.log(this.nbrPlayers);
      this.joueurs = []
      for (let i = 0; i < nombreJoueurs; i++) {
        this.joueurs.push({
          id: i+1,
          nom: 'Joueur',  // Propriétés de chaque joueur, à personnaliser selon vos besoins
          // ... d'autres propriétés
        });
      }
      console.log(this.joueurs);
    },
  },
  watch: {
    nbrPlayers: function(nouvellesInfos) {
      this.ajouterJoueur(this.nbrPlayers)
    }
  },
};
</script>