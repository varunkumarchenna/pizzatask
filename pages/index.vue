<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10">
      <!-- <div class="text-center">
        <logo />
        <vuetify-logo />
      </div> -->
      <v-card
        class="mx-auto"
      >
        <v-img
          src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
          height="200px"
        ></v-img>

        <v-card-title class="headline">
          Welcome to Pizza Palace
        </v-card-title>

        <v-card-subtitle>
          1,000 miles of wonder
        </v-card-subtitle>

        <v-card-actions>
          <v-btn
            color="orange lighten-2"
            nuxt
            to="/orders"
            text
          >
            Orders
          </v-btn>

          <v-spacer></v-spacer>

          <v-btn
            icon
            @click="show = !show"
          >
            <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
          </v-btn>
        </v-card-actions>

        <v-expand-transition>
          <div v-show="show">
            <v-divider></v-divider>

            <v-card-text>
              Please Click on Orders to see the full list of Orders.
            </v-card-text>
          </div>
        </v-expand-transition>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
  export default {
    data: () => ({
      show: false,
    }),
  }
</script>