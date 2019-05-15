<template>
    <div v-if="productItem">
        <div class="item">
            <div class="desc">
                <span>{{ productItem.name }}</span>
                <span>{{ productItem.price | toPrice }}</span>
            </div>
            <button @click="$emit('addToCart',productItem)">Agregar</button>
        </div>
    </div>
</template>

<script>
import { toPrice } from "../libraries/filters"

export default {
    name: "PrductItems",
    props:{
        productItem: Object,

    },filters:{
        toPrice
    }
}
</script>

<style scoped>
    .item{
        background: #89afea;
        padding: 22px 30px;
        width: 80%;
        max-width: 400px;
        border-radius: 4px;
        position: relative;
        margin: 15px auto;
        height: 32px;
        box-shadow: 0px 0px 8px #cecdcd;
    }
    .desc{
        color: #FFF;
        position: relative;
        display: inline-block;
        text-align: left;
        float: left;
    }
    .desc span{
        display: block;
        margin-bottom: 4px;
    }
    .item button{
        display: inline-block;
        float: right;
        border: 0;
        background: #dfa741;
        padding: 5px 20px;
        color: #FFF;
        font-size: 18px;
        border-radius: 3px;
    }
    .item button:hover{
        cursor: pointer;
        background: #efc730;
    }
</style>
