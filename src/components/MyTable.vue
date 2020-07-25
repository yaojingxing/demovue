<template>
    <table class="mytable">
        <tr >
            <th v-for="(item,key) in filterdata(tabledata[0])"  :key="key">{{key}}</th>
<!-- v-if="key!=='editable'"-->
        </tr>
        <tr v-for="(item,index) in tabledata" :key="index">
            <td v-for="(value,key) in filterdata(tabledata[index])" :key="key" >
<!--                v-if="key!=='editable'"-->
                <span v-if="!isActive(index)">{{value}}</span>
                <input v-else type="text" :placeholder=value v-model="tabledata[index][key]" >
            </td>
        </tr>
    </table>
</template>

<script>
    export default {
        name: "MyTable",
        props: {
            tabledata: {
                type: Array,
                default() {
                    return []
                }
            }
        },
        methods: {
            isActive(index) {
                return this.tabledata[index].editable === true;
            },
            filterdata(data){
                let newdata = JSON.parse(JSON.stringify(data));
                delete newdata.editable;
                return newdata;

            }

            // filterdata(data){
            //     return data.filter(function(item){
            //
            //     })
            // }

        }
    }
</script>

<style scoped>
    *{
        border:0;
        margin:0;
    }
    .mytable,.mytable>tr,.mytable th,.mytable td{
        border:1px black solid;
        font-size:15px;


    }
    .mytable{
        border-collapse:collapse;
        width:400px;
        height:400px;
        text-align:center;
    }
    .mytable input{
        font-size:15px;
        text-align:center;
        display:inline-block;
        outline:none;
    }


</style>