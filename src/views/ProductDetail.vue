<template>
  <v-container>
    <v-btn @click="$router.push({name: 'Catalog'})">Back to Catalog</v-btn>
  </v-container>
    <div class="product">
        <div class="product-image">
            <img :src="selectedProduct.thumbnail" alt="">
        </div>
        <div class="product-info">
            <p>Brand: {{ selectedProduct.brand }}</p>
            <p>Description: {{ selectedProduct.description }}</p>
            <h2>Price: ${{ selectedProduct.price }}</h2>
          <v-container>
            <v-btn @click="addToCard">Add to cart</v-btn>
          </v-container>
        </div>
    </div>
</template>

<script>
    import { defineComponent } from 'vue';
    export default defineComponent({
        name: 'ProductDetail'
    })

</script>

<script setup>
    import { computed } from 'vue';
    import { productsStore } from '@/stores/products';
    import { useRoute, useRouter } from 'vue-router';

    const route = useRoute();
    const router = useRouter();
    const store = productsStore();


    const selectedProduct = computed(() => {
       return store.products.find((item) => item.id === Number(route.params.id))
    })

    const addToCard = () => {
        store.addToCart(selectedProduct.value)
        router.push({name: 'CartView'})
    }

</script>

<style scoped>

.product{
    display: flex;
    margin-top: 50px;
}

.product-image{
    margin-right: 24px;
    box-shadow: 0px 0px 14px 1px #e6e6e6;
}

</style>
