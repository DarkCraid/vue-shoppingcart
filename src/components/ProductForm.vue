<template>
    <form @submit.prevent="onSubmit">
        <input 
            type="text" 
            placeholder="Nombre del product" 
            v-model="name"
            v-validate="'required'"
            name="name"
        >
        <span>{{ errors.first('name') }}</span>
        <input 
            type="number" 
            placeholder="Precio del producto" 
            v-model="price"
            v-validate="'required|min_value:1|min:1'"
            name="price"
        >
        <span>{{ errors.first('price') }}</span>
        <button type="submit">Guardar</button>
    </form>
</template>

<script>
export default {
    name:'ProductForm',
    data(){
        return {
            name: '',
            price: 0
        }
    },
    methods:{
        onSubmit(){
            this.$validator.validate().then(valid => {
                if(valid){
                    this.$emit('addToList',{
                        name: this.name,
                        price: parseInt(this.price)
                    });
                }else{
                    console.log("algo esta mal ",valid);
                }
            }).catch(err => console.log(err));
        }
    }

}
</script>

<style>
form{
    background: #d898df;
    max-width: 400px;
    width: 80%;
    position: relative;
    display: inline-block;
    padding: 30px;
    border-radius: 3px;
    box-shadow: 0px 0px 8px #c2c2c2;
}
form > *{
    border-radius: 3px;
    border: 0;
    display: flex;
    width: 100%;
    position: relative;
    left: -21px;
}
form input{
    padding: 5px 20px;
    border: 1px solid #e3e3e3;
}
form button{
    background: #000;
    color: #e3e3e3;
}
</style>
