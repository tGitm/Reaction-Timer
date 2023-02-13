<template>
    <br> <br> <br>
    <h3>Your reaction time is {{ reactionTimeScore }} ms.</h3>
    <p :class="{ 'good': time === 1, 'slow': time === 2, 'bad': time === 3 }"> {{ resutlText }}</p>
</template>

<script>
export default {
    props: ['reactionTimeScore'],
    data() {
        return {
            resutlText: null,
            time: null
        }
    },
    methods: {
        appResponse() {
            if (this.reactionTimeScore < 300) {
                this.resutlText = "Good :)"
                this.time = 1
            } else if (this.reactionTimeScore < 500) {
                this.resutlText = "Slow!"
                this.time = 2
            } else {
                this.resutlText = "Very bad :("
                this.time = 3
            }
        }
    },
    mounted() {
        this.appResponse()
    }
}
</script>

<style>
    h3 {
        color: #42b883;
    }

    .good {
        color:#42b883
    }

    .slow {
        color: orange;
    }

    .bad {
        color: red;
    }
</style>