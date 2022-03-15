<template>
  <v-app>
    <v-main>
      <RegisterForm />
      <LoginForm />
      <CartComponent :products="cartProducts" :deleteProduct="deleteProduct" />
      <div v-for="product in products" :key="product.id">
        <CardProduct :product="product" :addToCart="addToCart" />
      </div>
    </v-main>
  </v-app>
</template>

<script>
import RegisterForm from './components/auth/RegisterForm';
import LoginForm from './components/auth/LoginForm';
import CardProduct from './components/CardProduct';
import CartComponent from './components/CartComponent';
import products from '../products.json';

export default {
  name: 'App',

  components: {
    RegisterForm,
    LoginForm,
    CardProduct,
    CartComponent,
  },

  data: () => ({
    products,
    cartProducts: [],
  }),

  methods: {
    addToCart(product) {
      if (this.cartProducts.find((p) => p.id === product.id)) {
        this.cartProducts.find((p) => p.id === product.id).quantity++;
      } else {
        this.cartProducts.push({
          ...product,
          quantity: 1,
        });
      }
    },
    deleteProduct(product) {
      this.cartProducts = this.cartProducts.filter((p) => p.id !== product.id);
    },
  },
};
</script>
