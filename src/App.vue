<template>
    <div id="app">
        <Fact
            v-bind:fact="fact"/>
    </div>
</template>

<script>
    import Fact from "@/components/Fact";

    export default {
        name: 'app',
        data() {
            return {
                fact: ""
            }
        },
        components: {
            Fact
        },
        methods: {
            update() {
                this.axios
                    .get("http://188.225.47.187/api/cats/random-fact.php")
                    .then((response) => {
                        this.fact = response.data;
                    });
            }
        },
        mounted() {
            this.update();
            setInterval(this.update, 10000);
        }
    }
</script>

<style>
    body {
        padding: 0;
        margin: 0;
        min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
