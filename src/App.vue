<template>
    <div id="app">
        <Shop/>
    </div>
</template>

<script>
    import Shop from './components/Shop.vue';

    let App = {
        name: 'app',
        components: {
            Shop
        }
    };
    export default App;
</script>

<style lang="scss">
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
