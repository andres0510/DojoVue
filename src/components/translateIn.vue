<template>
    <div id="translateIn">
        Translation
        <form v-on:submit="formSubmit">
            <input type="text" v-model="textoTraducir" placeholder="escriba la palabra">
            <input type="submit" value="traducir">
        </form>
        <select v-model="idioma">
            <option value="en"> Inglés </option>
            <option value="it"> Italiano </option>
        </select>
    </div>
</template>

<script>
export default {
    name: "translateIn",
    data(){
        return{
            textoTraducir:'',
            idioma:''
        }
    },
    created(){
        this.idioma='en';
    },
    methods:{
        formSubmit(e){
            this.$emit('formSubmit', this.textoTraducir, this.idioma);
            e.preventDefault();
        }
    }
}
</script>