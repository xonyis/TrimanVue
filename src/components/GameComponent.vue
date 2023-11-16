script
<template>
    <div class="parent">
<div class="div1"><h2>C'est au tour de :</h2></div>
<div class="div2"><h2>Règle :</h2></div>
<div class="div3"><h2>Total :</h2></div>
<div class="div4"><h2>Jouer !</h2></div>
<div class="div5"><h2>Dé 1</h2></div>
<div class="div6"><h2>Dé 2</h2></div>
</div>
</template>
<style scoped>

.parent div{
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
}
.div6 { grid-area: 3 / 7 / 7 / 9;
    background: var(--black);
    text-align: center;
}
</style>