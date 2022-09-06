<template>
  <base-layout page-title="Random Meal">
    <template v-slot:actions-end>
      <ion-button @click="fetchRandomMeal">
        <ion-icon slot="icon-only" :icon="refreshOutline">
        </ion-icon>
      </ion-button>
    </template>
    <template v-if="loading">
      <meal-card-loading :meal="randomMeal" :loading="loading" />
    </template>
    <template v-else>
      <meal-card :meal="randomMeal" :loading="loading" />
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from "vue";
import MealCardLoading from "../components/MealCardLoading.vue";
import MealCard from "../components/MealCard.vue";
import axios from "axios";

import { IonButton, IonIcon} from '@ionic/vue'
import { refreshOutline } from 'ionicons/icons'

export default defineComponent({
  name: "Tab1Page",
  components: { MealCard, IonButton, IonIcon, MealCardLoading },
  data() {
    return {
      loading: true,
      randomMeal: null,
      refreshOutline
    };
  },
  methods: {
    async fetchRandomMeal() {
      this.loading = true
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
