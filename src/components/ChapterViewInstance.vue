<template>
    <div>{{dataEx}}</div>
    <div id="app">
        <p>{{ objEx.foo }}</p>
        <!-- this will no longer update `foo`! -->
        <button v-on:click="objEx.foo = 'baz'">Change it</button>
    </div>
</template>

<script>

    var dataEx = 1

    var obj = {
        foo: 'bar'
    }
    Object.freeze(obj)
    export default {
        name: 'ChapterViewInstance',
        data() {
            return {
                // Our data object
                dataEx,
                objEx: obj
            }
        },
        mounted() {},
        methods: {},
        components: {}

    }

    dataEx = 2
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped="scoped">
    h3 {
        margin: 40px 0 0;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
</style>