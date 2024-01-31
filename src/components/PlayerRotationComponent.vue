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
      joueurs: [
        {id:1, nom: 'Joueur'}
        // ... autres joueurs
      ],
    };
  },
  props: {
    nbrPlayers: Number,
  },

  methods: {
    changerJoueur(nouveauJoueur) {
      // Logique pour changer le joueur actif
      console.log('Changer de joueur vers', nouveauJoueur);
      // Mettez en œuvre la logique de changement de joueur ici
    },

    ajouterJoueur() {
      const nouvelJoueur = { id: this.joueurs.length + 1, nom: 'Joueur' };
      this.joueurs.push(nouvelJoueur);
      console.log(this.nbrPlayers);
    },
  },
};
</script>