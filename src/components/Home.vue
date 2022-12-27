<template>
  <v-container>
    <v-menu
        v-model="showMenu"
        absolute
        offset-y
        style="max-width: 600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
            v-bind="attrs"
            v-on="on"
            class="buy-options"
            color="green darken-2"
            dark
        >
          <v-icon
              dark
              x-large
              color="black"
          >
            mdi-cart-outline
          </v-icon>
        </v-btn>
      </template>

      <v-list>
        <v-list-item
            v-for="(item, index) in items"
            :key="index"
        >
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  <v-card
      class="mx-auto my-12"
      max-width="374"
  >
    <template slot="progress">
      <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
      ></v-progress-linear>
    </template>

    <Carousel></Carousel>

    <v-card-title>Das geilste Produkt</v-card-title>

    <v-card-text>
      <v-row
          align="center"
          class="mx-0"
      >
      <Rating></Rating>

        <div class="grey--text ms-4">
          4.5 (413)
        </div>
      </v-row>

      <div class="my-4 text-subtitle-1">
        99,99 €
      </div>

      <div>Dieses Produkt überzeugt durch seine Lässigkeit. Wenn das Produkt reden könnte, würde es sagen, dass es von Niceigkeit her kaum übertroffen werden kann!</div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-title>Kaufen unter:</v-card-title>

    <v-card-text>
      <v-chip-group
          v-model="selection"
          active-class="blue accent-4 white--text"
          column
      >
        <v-chip>Amazon</v-chip>

        <v-chip>Ebay</v-chip>

        <v-chip>Wish</v-chip>

        <v-chip>Alibaba</v-chip>
      </v-chip-group>
    </v-card-text>

    <v-card-actions>
      <v-btn
          color="deep-purple lighten-2"
          text
      >
        Button
      </v-btn>
    </v-card-actions>
  </v-card>
  </v-container>
</template>

<script>

import Carousel from "@/components/Carousel";
import Rating from "@/components/Rating";

  export default {
    name: 'Home',
    components: {
      Carousel,
      Rating
    },
    data: () => ({
      loading: false,
      selection: 0,
      showMenu: false,
      items: [
        { title: 'Amazon' },
        { title: 'Ebay' },
        { title: 'Wish' },
      ],
    })
  }
</script>

<style lang="scss" scoped>

.buy-options {
  position: fixed;
  z-index: 1;
  top: 90%;
  left: 85%;
}

</style>
