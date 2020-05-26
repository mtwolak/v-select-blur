<template>
  <v-app>
    <v-content>
        <v-select
        :value="selectedFruits"
        :items="fruits"
        label="Favorite Fruits"
        multiple
        @blur="onBlur"
        >
        <template v-slot:prepend-item>
            <v-list-item
            ripple
            @click="toggle"
            >
            <v-list-item-content>
                <v-list-item-title>Select All</v-list-item-title>
            </v-list-item-content>
            </v-list-item>
        </template>
        </v-select>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
      fruits: [
        'Apples',
        'Apricots',
      ],
      selectedFruits: [],
    }),

    computed: {
      likesAllFruit () {
        return this.selectedFruits.length === this.fruits.length
      },
    },
    methods: {
        onBlur() {
            console.log("Blur")
        },
      toggle () {
        this.$nextTick(() => {
          if (this.likesAllFruit) {
            this.selectedFruits = []
          } else {
            this.selectedFruits = this.fruits.slice()
          }
        })
      },
    },
};
</script>
