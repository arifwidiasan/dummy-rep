<template>
  <v-row justify="center" align="center ">
    <v-col cols="12" sm="8" md="6" lg="12">
      <v-card class="pa-5 mt-5 mr-10 ml-10" style="background-color: #6b4bcc">
        <v-row>
          <v-col cols="9">
            <v-card-title class="headline">
              Selamat datang kembali, Eirene!
            </v-card-title>
            <v-card-text>
              <p>
                Anda login sebagai Admin, Silahkan sesuaikan dengan kebutuhanmu
                agar segera rilis ke tampilan User Aplikasi
                <strong> Upay! </strong>
              </p>
            </v-card-text>
          </v-col>
          <v-col cols="3">
            <img src="../assets/img/emo1.png" width="200" />
          </v-col>
        </v-row>
      </v-card>

      <v-row justify="center" align="center" class="mt-5 mr-7 ml-7">
        <v-col xs="12" sm="12" md="6" lg="3">
          <v-card class="pa-5 text-center" style="background-color: #4c3a51">
            <h4>Rp.2.528.000</h4>
            <p>Pemasukan Minggu Ini</p>
          </v-card>
        </v-col>
        <v-col xs="12" sm="12" md="6" lg="3">
          <v-card class="pa-5 text-center" style="background-color: #df7861">
            <h4>Rp.573.000</h4>
            <p>Total Keuntungan</p>
          </v-card>
        </v-col>
        <v-col xs="12" sm="12" md="6" lg="3">
          <v-card class="pa-5 text-center" style="background-color: #774360">
            <h4>1802</h4>
            <p>Member Terdaftar</p>
          </v-card>
        </v-col>
        <v-col xs="12" sm="12" md="6" lg="3">
          <v-card class="pa-5 text-center" style="background-color: #b25068">
            <h4>23</h4>
            <p>Member Baru</p>
          </v-card>
        </v-col>
      </v-row>

      <v-row justify="center" align="center" class="mt-8 mr-7 ml-16 mb-10 pl-5">
        <img src="../assets/img/Statistik.png" width="1050" />
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>
