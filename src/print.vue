<template>
  <v-card flat height="100%">
    <v-toolbar dense>
      <div class="body-2">Print Stuff</div>
      <v-spacer></v-spacer>
      <v-btn small color="primary" @click="printSection">
        <v-icon small class="mr-1">print</v-icon>Print
      </v-btn>
    </v-toolbar>
    <v-flex xs12>
      <div id="printSection">
        <span v-html="printStuff"></span>
      </div>
    </v-flex>
  </v-card>
</template>

<script>
export default {
  methods: {
    ...mapActions("myModule", ["fetchPrintStuff"]),

    printSection() {
      this.$htmlToPaper("printSection");
    },
  },

  mounted() {
    this.fetchPrintStuff();

    // a Vuex action to get stuff to print from server
  },
};
</script>
