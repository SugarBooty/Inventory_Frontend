<template>
  <v-card class="pa-2">
    <v-data-table
      :headers="headers"
      :items="items"
      :items-per-page="5"
    ></v-data-table>
    <v-btn @click="test">Retrieve Database</v-btn>
  </v-card>
</template>

<script>
export default {
  props: {
    items: Array,
  },
  data() {
    return {
      headers: [
        {
          text: "Name",
          align: "start",
          sortable: false,
          value: "name",
        },
        { text: "Description", value: "desc" },
        { text: "Location", value: "location" },
        { text: "Tags", value: "tags" },
      ],
    };
  },
  methods: {
    test() {
      this.$emit("trigger:refresh");
    },
  },
};
</script>
