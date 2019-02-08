<template>
    <div class="row">
        <div class="form col-md-6 d-flex flex-column">
            <input type="text" placeholder="name" class="username p-3" v-model="name">
            <input type="text" placeholder="phone" class="phone p-3" v-model="phone">
            <input type="text" placeholder="email" class="email p-3" v-model="email">
            <label class="container my-3">I agree the processing of personal data
                <input type="checkbox" v-model="agree">
                <span class="checkmark"></span>
            </label>
            <a href="#" @click.prevent="sendForm" class="button button-submit my-2">{{loading ? 'loading...':'get in touch'}}</a>
        </div>
    </div>
</template>
<script>
import axios from 'axios';

export default {
    data(){
        return {
            name:'',
            phone:'',
            email:'',
            agree:false,
            loading:false,
        }
    },
    computed:{
        formIsValid(){
            let emailRegexp = /\S+@\S+\.\S+/;
            let nameRegexp = /^[a-zA-Z аА-яЯ]{2,30}$/;
            let phoneRegexp = /[0-9+-]/;

            return (    emailRegexp.test(this.email) &&
                        nameRegexp.test(this.name) &&
                        phoneRegexp.test(this.phone) &&
                        this.agree
                    )
        }
    },
    methods:{
        async sendForm(){
            if(!this.formIsValid){
                this.$emit('showModalEvent','Invalid form')
                return ;
            }

            this.loading = true;
            let url = 'http://httpbin.org/post'
            let data = {
                name:this.name,
                phone:this.phone,
                email:this.email,
            }
            let result = await axios.post(url,data).then(res=>res)
            if(result){
                this.loading = false;
                this.$emit('showModalEvent','Success!')
            }

        },
    }
}
</script>
