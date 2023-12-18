<script>
import GameComponent from '../components/GameComponent.vue';
import GameSettings from '../components/GameSettings.vue';

export default {
  data() {
  	return {
	    gameReady: true,
  	}
	},
    components: {
        GameComponent,
        GameSettings,
    },
}

</script>
<template>

    <main>
        <GameComponent/>
        <GameSettings v-show="!gameReady"/>
    </main>
</template>
<style scoped>
main {
    width: 100vw;
    height: 100vw;
}
</style>