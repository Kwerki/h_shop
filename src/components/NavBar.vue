<template>
  <v-app-bar app color="blue-grey-lighten-4" dark>
    <v-toolbar-title style="color: #212121; cursor: pointer;" @click="router.push('/')">
      Hublitz Parts
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn @click="router.push({ name: 'Catalog' })" text>
      <v-icon left>mdi-printer-3d</v-icon>
      Products
    </v-btn>
    <v-btn @click="router.push({ name: 'CartView' })">
      <v-icon left>mdi-cart</v-icon>
      Cart
    </v-btn>
  </v-app-bar>
</template>

<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()
</script>

<style>
.clickable {
  cursor: pointer;
}
</style>
