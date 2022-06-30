<template>
  <div>
    <v-card class="mt-5 mx-7 mb-7" light>
      <v-row class="mr-15 mt-5">
        <v-col cols="1"></v-col>
        <v-col cols="10" class="d-flex justify-end mb-5 pr-16 mt-10">
          <v-btn depressed color="primary"> Tambah Metode Pembayaran </v-btn>
        </v-col>
      </v-row>
      <v-row class="ml-5 mt-1">
        <v-col cols="1"></v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/Bank1.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/Bank2.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <v-row class="ml-5 mt-7">
        <v-col cols="1"></v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/Bank3.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/Bank4.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <v-row class="ml-5 mt-1">
        <v-col cols="1"></v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/Merchant1.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/Merchant2.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <v-row class="ml-5 mt-1">
        <v-col cols="1"></v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/VirtualWallet1.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
        <v-col cols="5">
          <v-row class="pa-5">
            <v-col cols="7">
              <img src="../assets/img/VirtualWallet2.png" alt="" width="100" />
              <p>Bank Central Asia</p>
            </v-col>
            <v-col cols="5">
              <v-switch v-model="switchProcces"></v-switch>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  methods: {
    tambahPembayaran() {
      // eslint-disable-next-line no-console
      console.log('tambah pembayaran')
    },
  },
}
</script>
