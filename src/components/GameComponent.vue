<script>
import PopUp from './RulesComponent.vue';
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
    rules: null,
    rules1: null,
    nbrPlayer: 1,
    };
  },
  components: {
    PopUp,
  },
  methods: {
    ouvrirPopUp() {
      this.$refs.popup.ouvrirPopUp();
    },
    lancerDés() {
        this.d1 = Math.floor(Math.random() * 6) + 1;
        this.d2 = Math.floor(Math.random() * 6) + 1;
        this.total = this.d1+ this.d2;
        console.log(this.nbrPlayers);
        if (this.isTriman === true) {
            console.log('trigger');
            this.checkRulesTtl(this.total,this.d1, this.d2)
        }else {
            this.rules1 = "on cherche un Triman"
            this.checkIsTriman()
            if (this.nbrPlayer < this.nbrPlayers) {
                this.nbrPlayer++
            }else {
                this.nbrPlayer = 1
            }
        }
    },
    checkIsTriman(d1, d2, total){
        if (this.d1 === 3 || this.d2 === 3 || this.total === 3) {
            this.rules1 = 'on a un Triman, Tu bois pour feter ca'
            alert('On a un triman')
            this.isTriman = true
        }else {
            console.log("no triman");
        }
    },

    checkRulesTtl(total, d1, d2) {
        // VERIF DOUBLE
        if (d1 === d2) {
            this.rules1 = 'Tu distribue '+d1+' gorgées'
        }else {
            this.rules1 = ' '
        }

        //VERIF TRIMAN DÉ
        if (d1 || d2 === 3) {
            this.rules = 'Triman bois pour feter ca '
        }else {
            this.rules = ''
        }
        
        // VERIF TOTAL 
        switch (total) {
            case 3:
                this.rules = 'Triman bois pour feter ca '
                break;
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
            if (this.nbrPlayer < this.nbrPlayers) {
                this.nbrPlayer++
            }else {
                this.nbrPlayer = 1
            }
                break;
        };
    },
  },
};
</script>

<template>
    <div class="parent">
        
<div class="div1"><div class="tourContainer"><h2>C'est au tour du :</h2><span>{{ nbrPlayer }}/ {{ nbrPlayers }}</span></div>  <p></p></div>
<div class="div2" @click="ouvrirPopUp"><h2>Règle :</h2><p class="rules">{{ rules1}} <br>{{ rules }}</p></div>
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
    border-radius: 10px;
    padding: 1em 2em;
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
.div1 { grid-area: 1 / 1 / 3 / 5; 
    background-color: var(--blue);
    display: flex;
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
}
.div3 { grid-area: 3 / 3 / 5 / 7; 
    background: var(--red);
}
.div4 { grid-area: 5 / 3 / 7 / 7; 
    background: var(--green);
    justify-content: center;
    font-size: 1.5em;
    display: flex;
    align-items: center;
}
.div5 { grid-area: 3 / 1 / 7 / 3;
    background: var(--black);
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.div6 { grid-area: 3 / 7 / 7 / 9;
    background: var(--black);
    text-align: center;
    color: #e6e6e6;

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