<template>
    <div>
        <el-button @click='goback' type='info'>退出</el-button>
    </div>
</template>


<script>
export default {
    data(){

    },
    methods:{
        goback(){
            this.$router.push('login')
        }
    }
}
</script>

<style scoped>

</style>
