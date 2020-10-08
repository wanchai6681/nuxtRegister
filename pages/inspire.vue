<template>
  <v-card :loading="loading" class="mx-auto my-12" max-width="374">
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      src="https://scontent.fcnx3-1.fna.fbcdn.net/v/t1.0-9/49121565_1091418274372155_4646027674983071744_o.png?_nc_cat=104&_nc_sid=09cbfe&_nc_eui2=AeELlXCFuHZ_Z4-1imimzh_VNu1DO9zhMws27UM73OEzC3SwQQd-kALR210cPD4svx1sIFg7gf7-q8pSLEyI5osz&_nc_ohc=0r1HM24-e94AX-tnJup&_nc_ht=scontent.fcnx3-1.fna&oh=8ff5b91fc9b707de923ec3b08cb4c500&oe=5FA2F4C1"
    ></v-img>

    <v-card-title>CSMJU Studio</v-card-title>

    <v-card-text>
      <v-row align="center" class="mx-0">
        <v-rating
          :value="5"
          color="amber"
          dense
          half-increments
          readonly
          size="14"
        ></v-rating>

        <div class="grey--text ml-4">5 (413)</div>
      </v-row>

      <div class="my-4 subtitle-1">$ • STUDIO, CSMJU Shop</div>

      <!--<div>
        Small plates, salads & sandwiches - an intimate setting with 12 indoor
        seats plus patio seating.
      </div>-->
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-text>
      <v-chip-group
        v-model="selection"
        active-class="deep-purple accent-4 white--text"
        column
      >
        <v-chip>8:30น.</v-chip>

        <v-chip>11:30น.</v-chip>

        <v-chip>15:00น.</v-chip>

        <v-chip>17:00น.</v-chip>
      </v-chip-group>
    </v-card-text>

    <v-card-actions>
      <v-btn color="deep-purple lighten-2" text @click="reserve">
        Reserve
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    loading: false,
    selection: 1,
  }),
  methods: {
    reserve() {
      this.loading = true
      setTimeout(() => (this.loading = false), 2000)
    },
  },
}
</script>
