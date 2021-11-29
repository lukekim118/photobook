<template>
    <div>
        <form class="flex flex-col items-center" @submit.prevent= "login">
            <div class="flex flex-col user">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="userName">User Name</label>
                <input type="text" class="bshadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight" v-model= "userName" id="userName" />
                
            </div>
            <div class="flex flex-col mt-10">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="password"> Password</label>
                <input 
                    class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700"
                    type="password"
                    v-model= "password"
                />
            </div>
            <button class="btn-blue">Sign in </button>
        </form>
        <div class="text-red-600">{{ error.message }}</div>
    </div>
</template>
<script>
import {mapActions} from 'vuex'
export default {
    data:()=> ({
         username: "",
         password: "",
         email:"",
         error:""
            
        }),
        methods: {
            ...mapActions({
                loginVue: "auth/login",
                }),
            async login(){
                try {
                    await this.loginVue({
                        username: this.username,
                        password: this.password
                    });
                } catch (error) {
                    this.error=error;
                }
            }
        }
    }
    

</script>
<style lang="scss" scoped>
    
</style>