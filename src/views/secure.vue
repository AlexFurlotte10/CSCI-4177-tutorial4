<template>
<div class="get" v-if="list.length">
    <table>
        <tr>
            <th>Title</th>
            <th>First Name</th>
            <th>Last Name</th>
            <th>Picture</th>
         
        </tr>
        <tbody v-for="item in list" :key="item.id">
            <tr>
                <td>{{item.title}}</td>
                <td>{{item.firstName}}</td>
                <td>{{item.lastName}}</td>
                <td><img :src="path+'https://tutorial4-api.herokuapp.com/api/users/'+item.picture" class="img-circle" alt="Services"></td>
               
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