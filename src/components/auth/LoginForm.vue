<template>
  <v-container>
    <v-row>
      <v-col cols="6">
        <h1>Iniciar Sesion</h1>
        <v-form v-model="valid" ref="form" @submit.prevent="submitForm">
          <v-container>
            <v-row>
              <v-col cols="12">
                <v-text-field
                  v-model="email"
                  label="E-mail"
                  required
                ></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-text-field
                  v-model="password"
                  :rules="passwordRules"
                  type="password"
                  label="Contraseña"
                  required
                ></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-btn class="mr-4" type="submit"> Iniciar Sesion </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'RegisterForm',

  data: function () {
    return {
      valid: false,
      email: '',
      password: '',
      passwordRules: [(v) => !!v || 'Password is required'],
    };
  },

  methods: {
    submitForm() {
      console.log(`
        E-mail: ${this.email}
        Password: ${this.password}
        `);
    },
  },
};
</script>
