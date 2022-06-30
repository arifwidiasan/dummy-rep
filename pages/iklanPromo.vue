<template>
  <div>
    <v-row justify="center" align="center" class="mx-5 mt-5">
      <v-col cols="12" sm="8" md="6" lg="4">
        <v-card :loading="loading" class="mx-auto my-12" max-width="374" light>
          <template slot="progress">
            <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
            ></v-progress-linear>
          </template>

          <v-img
            height="250"
            src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
          ></v-img>
          <v-card-title style="justify-content: center"
            >Discount 10%</v-card-title
          >
          <v-divider class="mx-4"></v-divider>
          <v-card-actions style="justify-content: center" light>
            <v-btn color="deep-purple lighten-2" text @click="update">
              Update
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="12" sm="8" md="6" lg="4">
        <v-card :loading="loading" class="mx-auto my-12" max-width="374" light>
          <template slot="progress">
            <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
            ></v-progress-linear>
          </template>

          <v-img
            height="250"
            src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
          ></v-img>
          <v-card-title style="justify-content: center"
            >Discount 10%</v-card-title
          >
          <v-divider class="mx-4"></v-divider>
          <v-card-actions style="justify-content: center">
            <v-btn color="deep-purple lighten-2" text @click="update">
              Update
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="12" sm="8" md="6" lg="4">
        <v-card :loading="loading" class="mx-auto my-12" max-width="374" light>
          <template slot="progress">
            <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
            ></v-progress-linear>
          </template>

          <v-img
            height="250"
            src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
          ></v-img>
          <v-card-title style="justify-content: center"
            >Discount 10%</v-card-title
          >
          <v-divider class="mx-4"></v-divider>
          <v-card-actions style="justify-content: center">
            <v-btn color="deep-purple lighten-2" text @click="update">
              Update
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>
