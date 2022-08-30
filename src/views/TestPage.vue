<template>
  <base-layout page-title="Random">
    <div class="container">
      <h1>Splendid</h1>
    </div>
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
      <ion-card>
        <ion-img :src="randomMeal.strMealThumb"></ion-img>
        <ion-card-header>
          <ion-card-subtitle>
            {{ randomMeal.strCategory }} | Served in
            {{  }}
          </ion-card-subtitle>
          <ion-title>
            {{ randomMeal.strMeal }}
          </ion-title>
        </ion-card-header>
        <ion-card-content>
          <p>{{ randomMeal.strInstructions }}</p>
        </ion-card-content>
        <ion-list-header>Ingridents</ion-list-header>
        <ion-list>
          <ion-item v-if="randomMeal.strIngredient1">
            <ion-label>
              <span v-if="randomMeal.strMeasure1">
                {{ randomMeal.strMeasure1 }} |
              </span>
              <span>
                {{ randomMeal.strIngredient1 }}
              </span>
            </ion-label>
          </ion-item>
        </ion-list>
      </ion-card>
  </base-layout>
</template>

<script>
import { defineComponent } from 'vue'
import { IonSpinner, IonImg, IonCard, IonCardSubtitle, IonCardHeader, IonTitle, IonListHeader, IonList, IonItem, IonCardContent, IonLabel } from '@ionic/vue'
import axios from 'axios'

export default  defineComponent({
  name: 'Tab1Page',
  components: { IonSpinner, IonImg, IonCard, IonCardSubtitle, IonCardHeader, IonTitle, IonListHeader, IonList, IonItem, IonCardContent, IonLabel },
  data() {
    return {
      loading: true,
      randomMeal: null
    }
  },
  methods: {
    async fetchRandomMeal () {
      const res = await axios.get('https://www.themealdb.com/api/json/v1/1/random.php')
      this.randomMeal = res.data.meals[0]
      console.log(this.randomMeal)
      console.log(`https://www.themealdb.com/ingredient/${this.randomMeal.strIngredient1}`)
      this.loading = false
    }
  },
  created () {
    this.fetchRandomMeal()
  }
})
</script>

<style scoped>
.loading-center {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 10vh;
  transform: scale(1.5);
}
.container {
  width: 100vw;
  height: 100vh;
  background-color: white;
}
</style>
