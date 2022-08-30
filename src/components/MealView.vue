<template>
  <ion-card>
    <ion-grid>
      <ion-row>
        <ion-col size="12" size-sm>
          <ion-img :src="meal.strMealThumb"></ion-img>
        </ion-col>
        <ion-col size="12" size-sm>
          <ion-card-header>
            <ion-card-subtitle>
              Category- {{ meal.strCategory }} | From the {{ meal.strArea }}
            </ion-card-subtitle>
            <ion-title>
              {{ meal.strMeal }}
            </ion-title>
          </ion-card-header>
          <ion-list-header><u>Ingridents</u></ion-list-header>
          <ion-list>
            <template v-for="index in 15" :key="index">
              <ion-item v-if="meal[`strIngredient${index}`]">
                <ion-label>
                  <span v-if="meal[`strMeasure${index}`]">
                    {{ meal[`strMeasure${index}`] }} |
                  </span>
                  <span>
                    {{ meal[`strIngredient${index}`] }}
                  </span>
                </ion-label>
              </ion-item>
            </template>
          </ion-list>
        </ion-col>
      </ion-row>
    </ion-grid>
    <ion-card-content>
      <p>{{ meal.strInstructions }}</p>
    </ion-card-content>
  </ion-card>
</template>

<script>
import { defineComponent } from "vue";
import {
  IonCard,
  IonImg,
  IonTitle,
  IonCardSubtitle,
  IonCardHeader,
  IonListHeader,
  IonList,
  IonItem,
  IonCardContent,
  IonLabel,
  IonGrid,
  IonRow,
  IonCol,
} from "@ionic/vue";

export default defineComponent({
  name: "MealView",
  props: ["meal"],
  components: {
    IonCard,
    IonImg,
    IonTitle,
    IonCardSubtitle,
    IonCardHeader,
    IonListHeader,
    IonList,
    IonItem,
    IonCardContent,
    IonLabel,
    IonGrid,
    IonRow,
    IonCol,
  },
});
</script>