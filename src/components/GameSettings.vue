<script>
export default {
  data() {
    return {
      formData: {
        nbrPlayers: Number,
//emit le game ready
      }
    };
    let gameReady = true
  },
  methods: {
    submitForm() {
        this.$emit('formSubmitted', this.nbrPlayers, this.gameReady);
        console.log("nbr de joueurs",this.nbrPlayers, this.gameReady);
    }
  }
};
</script>
<template>
    <main>
        <div class="overlay-container">
            <h2>Lancer une Partie</h2>
            <form @submit.prevent="submitForm">
                <label for="numberInput">Choisissez le nombre de joueurs :</label>
                <input type="number" id="numberInput" v-model="nbrPlayers" min="1" max="15"/>        
                <button type="submit" >Lancer la Partie</button>
            </form>
        </div>
    </main>
</template>
<style scoped>

form {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    height: 80%;
}
.overlay-container {
    background: #fff;
    color: #333;
    width: 70%;
    height: 70%;
    padding: 1.5em;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    border-radius: 10px;
}

.overlay-container button {
    padding: 1em 1.5em;
    border: none;
    background: var(--green);
    font-family: var(--font);
    color: white;
    font-size: 1.5em;
    border-radius: 10px;
    
}

.overlay-container input {
    font-size: 1.5em;
    padding: .5em;
    text-align: center;
    font-family: var(--font);
}

.overlay-container h2{
    text-align: center;
    font-size: 2em;
    height: 20%;
}

main {
    font-family: var(--font);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 2;
    position: absolute;
    background: #5454545f;
    width: 100%;
    min-height: 100%;
    max-height: 100%;

    backdrop-filter: blur(4px);
}


</style>