<template>
    <div class="item">
        <input
                type="checkbox"
                class="toggle"
                v-model="todo.completed"
        >
        <label>{{todo.content}}</label>
        <button @click="deleteTodo" class="destroy">X</button>
    </div>
</template>

<script>
    export default{
        props: {
            todo: {
                type: Object,
                required: true
            }
        },
        methods: {
            deleteTodo(){
                this.$emit('del', this.todo.id)
            }
        }
    }
</script>

<style lang="stylus" scoped>
    .item
        color #333
</style>
