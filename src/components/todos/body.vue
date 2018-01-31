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
                v-for="todo in filteredTodos"
                @del="deleteTodo"
        ></item>
        <tabs
                :todos="todos"
                :filter="filter"
                @toggle="toggleFilter"
                @clearAllCompleted="clearAllCompleted"
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
                filter: 'all'
            }
        },
        computed:{
            filteredTodos(){
                if(this.filter === 'all'){
                    return this.todos
                }
                const completed = this.filter === 'completed'
                return this.todos.filter(todo => completed === todo.completed)
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
            },
            toggleFilter(state){
                this.filter = state
            },
            clearAllCompleted(){
                this.todos = this.todos.filter(todo => !todo.completed)
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
        width 600px
        margin 0 auto
        box-shadow 0 0 5px #666
        .add-input
            position relative
            margin 0
            width 100%
            font-size 24px
            font-family inherit
            font-weight inherit
            line-height 1.4em
            outline none
            color inherit
            box-shadow inset 0 -1px 5px 0 rgba(0,0,0,0.2)
            box-sizing border-box
            font-smoothing antialiased
            padding 16px 16px 16px 60px
            border none
            //box-shadow inset 0 -2px 1px rgba(0,0,0,0.03)
</style>
