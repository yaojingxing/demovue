<template>
    <table class="mytable">
        <tr >
            <th v-for="(item,key) in tabledata[0]" v-if="key!=='editable'">{{key}}</th>

        </tr>
        <tr v-for="(item,index) in tabledata">
            <td v-for="(value,key) in tabledata[index]" v-if="key!=='editable'">
                <span v-if="!isActive(index)">{{value}}</span>
                <input v-else type="text" :placeholder=value v-model="tabledata[index][key]" >
            </td>
        </tr>
    </table>
</template>

<script>
    export default {
        name: "table",
        props: {
            tabledata: {
                type: Object,
                default() {
                    return {}
                }
            }
        },
        methods: {
            isActive(index) {
                return this.user0[index].editable === true;
            }
        }
    }
</script>

<style scoped>

</style>