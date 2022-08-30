<template>
  <base-layout page-title="Search By Ingrident">
    <template v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <ion-list>
        <ion-item
          v-for="meal in lstMeals"
          :key="meal"
          @click="() => router.push(`/meal/${meal.idMeal}`)"
        >
          <ion-avatar slot="start">
            <ion-img :src="[meal.strMealThumb]"></ion-img>
          </ion-avatar>
          <ion-label>
            <h1>{{ meal.strMeal }}</h1>
          </ion-label>
        </ion-item>
      </ion-list>
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from "vue";
import {
  IonList,
  IonItem,
  IonSpinner,
  IonAvatar,
  IonLabel,
  IonImg,
} from "@ionic/vue";
import axios from "axios";
import { useRouter, useRoute } from "vue-router";

export default defineComponent({
  name: "Tab2Page",
  data() {
    return {
      loading: true,
      lstMeals: [],
    };
  },
  methods: {
    async fetchIngredientMeals() {
      const ingredient = this.$route.params.ingredient;
      const res = await axios.get(
        `https://www.themealdb.com/api/json/v1/1/filter.php?i=${ingredient}`
      );

      this.lstMeals = res.data.meals;
      this.loading = false;
    },
  },
  components: { IonList, IonItem, IonSpinner, IonAvatar, IonLabel, IonImg },
  created() {
    setTimeout(this.fetchIngredientMeals, 500);
  },
  setup() {
    const router = useRouter();
    const route = useRoute();
    return { router, route };
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
ion-spiner {
  transform: scale(1.5);
}
</style>