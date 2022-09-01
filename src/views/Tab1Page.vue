<template>
  <base-layout page-title="Random Meal">
    <template v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <meal-card :meal="randomMeal" />
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from "vue";
import MealCard from "../components/MealCard.vue";
import { IonSpinner } from "@ionic/vue";
import axios from "axios";

export default defineComponent({
  name: "Tab1Page",
  components: { IonSpinner, MealCard },
  data() {
    return {
      loading: true,
      randomMeal: null,
    };
  },
  methods: {
    async fetchRandomMeal() {
      const res = await axios.get(
        "https://www.themealdb.com/api/json/v1/1/random.php"
      );
      
      this.randomMeal = res.data.meals[0];
      this.loading = false;
    },
  },
  created() {
    this.fetchRandomMeal();
  },
});
</script>
