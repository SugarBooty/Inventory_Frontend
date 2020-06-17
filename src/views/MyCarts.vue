<template>
  <v-container>
    <v-content>
      <v-card>
        <v-list>
          <v-list-group
            v-for="list in item_lists_to_be_taken_out"
            :key="list.name"
            v-model="list.active"
            no-action
          >
            <!-- <template v-slot:activator="{ on }">
              <v-list-item-content>
                <v-list-item-title v-text="list.name"></v-list-item-title>
                <v-list-item-subtitle v-text="list.description"></v-list-item-subtitle>
              </v-list-item-content>
            </template>

            <v-item-list
              v-for="cartItem in list.item"
              :key="cartItem.name"

              v-on="on"
            >
              <v-list-item-content>
                <v-list-item-title v-text="cartItem.name"></v-list-item-title>
              </v-list-item-content>
            </v-item-list> -->

          </v-list-group>
        </v-list>
      </v-card>
    </v-content>
  </v-container>
</template>

<script>
export default {
  props: {
    gay: Array,
  },
  data() {
    return {
      item_lists_to_be_taken_out: [
        {
          name: "Fixing Lamp",
          description: "Items I'll need to fix the lamp",
          items: [
            {
              name: "Bulb Socket",
              description: "Standard bulb socket",
              tags: ["lightbulb", "socket", "120v"],
              quantity: 1,
              location: "/workshop/desk/shoebox",
            },
            {
              name: "Philips Head Screwdriver",
              description: "#4 Philips head screwdriver",
              tags: ["#4", "philips", "screwdriver"],
              quantity: 1,
              location: "/workshop/desk/shoebox",
            },
            {
              name: "LED Lightbulb",
              description: "60W eqv. Lightbulb",
              tags: ["LED", "60w", "Lightbulb"],
              quantity: 1,
              location: "/workshop/desk/shoebox",
            },
          ],
        },
        {
          name: "RGB Printer Upgrade",
          description: "Parts to add RGB lighting to the printer",
          items: [
            {
              name: "RGB LED",
              description: "5v RGB LED strips",
              tags: ["5v", "RGB", "LED", "STRIP", "Adhesive_Backed"],
              quantity: 2,
              location: "/workshop/shelf/LED_bin",
            },
          ],
        },
      ],

      item_lists_taken_out: [
        {
          name: "ESP testing",
          description: "Seeing if the ESP was the problem",
          items: [
            {
              name: "ESP8266",
              description: "ESP8266",
              tags: ["ESP8266",
              "microcontroller",
              "wifi"],
              quantity: 1,
              location: "/bedroom/workbench/takeout_bin_1"
            },
          ],
        },
      ],
    };
  },
  methods: {
    printShit() {
      console.log(this.on)
    }
  }
};
</script>
