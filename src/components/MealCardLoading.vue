<template>
  <ion-card>
    <ion-grid>
      <ion-row>
        <ion-col size="12" size-sm>
          <ion-skeleton-text :animated="true" style="width: 100%; height: 400px" />
        </ion-col>
        <ion-col size="12" size-sm>
          <ion-card-header>
            <ion-card-subtitle>
              <ion-skeleton-text :animated="true" style="width: 30%; height: 10px;" />
            </ion-card-subtitle>
            <ion-title>
              <ion-skeleton-text :animated="true" style="width: 40%; height: 20px;" />
            </ion-title>
          </ion-card-header>
          <ion-list-header><u>Ingridents</u></ion-list-header>
          <ion-list>
            <template v-for="index in 15" :key="index">
              <ion-item>
                <ion-label>
                  <ion-skeleton-text :animated="true" style="width: 50%; height: 15px;" />
                </ion-label>
              </ion-item>
            </template>
          </ion-list>
        </ion-col>
      </ion-row>
    </ion-grid>
    <ion-card-content>
      <ion-skeleton-text :animated="true" style="width: 100%; height: 100px;" />
    </ion-card-content>
  </ion-card>
</template>

<script>
import { defineComponent } from "vue";
import {
  IonCard,
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
  IonSkeletonText
} from "@ionic/vue";

export default defineComponent({
  name: "MealCard",
  components: {
    IonCard,
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
    IonSkeletonText
  },
});
</script>
