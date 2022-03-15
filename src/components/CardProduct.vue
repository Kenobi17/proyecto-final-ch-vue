<template>
  <v-container>
    <v-card class="mx-auto" max-width="440">
      <v-img :src="product.image" height="300px"></v-img>

      <v-card-title> {{ product.name }} </v-card-title>

      <v-card-subtitle>
        Precio - ${{ product.price.toFixed(2) }}
      </v-card-subtitle>

      <v-card-actions>
        <v-btn @click="show = !show" color="orange lighten-2" text>
          Descripcion
        </v-btn>
        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
        <v-spacer></v-spacer>

        <v-spacer></v-spacer>

        <v-btn
          @click="
            addToCart({
              id: product.id,
              name: product.name,
              price: product.price,
            })
          "
          icon
        >
          +<v-icon>mdi-cart</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            {{ product.description }}
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'CardProduct',

  data: function () {
    return {
      show: false,
    };
  },

  props: {
    product: Object,
    addToCart: Function,
  },
};
</script>
