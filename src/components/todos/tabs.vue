<template>
<div class="tab" v-show="count > 0">
{{count}}
</div>
</template>

<script>
export default{
    //props拿进来的数据和定于在data里差不多啊 直接this就能拿
    props:{
        todos:{
            type:Array,
            required:true
        }
    },
    computed:{
        count(){
            return this.todos.length
        }
    }
}
</script>

<style lang="stylus" scoped>
.tab
    color #333
</style>
