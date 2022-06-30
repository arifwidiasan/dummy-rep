<template>
  <v-row justify="center" align="center ">
    <v-col cols="12" sm="8" md="6" lg="12">
      <v-card class="pa-5 mt-5 mr-10 ml-10">
        <v-card-title class="headline"> Tambah Produk </v-card-title>
        <v-form>
          <v-container>
            <v-row>
              <v-col cols="12" sm="12">
                <v-text-field
                  label="Nama Produk"
                  placeholder="For example, Dana/Pulsa"
                  outlined
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="12">
                <v-autocomplete
                  ref="country"
                  v-model="country"
                  :rules="[() => !!country || 'This field is required']"
                  :items="countries"
                  label="Tipe Produk"
                  placeholder="Select..."
                  outlined
                  required
                ></v-autocomplete>
              </v-col>
              <v-col cols="12" sm="12">
                <v-autocomplete
                  ref="operator"
                  v-model="operator"
                  :rules="[() => !!operator || 'This field is required']"
                  :items="operators"
                  label="Pilih Operator"
                  placeholder="Select..."
                  outlined
                  required
                ></v-autocomplete>
              </v-col>
              <v-col cols="12" sm="12">
                <v-text-field
                  label="Harga Jual"
                  value="Masukkan Harga Jual"
                  placeholder="For example, 51000"
                  type="number"
                  outlined
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="12">
                <v-text-field
                  label="Stok"
                  value="Masukkan Jumlah Stok"
                  placeholder="For example, 10"
                  type="number"
                  outlined
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <!-- <v-row align="center" justify="space-around" class="mb-5">
              <v-btn color="primary"> Simpan </v-btn>
            </v-row> -->

            <v-row justify="center">
              <v-btn color="primary" dark @click.stop="dialog = true">
                Simpan
              </v-btn>

              <v-dialog v-model="dialog" max-width="290">
                <v-card>
                  <v-card-title class="text-h5"> Selamat </v-card-title>

                  <v-card-text> Anda berhasil Menambahkan Produk! </v-card-text>

                  <v-card-actions>
                    <v-spacer></v-spacer>

                    <v-btn color="green darken-1" text @click="dialog = false">
                      Close
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',
  data: () => ({
    countries: [
      'E-Wallet',
      'Paket Data',
      'Pascabayar',
      'Pulsa',
      'Token Listrik',
    ],
    operators: [
      'Gojek',
      'Indosat Ooredo Hutchsion',
      'PLN',
      'Shopee',
      'Smartfren',
      'XL Axiata',
    ],
    errorMessages: '',
    name: null,
    address: null,
    city: null,
    state: null,
    zip: null,
    country: null,
    formHasErrors: false,
    dialog: false,
  }),
}
</script>
