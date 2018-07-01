<template>
    <div id="translateForm">
        <form v-on:submit="formSubmit">
            <input type="text" placeholder="请输入要翻译的内容" v-model="textToTranslate">
            <select name="" id="" v-model="language">
                <option value="en">English</option>
                <option value="ru">Russian</option>
                <option value="ko">Korean</option>
                <option value="ja">Janpanese</option>


            </select>
            <input type="submit" value="翻译">
        </form>
    </div>
</template>

<script>
    export default {
        name: 'translateForm',
        data:function(){
            return {
                textToTranslate:'',
                language:""
            }
        },
        methods:{
            formSubmit:function(e){
//                alert(this.textToTranslate);
                this.$emit('formSubmit',this.textToTranslate,this.language);//名字随意
                e.preventDefault();

            }
        }
    }
</script>

<style>

</style>
