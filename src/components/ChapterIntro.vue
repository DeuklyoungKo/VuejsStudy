<template>
    <div id="counter">
        Counter:
        {{ counter }}
    </div>
    <div id="bind-attribute">
        <span v-bind:title="message">
            Hover your mouse over me for a few seconds to see my dynamically bound title!
        </span>
    </div>
    <div id="event-handling">
        <p>{{ message }}</p>
        <button v-on:click="reverseMessage">Reverse Message</button>
    </div>
    <div id="two-way-binding">
        <p>{{ message }}</p>
        <input v-model="message"/>
    </div>
    <div id="conditional-rendering">
        <span v-if="seen">Now you see me</span>
    </div>
    <div id="list-rendering">
        <ol>
            <li v-for="todo in todos" v-bind:key="todo">
                {{ todo.text }}
            </li>
        </ol>
    </div>
    <div id="list-rendering">
        <ol>
            <li v-for="todo3 in todos2" v-bind:key="todo3">
                {{ todo3 }}
            </li>
        </ol>
    </div>
    <div>
        TodoItem<br>
            <ol>
                <todo-item v-for="item in groceryList" v-bind:todo="item" v-bind:key="item.id"></todo-item>
            </ol>
        </div>
    </template>

    <script>
        import TodoItem from './TodoItem.vue'

        export default {
            name: 'ChapterIntro2',
            data() {
                return {
                    counter: 0,
                    message: 'You loaded this page on ' + new Date().toLocaleString(),
                    seen: true,
                    todos: [
                        {
                            text: 'Learn JavaScript'
                        }, {
                            text: 'Learn Vue'
                        }, {
                            text: 'Build something awesome'
                        }
                    ],
                    todos2: [
                        "test1", "test2", "test3"
                    ],
                    groceryList: [
                        {
                            id: 0,
                            text: 'Vegetables'
                        }, {
                            id: 1,
                            text: 'Cheese'
                        }, {
                            id: 2,
                            text: 'Whatever else humans are supposed to eat'
                        }
                    ]
                }
            },
            mounted() {
                setInterval(() => {
                    this.counter++
                }, 1000)
            },
            methods: {
                reverseMessage() {
                    this.message = this
                        .message
                        .split('')
                        .reverse()
                        .join('')
                }
            },
            components: {
                //HelloWorld,
                TodoItem
            }

        }
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