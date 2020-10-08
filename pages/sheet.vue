<template>
  <div>
    <v-card class="mx-auto pa-4" elevation="11">
      <h3>ลงทะเบียนร้าน</h3>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-row>
          <v-col cols="8">
            <v-text-field
              v-model="name"
              :rules="nameRules"
              label="ชื่อร้าน"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="4">
            <v-select
              v-model="genre"
              :rules="nameRules"
              :items="items"
              label="ประเภทร้าน"
              required
            ></v-select>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="11" sm="5">
            <v-menu
              ref="menu"
              v-model="menu2"
              :rules="nameRules"
              :close-on-content-click="false"
              :nudge-right="40"
              :return-value.sync="opentime"
              transition="scale-transition"
              offset-y
              max-width="290px"
              min-width="290px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="opentime"
                  :rules="nameRules"
                  label="Open"
                  prepend-icon="mdi-clock-time-four-outline"
                  readonly
                  required
                  v-bind="attrs"
                  v-on="on"
                ></v-text-field>
              </template>
              <v-time-picker
                v-if="menu2"
                v-model="opentime"
                full-width
                @click:minute="$refs.menu.save(opentime)"
              ></v-time-picker>
            </v-menu>
          </v-col>

          <v-col cols="11" sm="5">
            <v-menu
              ref="menu1"
              v-model="menu1"
              :close-on-content-click="false"
              :nudge-right="40"
              :return-value.sync="closetime"
              transition="scale-transition"
              offset-y
              max-width="290px"
              min-width="290px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="closetime"
                  :rules="nameRules"
                  label="Close"
                  prepend-icon="mdi-clock-time-four-outline"
                  readonly
                  required
                  v-bind="attrs"
                  v-on="on"
                ></v-text-field>
              </template>
              <v-time-picker
                v-if="menu1"
                v-model="closetime"
                full-width
                @click:minute="$refs.menu1.save(closetime)"
              ></v-time-picker>
            </v-menu>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="4">
            <v-text-field
              v-model="phone"
              :rules="nameRules"
              label="เบอร์โทร"
              prepend-icon="mdi-cellphone"
              required
            >
              icon="mdi-cellphone"
            </v-text-field>
          </v-col>
        </v-row>
        <v-divider></v-divider>
        <v-row>
          <v-col cols="6">
            <v-textarea
              v-model="add"
              :rules="nameRules"
              name="input-7-1"
              label="ที่อยู่ร้าน"
              required
            ></v-textarea>
          </v-col>
          <v-col cols="6">
            <v-text-field
              v-model="sub_district"
              :rules="nameRules"
              name="input-7-1"
              label="ตำบล/แขวง"
              required
            ></v-text-field>
            <v-text-field
              v-model="district"
              :rules="nameRules"
              name="input-7-1"
              label="อำเภอ/เขต"
              required
            ></v-text-field>
            <v-text-field
              v-model="province"
              :rules="nameRules"
              name="input-7-1"
              label="จังหวัด"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="6"> </v-col>
        </v-row>
        <v-divider></v-divider>

        <v-row>
          <v-col cols="10"> </v-col>
          <v-col cols="2">
            <div class="text-center">
              <v-dialog v-model="dialog" width="800">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    :disabled="!valid"
                    v-bind="attrs"
                    color="primary"
                    nuxt
                    to="/inspire"
                    v-on="on"
                    @click="validate"
                  >
                    SUMMIT
                  </v-btn>
                </template>
              </v-dialog>
            </div>
          </v-col>
        </v-row>
      </v-form>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: null,
      phone: '',
      add: '',
      Address: {},
      genre: '',
      items: ['ร้านอาหาร', 'ร้านขนม', 'ร้านกาแฟ', 'สถานบันเทิง', 'อื่นๆ'],
      arr: {},
      description: '',
      opentime: '',
      closetime: '',
      menu1: false,
      menu2: false,
      sub_district: '',
      district: '',
      province: '',
      dialog: false,
      nameRules: [(v) => !!v || 'please required'],
      valid: true,
    }
  },
  methods: {
    reset() {
      this.$refs.form.reset()
    },
    validate() {
      this.$refs.form.validate()
    },
    set() {
      this.arr = {
        name: this.name,
        genre: this.genre,
        phone: this.phone,
        address: {
          add: this.add,
          sub_district: this.sub_district,
          district: this.district,
          province: this.province,
        },
        description: this.description,
        open: this.opentime,
        close: this.closetime,
        sub_district: this.sub_district,
        district: this.district,
        province: this.province,
      }
      this.$store.commit('set_arr', this.arr)
    },
  },
}
</script>
