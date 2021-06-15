<template>
<div class="get" v-if="list.length">
    <div class="search-bar">
        <b-form-input
          @input="search_text()"
          v-model="search.text"
          type="text"
          placeholder="Search by Name"
        ></b-form-input>
      

      </div>
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
        search_text() {
      //console.log(this.search.text);
var inside = this;
this.item = this.list.filter(function(item) {
        if (
          item.place
            .toLowerCase()
            .indexOf(inside.search.text.toLowerCase()) != "-1"
        ) {
          return item;
        }
      });
    },
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