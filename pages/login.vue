<template>
  <div>
    <img
      src="../assets/img/logo.png"
      width="100"
      style="margin-left: 130px; margin-top: 20px"
    />
    <v-row justify="center" style="margin-top: 120px; margin-left: 100px">
      <v-col cols="4">
        <v-card
          ref="form"
          light
          flat
          style="background-color: transparent !important"
        >
          <v-card-title style="margin-left: 100px">
            <h4>LOGIN ADMIN</h4>
          </v-card-title>
          <v-card-text>
            <v-form>
              <v-text-field
                ref="Username"
                v-model="login.username"
                label="Username"
                placeholder="Masukkan Username"
                prepend-icon="mdi-account-circle"
              ></v-text-field>
              <v-text-field
                ref="Password"
                v-model="login.password"
                label="Password"
                :type="showPassword ? 'text' : 'password'"
                placeholder="Masukkan Password"
                prepend-icon="mdi-lock"
                :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                @click:append="tampilPassword"
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <!--  <v-btn text> Cancel </v-btn> -->
            <!--             <v-spacer></v-spacer>
            <v-slide-x-reverse-transition>
              <v-tooltip v-if="formHasErrors" left>
                <template #activator="{ on, attrs }">
                  <v-btn
                    icon
                    class="my-0"
                    v-bind="attrs"
                    @click="resetForm"
                    v-on="on"
                  >
                    <v-icon>mdi-refresh</v-icon>
                  </v-btn>
                </template>
                <span>Refresh form</span>
              </v-tooltip>
            </v-slide-x-reverse-transition> -->
            <v-btn block dark style="background-color: blue" @click="userLogin">
              <strong>Login</strong>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="5" style="margin-left: 150px">
        <img src="../assets/img/illustration1.png" width="450" />
      </v-col>
    </v-row>

    <!-- <v-app dark>
               <v-row class="mt-16">
        <v-col cols="2"></v-col>
        <v-col cols="4">
          <v-img
            class="white--text align-end"
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
          >
          </v-img>
        </v-col>
        <v-col cols="4">
          <h2>form</h2>
          <form>
            <v-text-field
              v-model="name"
              :error-messages="nameErrors"
              label="Username"
              required
              @input="$v.name.$touch()"
              @blur="$v.name.$touch()"
            ></v-text-field>
            

            <v-btn class="mr-4" @click="submit"> submit </v-btn>
            <v-btn @click="clear"> clear </v-btn>
          </form>
        </v-col>
        <v-col cols="2"></v-col>
      </v-row>
    
    </v-app> -->
  </div>
</template>

<script>
export default {
  name: 'LoginPage',
  layout: 'loginDefault',
  data() {
    return {
      showPassword: false,
      login: {
        username: '',
        password: '',
      },
    }
  },
  methods: {
    tampilPassword() {
      this.showPassword = !this.showPassword
    },
    async userLogin() {
      try {
        const response = await this.$auth.loginWith('local', {
          data: this.login,
        })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    },
  },
}
</script>
<style>
html {
  font-family: 'Poppins', sans-serif;
}
</style>
