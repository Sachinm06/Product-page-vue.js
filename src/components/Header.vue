<template>
  <nav>
    <v-toolbar app color="primary" height="100">
      <v-toolbar-title class="white--text text-uppercase">
        <h1>Vue pages</h1>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn depressed color="success" class="mr-10" @click="$router.push('/profile')">
        <v-icon class="mr-2">mdi-account-circle</v-icon>
        Profile
      </v-btn>
      <v-btn depressed color="success" class="mr-10" @click="$router.push('/products')"
        ><v-icon class="mr-2">mdi-shopping</v-icon> Products
      </v-btn>
      <v-btn depressed color="success" class="mr-10" @click="$router.push('/feedback')">
        <v-icon class="mr-1">mdi-comment-outline</v-icon>
        Feedback
      </v-btn>
    </v-toolbar>

  </nav>
</template>

<script>
export default {
  data() {
    return {
    };
  },
};
</script>
