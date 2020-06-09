<template>
  <div>
    <v-card class="pa-2">
      <v-card-title>Search</v-card-title>

      <v-card-text>
        <v-text-field
          v-model="search"
          label="Search"
          dense
          outlined
        ></v-text-field>

        <v-text-field
          v-model="tagFilter"
          label="Tags"
          dense
          outlined
        ></v-text-field>

        <v-text-field
          v-model="locationFilter"
          label="Location"
          dense
          outlined
        ></v-text-field>
      </v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="primary">
          <v-icon class="mr-1">mdi-format-list-bulleted-square</v-icon>
          List Location
        </v-btn>
        <v-btn color="primary">
          <v-icon class="mr-1">mdi-magnify</v-icon>
          Search
        </v-btn>
        <v-btn>
          <v-icon class="mr-1">mdi-backspace-outline</v-icon>
          Clear
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "search-vuetify",
};
</script>

<style scoped></style>
