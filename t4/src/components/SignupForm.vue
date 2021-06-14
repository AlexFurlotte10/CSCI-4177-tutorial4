<template>
<div class="row">
<nav>
      <router-link to="/">Home</router-link>
      <router-link to="/login">Login</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view></router-view>

    <form id="signup-form" v-on:submit.prevent="submit">
        
            
            
            <div class="col-12 form-group">
                <label class="col-form-label col-form-label-lg">Email <span class="text-danger">*</span></label>
                <input type="email"  name="foobar" v-model="foobar" v-model.trim="$v.email.$model" :class="{'is-invalid': validationStatus($v.email)}" class="form-control form-control-lg">
                
            </div>
         
            <div class="col-12 form-group">
                <label class="col-form-label col-form-label-lg">Password <span class="text-danger">*</span></label>
                <input type="password" name="foobar" v-model="foobar" v-model.trim="$v.password.$model" :class="{'is-invalid': validationStatus($v.password)}" class="form-control form-control-lg">
               
            </div>
            
            <div class="col-12 form-group text-center">
                <button @click="goToHome()"> </button>
            </div>
                </form>
        </div>

</template>
<script>
</script>
<style>
.btn-vue{
    background: #53B985;
    color: #31485D;
    font-weight: bold;
}
</style>