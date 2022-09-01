<template>
  <base-layout page-title="Search For Meal">
    <ion-toolbar>
      <ion-searchbar debounce="500" :onIonChange="(e) => fetchSearchResults(e.detail.value)"></ion-searchbar>
    </ion-toolbar>
    <div class="center" v-if="getResult && !lstMeals">
      <ion-label>No Results. pls search again..</ion-label>
    </div>
    <template v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <meal-card v-for="meal in lstMeals" :key="meal" :meal="meal" />
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from 'vue';
import { IonToolbar, IonSearchbar, IonLabel, IonSpinner } from '@ionic/vue';
import MealCard from "../components/MealCard.vue";
import axios from "axios";

export default defineComponent({
  name: 'Tab3Page',
  data () {
    return {
      loading: false,
      getResult: false,
      lstMeals: []
    }
  },
  components: { IonToolbar, IonSearchbar, IonLabel, IonSpinner, MealCard },
  methods: {
    async fetchSearchResults(request) {
      this.loading = true
      const res = await axios.get(
        `https://www.themealdb.com/api/json/v1/1/search.php?s=${request}`
      );

      this.lstMeals = res.data.meals;
      this.getResult = true
      this.loading = false
    }
  }
});
</script>
