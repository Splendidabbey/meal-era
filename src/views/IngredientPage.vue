<template>
  <base-layout :page-title="ingredient ? ingredient : 'loading...'" page-back-link="/tabs/tab2">
    <template v-if="loading">
      <list-card-loading />
    </template>
    <template v-else>
      <ion-list>
        <ion-item
          v-for="meal in lstMeals"
          :key="meal"
          @click="() => router.push(`/meal/${meal.idMeal}`)"
          button="true"
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
  IonAvatar,
  IonLabel,
  IonImg,
} from "@ionic/vue";
import axios from "axios";
import { useRouter, useRoute } from "vue-router";
import ListCardLoading from "../components/ListCardLoading.vue";

export default defineComponent({
  name: "Tab2Page",
  data() {
    return {
      loading: true,
      lstMeals: [],
      ingredient: this.$route.params.ingredient
    };
  },
  methods: {
    async fetchIngredientMeals() {
      const res = await axios.get(
        `https://www.themealdb.com/api/json/v1/1/filter.php?i=${this.ingredient}`
      );

      this.lstMeals = res.data.meals;
      this.loading = false;
    },
  },
  components: { IonList, IonItem, IonAvatar, IonLabel, IonImg, ListCardLoading },
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