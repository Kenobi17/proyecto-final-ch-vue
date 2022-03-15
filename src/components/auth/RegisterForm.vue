<template>
  <v-container>
    <v-row>
      <v-col cols="6">
        <h1>Registro</h1>
        <v-form v-model="valid" ref="form" @submit.prevent="submitForm">
          <v-row>
            <v-col cols="12">
              <v-text-field
                v-model="firstname"
                :rules="nameRules"
                label="Nombre"
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12">
              <v-text-field
                v-model="lastname"
                :rules="nameRules"
                label="Apellido"
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12">
              <v-text-field
                v-model="email"
                :rules="emailRules"
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
              <v-text-field
                v-model="repeatedPassword"
                :rules="repeatedPasswordRules"
                type="password"
                label="Repetir contraseña"
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12">
              <v-btn class="mr-4" type="submit"> Registrarse </v-btn>
            </v-col>
          </v-row>
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
      firstname: '',
      lastname: '',
      nameRules: [(v) => !!v || 'Name is required'],
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
      password: '',
      passwordRules: [
        (v) => !!v || 'Password is required',
        (v) => v.length >= 6 || 'Password must be at least 6 characters',
      ],
      repeatedPassword: '',
      repeatedPasswordRules: [
        (v) => !!v || 'Password is required',
        (v) => v.length >= 6 || 'Password must be at least 6 characters',
        (v) => v === this.password || 'Passwords must match',
      ],
    };
  },

  methods: {
    submitForm() {
      console.log(`
        First name: ${this.firstname}
        Last name: ${this.lastname}
        E-mail: ${this.email}
        Password: ${this.password}
        Repeat password: ${this.repeatedPassword}
        `);
    },
  },
};
</script>
