<template>
  <div>
    <v-card class="pa-2">
      <form>
        <v-card-title>
          Search
          <v-spacer></v-spacer>
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-icon v-bind="attrs" v-on="on" >mdi-help-circle-outline</v-icon>
            </template>
            This is the help tooltip
          </v-tooltip>
        </v-card-title>

        <v-card-text>
          <v-text-field
            v-model="search.nameFilter"
            :disabled="isDisabled.name"
            :v-on-lazy="updateSearchButton()"
            label="Name"
            dense
            outlined
          ></v-text-field>

          <v-text-field
            v-model="search.tagFilter"
            :disabled="isDisabled.tags"
            :v-on-lazy="updateSearchButton()"
            label="Tags"
            dense
            outlined
          ></v-text-field>

          <v-text-field
            v-model="search.locationFilter"
            :disabled="isDisabled.location"
            :v-on-lazy="updateSearchButton()"
            label="Location"
            dense
            outlined
          ></v-text-field>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" :disabled="isDisabled.search">
            <v-icon class="mr-1">{{ searchButton.icon }}</v-icon>
            {{ searchButton.text }}
          </v-btn>
          <v-btn :disabled="isDisabled.clear" @click="clearFields">
            <v-icon class="mr-1">mdi-backspace-outline</v-icon>
            Clear
          </v-btn>
        </v-card-actions>
      </form>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "search-vuetify",
  data() {
    return {
      searchButton: {
        text: "search",
        icon: "mdi-magnify",
      },

      isDisabled: {
        name: false,
        tags: false,
        location: false,
        search: false,
        clear: false,
      },

      search: {
        nameFilter: "",
        locationFilter: "",
        tagFilter: "",
      },
    };
  },
  methods: {
    clearFields() {
      console.log("Inside clearFields");
      for (let field in this.isDisabled) {
        field = !field;
        console.log(field);
      }
      this.searchButton.text = "ur gay";
      this.updateSearchButton();
    },
    updateSearchButton() {
      // changes the "Search" text to "Location"
      console.log("Hone, I'm home!");
      if (
        (this.search.locationFilter != "") &
        (this.search.tagFilter == "") &
        (this.search.nameFilter == "")
      ) {
        this.searchButton.text = "View Location";
        this.searchButton.icon = "mdi-format-list-bulleted";
      } else {
        this.searchButton.text = "Search";
        this.searchButton.icon = "mdi-magnify";
      }
    },
  },
};
</script>

<style scoped></style>
