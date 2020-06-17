<template>
  <v-form @submit.prevent="handleSubmit">
    <v-card class="pa-2">
      <v-card-title>
        Add New Item
        <v-spacer></v-spacer>
        <v-tooltip bottom>
          <template v-slot:activator="{ on, attrs }">
            <v-icon v-bind="attrs" v-on="on">mdi-help-circle-outline</v-icon>
          </template>
          This is the help tooltip
        </v-tooltip>
      </v-card-title>

      <v-card-text>
        <v-layout row wrap>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="item.name"
              class="leftAlign"
              label="Item Name"
              dense
              outlined
            >
            </v-text-field>
          </v-flex>

          <v-spacer></v-spacer>

          <v-flex xs12 sm6>
            <v-combobox
              v-model="item.tags"
              :items="item.tags"
              small-chips
              label="Tags"
              multiple
              single-line
              dense
              outlined
              loading="primary"
              clearable
            ></v-combobox>
          </v-flex>

          <v-flex xs10 sm10>
            <v-text-field
              v-model="item.location"
              label="Location"
              required
              dense
              outlined
            ></v-text-field>
          </v-flex>

          <v-flex xs2>
            <v-text-field
              v-model="item.quantity"
              label="Qty"
              required
              dense
              outlined
            >
            </v-text-field>
          </v-flex>

          <v-flex sm12>
            <v-text-field
              v-model="item.desc"
              label="Description"
              required
              dense
              outlined
            ></v-text-field>
          </v-flex>
        </v-layout>
      </v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn type="submit" color="primary">
          <v-icon left>mdi-check-circle-outline</v-icon>
          Submit
        </v-btn>
        <v-btn @click="clearFields">
          <v-icon left>mdi-backspace-outline</v-icon>
          Clear
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-form>
</template>

<script>
export default {
  name: "add-item-vueify",
  data() {
    return {
      load: true,
      item: {
        name: "",
        desc: "",
        location: "",
        tags: [],
        quantity: "",
      },
      // rules: {
      //   required: (v) => !!v || "Required",
      // },
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("add:item", this.item);
      console.log("in AddItem: ");
      console.log(this.item);
      this.clearFields();
    },

    clearFields() {
      this.item.name = "";
      this.item.desc = "";
      this.item.location = "";
      this.item.tags = [];
      this.item.quantity = "";
    },
  },
};
</script>

<style scoped></style>
