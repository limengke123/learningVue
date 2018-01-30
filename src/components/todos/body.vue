<template>
    <div class="body">
        <input
                type="text"
                class="add-input"
                autofocus="autofocus"
                placeholder="what's next?"
                @keyup.enter="addTodo"
        >
        <item
                :todo="todo"
                :key="todo.id"
                v-for="todo in todos"
                @del="deleteTodo"
        ></item>
        <tabs
                :todos="todos"

        ></tabs>
    </div>
</template>

<script>
    import tabs from './tabs.vue'
    import item from './item.vue'
    let id = 0
    export default{
        data(){
            return {
                todos: [],
                fliter: 'all'
            }
        },
        methods: {
            addTodo(e){
                this.todos.unshift({
                    id: id++,
                    content: e.target.value.trim(),
                    completed: false
                })
                e.target.value = ""
                console.log(this.todos)
            },
            deleteTodo(id){
                // findIndex array原生方法，传入一个函数，返回满足函数的索引，升级版的indexOf，不满足返回-1
                console.log(this.todos.findIndex(todo => todo.id === id))
                this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1)
            }
        },
        components: {
            tabs,
            item
        }
    }
</script>

<style lang="stylus" scoped>
    .body
        height 200px
        background-color #b94283
</style>
