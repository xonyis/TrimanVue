<script>
import PopUp from './RulesComponent.vue';
import PlayersRotation from './PlayerRotationComponent.vue'
import { ref, reactive, watch } from 'vue'
import gsap from 'gsap'



export default {
    props: {
    nbrPlayers: Number,
    },
    data() {
    return {
      d1: null,
      d2: null,
    total: null,
    rulesTriman: null,
    rules: null,
    playersDisplay: 1,
    trimanPlayer: null,
    joueurActuel: null,
    };
  },
  components: {
    PopUp,
    PlayersRotation,

  },
  methods: {
    ouvrirPopUp() { this.$refs.popup.ouvrirPopUp(); },

    lancerDés() {
        this.d1 = Math.floor(Math.random() * 6) + 1;
        this.d2 = Math.floor(Math.random() * 6) + 1;
        this.total = this.d1+ this.d2;
        console.log(this.nbrPlayers);
        if (this.isTriman === true) {
            console.log('trigger');
            // this.checkRulesTtl(this.total,this.d1, this.d2)
        }else {
            this.rulesTriman = "on cherche un Triman"
            this.checkIsTriman()
            
        }
    },

    triggerChildMethod() {
      // Accéder à la méthode du composant enfant via le ref
      this.$refs.childComponentRef.changerJoueur();
    },

    checkIsTriman(d1, d2, total){
        if (this.d1 === 3 || this.d2 === 3 || this.total === 3) {
            this.rulesTriman = 'on a un Triman, Joueur ' + this.joueurActuel + ' tu bois pour feter ca !'
            this.isTriman = true
            this.trimanPlayer = this.joueurActuel
            console.log("triman player "+ this.trimanPlayer);
        }else {
            console.log("no triman");
            this.triggerChildMethod()
        }
    },
    receiveArrayFromChild(array) {
      console.log("Tableau reçu du composant enfant :", array);
      // Faites ce que vous voulez avec le tableau reçu du composant enfant
    },
    receiveActualPlayer(joueurActif) {
        this.joueurActuel = joueurActif
      console.log("joueurActif :", joueurActif);
      // Faites ce que vous voulez avec le tableau reçu du composant enfant
    },
    checkRulesTtl(total, d1, d2) {
        // VERIF DOUBLE
        if (d1 === d2) {
            this.rules = 'Tu distribue '+d1+' gorgées'
        }else {
            this.rules = ' '
        }

        //VERIF TRIMAN DÉ
        if (d1 === 3 || d2 === 3 || total === 3) {
            this.rulesTriman = 'Triman bois pour feter ca '
            
        }else {
            this.rulesTriman = ' '
        }
        
        // VERIF TOTAL 
        switch (total) {
            case 9:
                this.rules = 'La personne à ta gauche bois une gorgés'
                break;
            case 10:
                this.rules = 'Tu bois une gorgé'
                break;
            case 11:
                this.rules = 'La personne à ta droite bois une gorgés'
                break;
            default:
            this.rules = ''
                break;
        };
    },
  },
};
</script>

<template>
    <div class="parent">
        
<div class="div1"><PlayersRotation :nbrPlayers="nbrPlayers" ref="childComponentRef" @tableau-joueurs="receiveArrayFromChild" @joueur-actif="receiveActualPlayer"></PlayersRotation></div>
<div class="div2" @click="ouvrirPopUp">
    
    <div><h2>Règle :</h2> <h5 style="color: var(--red);">Triman : Joueur {{ trimanPlayer}}</h5></div>
    <p class="rules">{{ rulesTriman }}<br>{{rules}}</p>
</div>
<div class="div3"><h2>Total :</h2><p class="scrTtl">{{ total }}</p></div>
<div class="div4" @click="lancerDés"><h2>Jouer !</h2></div>
<div class="div5" ><h2>Dé 1</h2>
    <img v-if="d1" :src="`/de${d1}.svg`" alt="Dé" />
</div>
<div class="div6"><h2>Dé 2</h2><img v-if="d2" :src="`/de${d2}.svg`" alt="Dé" /></div>
</div>
<PopUp ref="popup" />

</template>
<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

.parent >div{
    
}

.parent {
    font-family: var(--font);
    color: #e6e6e6;
    padding: 2em;
display: grid;
grid-template-columns: repeat(8, 1fr);
grid-template-rows: repeat(6, 1fr);
grid-column-gap: 1.5em;
grid-row-gap: 1em;
width: 100%;
height: 100%;
}
.div1 { 
    grid-area: 1 / 1 / 3 / 5; 
    display: flex;
    padding: 0;
    margin: 0;
    flex-direction: column;
}
.tourContainer {
    display: flex;
    justify-content: space-between;
    width: 100%;
    padding: 0em;
}

.div1 p {
    font-size: 2em;
    text-align: center;
}

.div1 span {
    font-size: 1.5em;
}
.div2 { grid-area: 1 / 5 / 3 / 9;
    background: var(--yellow);
    color: var(--black);
    border-radius: 10px;
    padding: 1em 2em;
    display: flex;
    flex-direction: column;
}

.div2 h2 {
    width: max-content;
}

.div2 div {
    display: flex;
    justify-content: space-between;
}
.div3 { grid-area: 3 / 3 / 5 / 7; 
    background: var(--red);
    border-radius: 10px;
    padding: 1em 2em;
}
.div4 { grid-area: 5 / 3 / 7 / 7; 
    background: var(--green);
    justify-content: center;
    font-size: 1.5em;
    display: flex;
    align-items: center;
    border-radius: 10px;
    padding: 1em 2em;
}
.div5 { grid-area: 3 / 1 / 7 / 3;
    background: var(--black);
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 10px;
    padding: 1em 2em;
}

.div6 { grid-area: 3 / 7 / 7 / 9;
    background: var(--black);
    text-align: center;
    color: #e6e6e6;
    border-radius: 10px;
    padding: 1em 2em;

}

.scrTtl {
    width: 100%;
    text-align: center;
    font-size: 2.5em;
    line-height: .2em;
}

img {
    width: 50%;
    height: 150px;
    color: #e6e6e6;
}

</style>