<template>
  <base-layout page-title="Random Meal">
    <template v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <meal-view :meal="randomMeal" />
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from "vue";
import MealView from "../components/MealView.vue";
import { IonSpinner } from "@ionic/vue";
import axios from "axios";

export default defineComponent({
  name: "Tab1Page",
  components: { IonSpinner, MealView },
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

<style scoped>
.loading-center {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 90vh;
}
ion-spinner {
  transform: scale(1.5);
}
</style>