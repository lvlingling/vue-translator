<template>
    <div id="app">
        <h1>在线翻译</h1>
        <h5>简单、易用、便捷</h5>
        <img src="./assets/logo.png">
        <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
        <translateOutput v-text="translatedText"></translateOutput>
        <router-view/>
    </div>
</template>

<script>
    import TranslateForm from './components/TranslateForm'
    import translateOutput from './components/translateOutput'

    export default {
        name: 'App',
        data:function(){
            return{
                translatedText:""
            }
        },
        components: {TranslateForm,translateOutput},
        methods: {
            translateText:function(text,language){
//                alert(text);
                this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180612T081625Z.07e998bb7ecd883d.7ff7861f174094225a4e68e445726bdea1232709&lang='+language+'&text='+text)
                    .then((response)=>{
//                    console.log(response.body.text[0]);
                        this.translatedText=response.body.text[0];
                })
            }

        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
