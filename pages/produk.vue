<template>
  <v-container class="pa-0">
    <v-card
      class="ml-5 mr-5 pb-5 pt-0"
      style="background-color: transparent !important"
      light
      flat
    >
      <v-card-title class="headline ml-2 pt-0">
        <strong> Daftar Produk </strong>
      </v-card-title>

      <v-data-table
        :headers="headers"
        :items="products"
        :search="search"
        sort-by="calories"
        class="pl-5 pr-5"
      >
        <template #top>
          <v-toolbar flat>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              rounded-lg
              dark
              single-line
              hide-details
              style="background-color: #2196f3; max-width: fit-content"
              class="pl-3 pr-3 pb-1 rounded-lg"
            ></v-text-field>
            <v-spacer></v-spacer>
            <v-dialog v-model="dialog" max-width="600px">
              <template #activator="{ on, attrs }">
                <v-btn
                  :to="{ name: 'addProduct' }"
                  style="background-color: #2196f3"
                  dark
                  class="mb-2"
                  v-bind="attrs"
                  v-on="on"
                >
                  Tambah Produk
                </v-btn>
              </template>
              <v-card>
                <v-card-title>
                  <span class="text-h5">{{ formTitle }}</span>
                </v-card-title>

                <v-card-text>
                  <v-container>
                    <v-row>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.name"
                          label="Nama Produk"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.typeProduct"
                          label="Tipe Produk"
                        ></v-text-field>
                        <!-- <v-autocomplete
                          ref="country"
                          v-model="editedItem.typeProduct"
                          :rules="[() => !!country || 'This field is required']"
                          :items="countries"
                          label="Tipe Produk"
                          placeholder="Select..."
                          outlined
                          required
                        ></v-autocomplete> -->
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.operator"
                          label="Nama Operator"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.price"
                          label="Harga Jual"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.stok"
                          label="Stok"
                        ></v-text-field>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card-text>

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="blue darken-1" text @click="close">
                    Cancel
                  </v-btn>
                  <v-btn color="blue darken-1" text @click="save"> Save </v-btn>
                  <!-- <v-dialog v-model="save" max-width="290">
                    <v-card>
                      <v-card-title class="text-h5"> Selamat </v-card-title>

                      <v-card-text> Anda berhasil Edit Produk! </v-card-text>

                      <v-card-actions>
                        <v-spacer></v-spacer>

                        <v-btn
                          color="green darken-1"
                          text
                          @click="dialog = false"
                        >
                          Close
                        </v-btn>
                      </v-card-actions>
                    </v-card>
                  </v-dialog> -->
                </v-card-actions>
              </v-card>
            </v-dialog>
            <v-dialog v-model="dialogDelete" max-width="500px">
              <v-card>
                <v-card-title class="text-subtitle-1"
                  >Apakah Anda yakin ingin menghapus product ?</v-card-title
                >
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="blue darken-1" text @click="closeDelete"
                    >Cancel</v-btn
                  >
                  <v-btn color="blue darken-1" text @click="deleteItemConfirm"
                    >OK</v-btn
                  >
                  <v-spacer></v-spacer>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-toolbar>
        </template>
        <template #[`item.actions`]="{ item }">
          <v-icon small class="mr-2" @click="editItem(item)">
            mdi-pencil
          </v-icon>
          <v-icon small @click="deleteItem(item)"> mdi-delete </v-icon>
        </template>
        <template #no-data>
          <v-btn color="primary" @click="initialize"> Reset </v-btn>
        </template>
      </v-data-table>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'IndexPage',
  data: () => ({
    search: '',
    dialog: false,
    // simpan: false,
    dialogDelete: false,
    headers: [
      {
        text: 'Kode Produk',
        align: 'start',
        sortable: false,
        value: 'code',
        class: 'blue',
      },
      { text: 'Nama Produk', value: 'name', class: 'blue' },
      { text: 'Tipe Produk', value: 'typeProduct', class: 'blue' },
      { text: 'Operator', value: 'operator', class: 'blue' },
      { text: 'Harga Jual', value: 'price', class: 'blue' },
      { text: 'Stok', value: 'stok', class: 'blue' },
      { text: 'Actions', value: 'actions', sortable: false, class: 'blue' },
    ],
    products: [],
    editedIndex: -1,
    editedItem: {
      code: '',
      name: 0,
      typeProduct: 0,
      operator: 65,
      price: 0,
      stok: 0,
    },
    defaultItem: {
      code: '',
      name: 0,
      typeProduct: 0,

      operator: 65,
      price: 0,
      stok: 0,
    },
  }),

  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'New Item' : 'Edit Produk'
    },
  },

  watch: {
    dialog(val) {
      val || this.close()
    },
    dialogDelete(val) {
      val || this.closeDelete()
    },
  },

  created() {
    this.initialize()
  },

  methods: {
    initialize() {
      this.products = [
        {
          name: 'Frozen Yogurt',
          code: 'AB159',
          typeProduct: 'Token Listrik',
          operator: 'Gojek',
          price: 24000,
          stok: 4,
        },
        {
          name: 'Ice cream sandwich',
          code: 'AB237',
          typeProduct: 'Pulsa',
          operator: 'Gojek',
          price: 37000,
          stok: 4,
        },
        {
          name: 'Eclair',
          code: 'AB262',
          typeProduct: 'E-Wallet',
          operator: 'PLN',
          price: 23000,
          stok: 6,
        },
        {
          name: 'Cupcake',
          code: 'AB305',
          typeProduct: 'Pulsa',
          operator: 'Telkomsel',
          price: 67000,
          stok: 4,
        },
        {
          name: 'Gingerbread',
          code: 'AB356',
          typeProduct: 'Token Listrik',
          operator: 'Shopee',
          price: 49000,
          stok: 3,
        },
        {
          name: 'Jelly bean',
          code: 'AB375',
          typeProduct: 'Token Listrik',
          operator: 'PLN',
          price: 94000,
          stok: 0,
        },
        {
          name: 'Lollipop',
          code: 'AB392',
          typeProduct: 'Pulsa',
          operator: 'Gojek',
          price: 98000,
          stok: 0,
        },
        {
          name: 'Honeycomb',
          code: 'AB408',
          typeProduct: 'E-Wallet',
          operator: 'Shopee',
          price: 87000,
          stok: 6,
        },
        {
          name: 'Donut',
          code: 'AB452',
          typeProduct: 'E-Wallet',
          operator: 'Smartfren',
          price: 51000,
          stok: 5,
        },
        {
          name: 'KitKat',
          code: 'AB518',
          typeProduct: 'Token Listrik',
          operator: 'PLN',
          price: 65000,
          stok: 7,
        },
      ]
    },

    editItem(item) {
      this.editedIndex = this.products.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem(item) {
      this.editedIndex = this.products.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialogDelete = true
    },

    deleteItemConfirm() {
      this.products.splice(this.editedIndex, 1)
      this.closeDelete()
    },

    close() {
      this.dialog = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    closeDelete() {
      this.dialogDelete = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    save() {
      if (this.editedIndex > -1) {
        Object.assign(this.products[this.editedIndex], this.editedItem)
        setTimeout(() => {
          alert('Anda Berhasil Update Produk!!')
        }, 100)
      } else {
        this.products.push(this.editedItem)
      }
      this.close()
    },
  },
}
</script>
