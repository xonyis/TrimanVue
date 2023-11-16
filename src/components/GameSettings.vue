<script setup>
</script>
<template>
    <main>
        <div class="overlay-container">
            <h2>Lancer une Partie</h2>
            <label for="numberInput">Choisissez le nombre de joueurs :</label>
            <input type="number" id="numberInput" v-model="nombre" min="1" max="6"/>        
            <button>Lancer la Partie</button>
        </div>
    </main>
</template>
<style scoped>
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