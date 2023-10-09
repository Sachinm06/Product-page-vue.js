<template>
  <v-container>
    <v-row>
      <v-col v-for="(product, index) in products" :key="index" cols="12" md="4">
        <v-card
          :loading="product.loading"
          class="mx-auto my-12"
          max-width="574"
          max-height="80"
        >
          <template slot="progress">
            <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
            ></v-progress-linear>
          </template>

          <v-img :src="product.image" height="250"></v-img>

          <v-card-title>{{ product.title }}</v-card-title>

          <v-card-text>
            <v-row align="center" class="mx-0">
              <v-rating
                :value="product.rating"
                color="amber"
                dense
                half-increments
                readonly
                size="14"
              ></v-rating>

              <div class="grey--text ms-4">
                {{ product.rating }} ({{ product.reviewsCount }})
              </div>
            </v-row>

            <div class="my-4 text-subtitle-1">$ • {{ product.category }}</div>

            <div>{{ product.description }}</div>
          </v-card-text>

          <v-divider class="mx-4"></v-divider>

          <v-card-title>Tonight's availability</v-card-title>

          <v-card-text>
            <v-chip-group
              v-model="product.selection"
              active-class="deep-purple accent-4 white--text"
              column
            >
              <v-chip v-for="time in product.availability" :key="time">{{ time }}</v-chip>
            </v-chip-group>
          </v-card-text>

          <v-card-actions>
            <v-btn color="deep-purple lighten-2" text @click="reserve(product)">
              Reserve
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      products: [
        {
          image: "https://cdn.vuetifyjs.com/images/cards/cooking.png",
          title: "Cafe Badilico",
          rating: 4.5,
          reviewsCount: 413,
          category: "Italian, Cafe",
          description:
            "Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating.",
          availability: ["5:30PM", "7:30PM", "8:00PM", "9:00PM"],
          selection: 1,
          loading: false,
        },
        {
          image:
            "https://www.tasteatlas.com/images/dishes/f4291f3e82f84c33a5997f801e8fb24f.jpg",
          title: "Sunshine Delights",
          rating: 4.8,
          reviewsCount: 352,
          category: "Breakfast, Brunch",
          description:
            "Start your day with delicious breakfast and brunch options. A perfect way to brighten your morning.",
          availability: ["6:00AM", "8:00AM", "9:30AM", "11:00AM"],
          selection: 1,
          loading: false,
        },
        {
          image:
            "https://d4t7t8y8xqo0t.cloudfront.net/resized/750X436/eazytrendz%2F1418%2Ftrend20170410055833.jpg",
          title: "Super Mart",
          rating: 4.2,
          reviewsCount: 587,
          category: "Grocery, Supermarket",
          description:
            "Wide range of groceries and daily essentials. Shop with us for quality products and great offers.",
          availability: ["9:00AM", "11:00AM", "1:00PM", "3:00PM"],
          selection: 1,
          loading: false,
        },
      ],
    };
  },
  methods: {
    reserve(product) {
      product.loading = true;

      setTimeout(() => {
        alert(`Reserved ${product.title}`);
        product.loading = false;
      }, 2000);
    },
  },
};
</script>

<style scoped>
/* Add your scoped styles here */
</style>
