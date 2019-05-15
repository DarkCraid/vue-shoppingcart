<template>
    <div>
        <h1>Mi carrito</h1>
        <ProductForm @addToList="addToList" />
        <ProductItems
            v-for="product in productList"
            v-bind:key="product.id"
            v-bind:productItem="product"
            @addToCart="addToCart"
        />
        <p class="totalCart">Total: {{ total | toPrice }}</p>
    </div>
</template>

<script>
    import ProductItems from "./ProductItems.vue"
    import { toPrice } from "../libraries/filters"
    import Axios from 'axios'
    import ProductForm from "./ProductForm.vue"

    export default {
        name: "Shoppingcart",
        beforeCreate(){
            console.log('before create: ',this.productList);
        },
        created(){
            // metodo fetch() es solo soportado por chrome actualmente

            Axios.get('https://api.myjson.com/bins/hoto8').then(resp => {
                this.productList = resp.data.products;
                console.log('before create: ',this.productList);
            });
        },
        data(){
            return {
                productList: [
                    {id:1, name:"agua", price: 15},
                    {id:2, name:"leche", price: 45},
                    {id:3, name:"galletas", price: 20}
                ],
                cart: []
            }
        },
        computed:{
            total(){
                return this.cart.reduce(function(total,curr){
                    return total + curr.price;
                },0);
            }
        },
        filters:{
            toPrice
        },
        methods:{
            addToCart(product){
                this.cart.push(product);
            },
            addToList(prodItem){
                const prod = {
                    id: this.productList.length + 1,
                    name: prodItem.name,
                    price: prodItem.price,
                    quantity: 0
                }

                this.productList.push(prod);
            }
        },
        components:{
            ProductItems,
            ProductForm
        }
    }
</script>

<style scoped>
    h1{
        font-size: 24px;
        color: burlywood;
    }
    .totalCart{
        color: orange;
    }
</style>
