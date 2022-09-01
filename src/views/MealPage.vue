<template>
  <base-layout :page-title="`${meal.strMeal}`">
    <template v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <meal-card :meal="meal" />
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
      meal: null
    };
  },
  methods: {
    async fetchMeal() {
      const id = this.$route.params.id;
      const res = await axios.get(
        `https://www.themealdb.com/api/json/v1/1/lookup.php?i=${id}`
      );

      this.meal = res.data.meals[0];
      this.loading = false
    },
  },
  created() {
    this.fetchMeal();
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