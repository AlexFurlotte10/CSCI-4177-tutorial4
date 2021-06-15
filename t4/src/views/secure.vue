<template>
<div class="get" v-if="list.length">
    <input type="text" v-model="search" placeholder="search users"/>
    <div v-for="item in filteredItems" :key="item.id">
        <h2>item.firstName</h2>
    </div>
    <table>
        <tr>
            <th>Title</th>
            <th>First Name</th>
            <th>Last Name</th>
            <th>Picture</th>
         
        </tr>
        <tbody v-for="item in list" :key="item.id">
            <tr>
                
               <th> {{item.title}}</th>
               <th> {{item.firstName}}</th>
                <th>{{item.lastName}}</th>
                <th>{{item.picture}}</th>
                <th><button v-on:click="details()">Profile</button></th>
               
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
               list: [],
               search: ''
           }
       },
       async mounted() {
           const result = await axios.get("https://tutorial4-api.herokuapp.com/api/users/");
           this.list= result.data.data;
       },
       methods: {
       details() {
                
                        this.$emit("authenticated", true);
                        this.$router.replace({ name: "Home" });
                   
            },
        computed: {
            filteredItems: function(){
                return this.list.filter((item) => {
                    return item.firstName.match(this.search)
                });
            }
   }
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