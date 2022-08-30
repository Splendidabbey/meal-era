<template>
  <base-layout page-title="Search By Ingrident">
    <template v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <ion-list>
        <ion-item v-for="index in 15" :key="index">
          <ion-avatar slot="start">
            <img src="">
          </ion-avatar>
          <ion-label>
            <h1>Ginger{{index}}</h1>
          </ion-label>
        </ion-item>
      </ion-list>
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from 'vue';
import { IonList, IonItem, IonSpinner, IonAvatar, IonLabel } from '@ionic/vue';

export default defineComponent({
  name: 'Tab2Page',
  data () {
    return {
      loading:true
    }
  },
  components: { IonList, IonItem, IonSpinner, IonAvatar, IonLabel },
  created () {
    setTimeout(() => {
      this.loading = false
    }, 1000);
  }
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
