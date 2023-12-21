<script>
import GameComponent from '../components/GameComponent.vue';
import GameSettings from '../components/GameSettings.vue';

export default {
  data() {
  	return {
        afficherPopup: false,
        donneesFormulaire: {},
        nbrPlayers: Number,
      	}
	},
    components: {
        GameComponent,
        GameSettings,
    },

    methods: {
    traiterFormulaire(donneesFormulaire) {
        // Stockez les données dans la propriété data
        this.donneesFormulaire = donneesFormulaire;
      this.nbrPlayers = donneesFormulaire.nbrPlayers;
      // Traitez les données du formulaire ici
      console.log('Données du formulaire reçues:',  this.nbrPlayers);
    },
    },
}

</script>
<template>

    <main>
        <GameComponent :nbrPlayers="nbrPlayers"/>
        <GameSettings :afficherPopup="afficherPopup" @fermerPopup="afficherPopup = true" @formulaireValide="traiterFormulaire" />
    </main>
</template>
<style scoped>
main {
    width: 100vw;
    height: 100vw;
}
</style>