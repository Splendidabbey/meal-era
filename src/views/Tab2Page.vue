<template>
  <base-layout page-title="Search By Ingrident">
    <template v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <ion-list>
        <ion-item v-for="ingrident in ingredients" :key="ingrident" @click="() => router.push(`/meal-by-ingredient/${ingrident.strIngredient}`)">
          <ion-avatar slot="start">
            <ion-img :src="`https://www.themealdb.com/images/ingredients/${ingrident.strIngredient}-Small.png`"></ion-img>
          </ion-avatar>
          <ion-label>
            <h1> {{ ingrident.strIngredient }}</h1>
          </ion-label>
        </ion-item>
      </ion-list>
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from 'vue';
import { IonList, IonItem, IonSpinner, IonAvatar, IonLabel, IonImg } from '@ionic/vue';
import axios from 'axios';
import { useRouter } from 'vue-router';

export default defineComponent({
  name: 'Tab2Page',
  data () {
    return {
      loading:true,
      ingredients: []
    }
  },
  methods: {
    async fetchIngredients () {
      const res = await axios.get(
      "https://www.themealdb.com/api/json/v1/1/list.php?i=list"
      );
      this.ingredients = res.data.meals
      this.loading = false;
    }
  },
  components: { IonList, IonItem, IonSpinner, IonAvatar, IonLabel, IonImg },
  created () {
    this.fetchIngredients()
  },
  setup () {
    const router = useRouter();
    return { router };
  }
});
</script>
