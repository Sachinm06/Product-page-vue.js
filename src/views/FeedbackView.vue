<template>
  <v-container>
    <v-form ref="form" v-model="valid" lazy-validation max-width="574">
      <v-text-field
        v-model="name"
        :counter="10"
        :rules="nameRules"
        label="Name"
        required
      ></v-text-field>

      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>

      <v-textarea
        v-model="feedback"
        :rules="[(v) => !!v || 'Feedback is required']"
        label="Feedback"
        required
      ></v-textarea>

      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        Submit
      </v-btn>
    </v-form>
  </v-container>
</template>

<style scoped>
.feedback-container {
  max-width: 300px;
}
</style>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      checkbox: false,
      feedback: "",
      valid: true,
      nameRules: [
        (v) => !!v || "Name is required",
        (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
      ],
      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
      ],
    };
  },
  methods: {
    validate() {
      this.$refs.form.validate();
    },
    resetForm() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },
  },
};
</script>
