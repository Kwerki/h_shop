<template>
    <button @click="router.push({name: 'Catalog'})">Back to Catalog</button>
    <div v-if="!store.cart.length" style="text-align: center;">
        <p>Empty Cart...</p>
    </div>
    <div class="cart-item" v-else>
        <div 
            class="cart-items"
            v-for="item in store.cart"
            :key="item.id"
            >
            <div class="item-detail">
                <img :src="item.thumbnail" alt="">
                <span> Brand: {{ item.brand }}</span>
                <span> Category: {{ item.category }}</span>
                <span> Price: ${{ item.price }} $</span>
                <button @click="removeFromCart(item.id)">Remove</button>
            </div>
        </div>
    </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'CartView'    
})

</script>


<script setup>
    import { productsStore } from '../stores/products';
    import { useRouter } from 'vue-router';

    const router = useRouter()
    const store = productsStore()

    const removeFromCart = (id) => {
        store.removeFromCart(id)
    }
</script>

<style scoped>

.item-detail{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 32px;
    box-shadow: 0px 0px 17px 6px #e7e7e7;
    border-radius: 8px;
    padding: 16px;
} 

.item-detail img{
    width: 20%;
}

</style>