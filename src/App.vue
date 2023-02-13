<template>
	<h1>Check your reflexes</h1>
	<button @click="start" :disabled="isPlaying">Play</button>

	<Block v-if="isPlaying" :delay="delay" @react="endGame" />
	
	<Result v-if="showResults" :reactionTimeScore="score" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
	name: 'App',
	components: {Block, Result },
	data() {
		return {
			isPlaying: false,
			delay: null,
			score: null,
			showResults: false
		}
	},
	methods: {
		start() {
			this.delay = 2000 + Math.random() + 5000 //random amount between 0 and 5000ms
			this.isPlaying = true
			this.showResults = false
		},

		endGame(reactionTime) {
			this.score = reactionTime
			this.isPlaying = false //end the game
			this.showResults = true
		}
	}
}
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #444;
		margin-top: 60px;
	}

	button {
		background: #0faf87;
		color: white;
		border: solid 1px #0faf87;
		padding: 8px 16px;
		border-radius: 4px;
		box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
		font-size: 16px;
		letter-spacing: 1px;
		cursor: pointer;
		margin: 10px;
		transition: 0.3s ease;
  	}

	button:hover {
		background: #fff;
		color: #0faf87;
	}

	button[disabled] {
		opacity: 0.2;
		cursor: not-allowed;
	}
</style>
