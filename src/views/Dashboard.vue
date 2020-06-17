<template>
  <v-container>
    <v-content>
      <v-layout row wrap>
        <v-flex xs12 sm6>
          <SearchVuetify class="ma-2" />
        </v-flex>

        <v-flex xs12 sm6>
          <AddItemVuetify class="ma-2" @add:item="addItem" />
        </v-flex>

        <v-flex sm12>
          <ItemListVuetify
            class="ma-2"
            :items="items"
            @trigger:refresh="getList"
          />
        </v-flex>
      </v-layout>
    </v-content>
  </v-container>
</template>

<script>
import AddItemVuetify from "@/components/AddItemVuetify.vue";
import SearchVuetify from "@/components/SearchVuetify.vue";
import ItemListVuetify from "@/components/ItemListVuetify.vue";

export default {
  name: "Dashboard",

  components: {
    AddItemVuetify,
    SearchVuetify,
    ItemListVuetify,
  },
  data() {
    return {
      items: [],
    };
  },
  methods: {
    addItem(item) {
      console.log("In Dashboard: ");
      console.log(item);
    },
    async getList() {
      const data = await fetch("http://192.168.1.24:5025/api/allitems");
      const dataJSON = await data.json();
      console.log(dataJSON.items);
      this.items = [];
      for (let item of dataJSON.items) {
        this.items.push(item);
      }
    },
  },
};
</script>

<style scoped></style>
