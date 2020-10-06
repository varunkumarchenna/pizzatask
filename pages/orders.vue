<template>
  <v-card
    class="mx-auto"
  >
    <v-toolbar
      color="pink"
      dark
    >
      <v-toolbar-title>Orders</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn text @click="reset()">
        Reset
      </v-btn>
    </v-toolbar>

    <v-list two-line>
        <template v-for="(item, index) in items">
          <v-list-item :key="item.title">
              <v-list-item-content>
                <v-list-item-title v-text="item.title"></v-list-item-title>

                <v-list-item-subtitle
                  class="text--primary"
                >No. of Pizzas {{item.itemCount}}</v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-content>
                <v-list-item-subtitle v-text="'Total Bill: '+item.total"></v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-content>
                <v-btn color="deep-orange" dark v-if="item.status=='Order Received'" @click="changeStatus(item)">Change Status</v-btn>
                <v-btn color="cyan" dark v-if="item.status=='Preparing Order'" @click="changeStatus(item)">Change Status</v-btn>
              </v-list-item-content>

              <v-list-item-action>
                <v-list-item-action-text v-text="item.status"></v-list-item-action-text>

                <v-icon
                  v-if="item.status=='Order Received'"
                  color="red darken-1"
                >
                  mdi-tag
                </v-icon>

                <v-icon
                  v-if="item.status=='Preparing Order'"
                  color="orange darken-3"
                >
                  mdi-run
                </v-icon>
                <v-icon
                  v-if="item.status=='Ready to serve'"
                  color="green darken-3"
                >
                  mdi-silverware-fork-knife
                </v-icon>
              </v-list-item-action>
          </v-list-item>

          <v-divider
            v-if="index < items.length - 1"
            :key="index"
          ></v-divider>
        </template>
    </v-list>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
      selected: [2],
      items: [
        {
          total: '₹ 150',
          itemCount: 1,
          status: "Ready to serve",
          title: 'Ali Connors',
        },
        {
          total: '₹ 250',
          itemCount: 2,
          status: "Order Received",
          title: 'Scrott',
        },
        {
          total: '₹ 1250',
          itemCount: 4,
          status: 'Order Received',
          title: 'Sandra Adams',
        },
        {
          total: '₹ 2120',
          itemCount: 8,
          status: 'Preparing Order',
          title: 'Trevor Hansen',
        },
        {
          total: '₹ 195',
          itemCount: 3,
          status: "Ready to serve",
          title: 'Britta Holt',
        },
      ],
    }),
    methods: {
      changeStatus(item){
        if(item.status=='Order Received')
          item.status = 'Preparing Order'
        else
          item.status = 'Ready to serve'
        console.log({item})
      },
      reset(){ // reset all orders
        this.items.forEach(item=>{
          item.status = 'Order Received'
        })
      }
    }
  }
</script>