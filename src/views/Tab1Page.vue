<template>
  <base-layout page-title="Random">
    <ion-content v-if="loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </ion-content>
    <ion-content :fullscreen="true" v-else>
      <h1>Hello</h1>
    </ion-content>
  </base-layout>
</template>

<script>
import { defineComponent } from 'vue'
import { IonSpinner, IonContent } from '@ionic/vue'
import axios from 'axios'

export default  defineComponent({
  name: 'Tab1Page',
  components: { IonSpinner, IonContent },
  data() {
    return {
      loading: true
    }
  },
  methods: {
    hideShow() {
      this.loading = !this.loading
    }
  },
  
})
</script>

<style scoped>
.loading-center {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 90vh;
  transform: scale(1.5);
}
</style>
