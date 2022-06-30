<template>
  <v-container>
    <v-card class="ml-5 mr-5" light flat>
      <v-card-title class="headline ml-2">
        <strong> Invoice </strong>
      </v-card-title>

      <v-data-table
        :headers="headers"
        :items="products"
        sort-by="calories"
        class="elevation-1 mx-5 text-center"
        light
      >
        <template #top>
          <v-dialog v-model="dialog" max-width="500px">
            <v-card>
              <v-card-title>
                <span class="text-h5">{{ formTitle }}</span>
              </v-card-title>

              <v-card-text>
                <v-container>
                  <v-row>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field
                        v-model="editedItem.code"
                        label="ID Transaksi"
                        readonly
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field
                        v-model="editedItem.paymentMethod"
                        label="Metode Pembayaran"
                        readonly
                      ></v-text-field>
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col cols="12" sm="6" md="4" lg="12">
                      <v-text-field
                        v-model="editedItem.numberVA"
                        label="Virtual Account"
                        readonly
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
                <v-btn color="blue darken-1" text @click="save">
                  SEND INVOICE
                </v-btn>
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
        </template>
        <template #[`item.actions`]="{ item }">
          <!-- <v-icon small class="mr-2" @click="generateVA(item)">
            mdi-pencil
          </v-icon>
          <v-icon small @click="deleteItem(item)"> mdi-delete </v-icon> -->
          <v-btn small color="primary" @click="generateVA(item)">
            Generate VA
          </v-btn>
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
        text: 'ID Transaksi',
        align: 'start',
        sortable: false,
        value: 'code',
      },
      { text: 'Kode Produk', value: 'name' },
      { text: 'Nama Produk', value: 'typeProduct' },
      { text: 'Harga', value: 'operator' },
      { text: 'Jumlah', value: 'price' },
      { text: 'Metode Pembayaran', value: 'paymentMethod' },
      { text: 'Aksi', value: 'actions', sortable: false },
    ],
    products: [],
    editedIndex: -1,
    editedItem: {
      code: '',
      name: 0,
      typeProduct: 0,
      operator: 65,
      price: 0,
      paymentMethod: 0,
      numberVA: '',
    },
    defaultItem: {
      code: '',
      name: 0,
      typeProduct: 0,

      operator: 65,
      price: 0,
      paymentMethod: 0,
    },
  }),

  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'New Item' : 'Generate Virtual Account'
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
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Ice cream sandwich',
          code: 'AB237',
          typeProduct: 'Pulsa',
          operator: 'Gojek',
          price: 37000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Eclair',
          code: 'AB262',
          typeProduct: 'E-Wallet',
          operator: 'PLN',
          price: 23000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Cupcake',
          code: 'AB305',
          typeProduct: 'Pulsa',
          operator: 'Telkomsel',
          price: 67000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Gingerbread',
          code: 'AB356',
          typeProduct: 'Token Listrik',
          operator: 'Shopee',
          price: 49000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Jelly bean',
          code: 'AB375',
          typeProduct: 'Token Listrik',
          operator: 'PLN',
          price: 94000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Lollipop',
          code: 'AB392',
          typeProduct: 'Pulsa',
          operator: 'Gojek',
          price: 98000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Honeycomb',
          code: 'AB408',
          typeProduct: 'E-Wallet',
          operator: 'Shopee',
          price: 87000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'Donut',
          code: 'AB452',
          typeProduct: 'E-Wallet',
          operator: 'Smartfren',
          price: 51000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
        {
          name: 'KitKat',
          code: 'AB518',
          typeProduct: 'Token Listrik',
          operator: 'PLN',
          price: 65000,
          paymentMethod: 'BRI',
          numberVA: '7810202001539202',
        },
      ]
    },

    generateVA(item) {
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
