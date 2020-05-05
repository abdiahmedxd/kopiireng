<template>
    <div class="container">
        <form @submit="handleSubmit">
            <h1> Login </h1>
            
            <input type="text" class="input" placeholder="username" v-model="username"/>{{errors.username}}
            <input type="password" class="input" placeholder="password" v-model="password" />{{errors.password}}
            <br>
            <input type="submit" value="submit"/>
        </form>
    </div>
</template>

<script>
    import qs from 'qs'
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
                this.errors.username = 'user tidak boleh kosong '
            
            }else{
                this.errors.username = ''
            }
            if(this.password === ""){
                this.errors.password = 'user tidak boleh kosong '
            
            }else{
                this.errors.password = ''
            }

            fetch('http://localhost:3000/login',{
                method:'POST',
                headers: {
                    'Content-type': 'application/x-www-form-urlencoded'
                },
                body: qs.stringify({username: this.username, password: this.password}) 
            })
            .then(res => res.json())
            .then(function(data){
                if(data.success === true){
                    alert('Berhasil login')
                }else{
                    alert(data.message)
                }
                localStorage.setItem('user',JSON.stringify(data.user))
            })
            e.preventDefault();

        }
    },

}

</script>

<style scoped>
    .container{
    width: 350px;
	background: white;
	margin: 80px auto;
	padding: 30px 20px;
}
.container form {

    margin-top: 15px;
    float: left;
    padding: 5px;
}
.container input{
    width: 90%;
    margin-top: 1px;
    height: 50px;
    border: 0px;
    border-bottom: 1px solid #6a82fb;
    font-size: 16px;
    font-family: OpenSans-Light;
    background: transparent;
}

</style>
