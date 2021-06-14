<template>
<div class="get" v-if="list.length">
    <table>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Year</th>
            <th>Color</th>
            <th>Value</th>
        </tr>
        <tbody v-for="item in list" :key="item.id">
            <tr>
                <td>{{item.id}}</td>
                <td>{{item.Name}}</td>
                <td>{{item.Year}}</td>
                <td>{{item.Color}}</td>
                <td>{{item.pantone_Value}}</td>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
   import axios from 'axios';

   export default {
       name: 'Get',
       data() {
           return {
               list: []
           }
       },
       async mounted() {
           const result = await axios.get("https://tutorial4-api.herokuapp.com/api/users/");
           this.list= result.data.data;
       }
   }
</script>

<style scoped>
    #secure {
        background-color: #FFFFFF;
        border: 1px solid #CCCCCC;
        padding: 20px;
        margin-top: 10px;
    }
</style>