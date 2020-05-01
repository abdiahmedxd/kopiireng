<template>
    <div class="container">
        <form @submit="handleSubmit">
            <input type="text" placeholder="username" v-model="username"/>{{errors.username}}
            <input type="text" placeholder="password" v-model="password" />{{errors.password}}
            <input type="submit" value="submit"/>
        </form>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                errors:{
                    username: '',
                    password: ''
                },
                username:'',
                password:''
            }
        },
    methods:{
        handleSubmit(e){
            if(this.username === ""){
                this.errors.username = 'user tidak boleh kosong cok'
            
            }else{
                this.errors.username = ''
            }
            if(this.password === ""){
                this.errors.password = 'user tidak boleh kosong cok'
            
            }else{
                this.errors.password = ''
            }

            e.preventDefault();


        }
    }

}

</script>

<style scoped>


</style>
