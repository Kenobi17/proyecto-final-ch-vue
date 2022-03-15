<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Producto</th>
          <th class="text-left">Precio</th>
          <th class="text-left">Cantidad</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td>{{ product.name }}</td>
          <td>${{ (product.price * product.quantity).toFixed(2) }}</td>
          <td>
            <v-btn
              @click="product.quantity--"
              :disabled="product.quantity === 1"
            >
              - </v-btn
            >{{ product.quantity }}
            <v-btn @click="product.quantity++"> + </v-btn>
            <v-btn @click="deleteProduct(product)">
              <v-icon>mdi-delete</v-icon>
            </v-btn>
          </td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
export default {
  name: 'CartComponent',

  data() {
    return {};
  },
  props: {
    products: Array,
    deleteProduct: Function,
  },
};
</script>
