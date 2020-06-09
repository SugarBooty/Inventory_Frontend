<template>
  <v-form @submit.prevent="handleSubmit">
    <v-card class="pa-2">
      <v-card-title>Add New Item</v-card-title>

      <v-card-text>
        <v-layout row wrap>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="item.name"
              class="leftAlign"
              label="Item Name"
              :rules="required"
              dense
              outlined
            >
            </v-text-field>
          </v-flex>

          <v-spacer></v-spacer>

          <v-flex xs12 sm6>
            <v-text-field
              v-model="item.tags"
              label="Tags"
              required
              dense
              outlined
            ></v-text-field>
          </v-flex>

          <v-flex sm12>
            <v-text-field
              v-model="item.location"
              label="Location"
              required
              dense
              outlined
            ></v-text-field>
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
          <v-icon class="mr-1">mdi-check-circle-outline</v-icon>
          Submit
        </v-btn>
        <v-btn @click="clearFields">
          <v-icon class="mr-1">mdi-backspace-outline</v-icon>
          Clear
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-form>
</template>

<script>
//   export default {
//      return item: {
//           name: '',
//           description: '',
//           location: '',
//           type: '',
//       },
//       nameRules: [
//         v => !!v || 'Name is required',
//       ],
//     },
//   }

export default {
  name: "add-item-vueify",
  data() {
    // nameRules: [
    //     v => !!v || 'Field is required!'
    // ]
    return {
      item: {
        name: "",
        desc: "",
        location: "",
        tags: [],
      },
      rules: {
        required: (v) => !!v || "Required",
      },
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("add:item", this.item);
      this.clearFields();
    },
    clearFields() {
      this.item.name = "";
      this.item.desc = "";
      this.item.location = "";
      this.item.tags = [];
    },
  },
};
</script>

<style scoped></style>
