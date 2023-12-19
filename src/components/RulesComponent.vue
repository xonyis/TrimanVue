<script>
export default {
  data() {
    return {
      afficherPopUp: false,
    };
  },
  methods: {
    ouvrirPopUp() {
      this.afficherPopUp = true;
    },
    fermerPopUp() {
      this.afficherPopUp = false;
    },
  },
};
</script>
<template>
    <div v-if="afficherPopUp" class="popup" @click.self="fermerPopUp">
    <div class="contenu-popup">
        <h2>Règles :</h2>
      <!-- Contenu de votre pop-up -->
      <div class="parent">
        <div class="div1">resulat</div>
        <div class="div2">règles</div>
        <div class="div3">gorgées</div>
        <div class="div4">3</div>
        <div class="div5">Le triman bois</div>
        <div class="div6">1</div>
        <div class="div7">9</div>
        <div class="div8">La personne à ta gauche bois</div>
        <div class="div9">1</div>
        <div class="div10">10</div>
        <div class="div11">Tu bois</div>
        <div class="div12">1</div>
        <div class="div13">11</div>
        <div class="div14">La personne à ta droite bois</div>
        <div class="div15">1</div>
        <div class="div16">double</div>
        <div class="div17">Tu donne le nbr du double de gorgés</div>
        <div class="div18">1 à 6</div>
    </div>
      <button @click="fermerPopUp">Fermer</button>
    </div>
  </div>
</template>
<style scoped>
.parent {
display: grid;
grid-template-columns: 0.5fr 2fr 0.5fr;
grid-template-rows: repeat(6, 1fr);
grid-column-gap: 0px;
grid-row-gap: 0px;
width: 100%;
border: 1px solid;
}

.parent > div {
    border-bottom: 1px solid black;
    
    text-align: center;
}
.div1,.div2,.div3{
    text-align: center;
}



.div1 { grid-area: 1 / 1 / 2 / 2; }
.div2 { grid-area: 1 / 2 / 2 / 3; }
.div3 { grid-area: 1 / 3 / 2 / 4; }
.div4 { grid-area: 2 / 1 / 3 / 2; }
.div5 { grid-area: 2 / 2 / 3 / 3; }
.div6 { grid-area: 2 / 3 / 3 / 4; }
.div7 { grid-area: 3 / 1 / 4 / 2; }
.div8 { grid-area: 3 / 2 / 4 / 3; }
.div9 { grid-area: 3 / 3 / 4 / 4; }
.div10 { grid-area: 4 / 1 / 5 / 2; }
.div11 { grid-area: 4 / 2 / 5 / 3; }
.div12 { grid-area: 4 / 3 / 5 / 4; }
.div13 { grid-area: 5 / 1 / 6 / 2; }
.div14 { grid-area: 5 / 2 / 6 / 3; }
.div15 { grid-area: 5 / 3 / 6 / 4; }
.div16 { grid-area: 6 / 1 / 7 / 2; }
.div17 { grid-area: 6 / 2 / 7 / 3; }
.div18 { grid-area: 6 / 3 / 7 / 4; }
.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5); /* Fond semi-transparent pour l'effet d'obscurcissement */
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: var(--font);

}

.contenu-popup {
  background: white;
  color: var(--black);
  padding:1em 2em;
  height: 70%;
  width: 70%;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}

button {
    background: var(--red);
    border: none;
    width: max-content;
    margin: auto;
    padding:.7em 1em;
    border-radius: 8px;
    color: white;
    font-family: var(--font);
}

h2 {
    text-align: center;
} 
</style>