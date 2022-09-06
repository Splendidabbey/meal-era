<template>
  <ion-list>
    <ion-item v-for="index in 10" :key="index">
      <ion-avatar slot="start">
        <ion-skeleton-text :animated="true" />
      </ion-avatar>
      <ion-label>
        <ion-skeleton-text :animated="true" style="width: 100%; height: 20px" />
      </ion-label>
    </ion-item>
  </ion-list>
</template>

<script>
import { defineComponent } from "vue";
import {
  IonList,
  IonItem,
  IonAvatar,
  IonLabel,
  IonSkeletonText,
} from "@ionic/vue";

export default defineComponent({
  name: "ListCardLoading",
  components: { IonList, IonItem, IonAvatar, IonLabel, IonSkeletonText },
});
</script>