<template>
    <my-table :tabledata="myjsondata"></my-table>
</template>

<script>
    import MyTable from "../../components/MyTable"
    import {myjsondata} from "../../tabledata";

    export default {
        name: "Home",
        components:{
            MyTable
        },
        data(){
            return{
                myjsondata
            }
        }
    }
</script>

<style scoped>

</style>