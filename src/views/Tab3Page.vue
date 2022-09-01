<template>
  <base-layout page-title="Search">
    <template v-if="!loading">
      <div class="loading-center">
        <ion-spinner color="primary"></ion-spinner>
      </div>
    </template>
    <template v-else>
      <ion-toolbar>
        <ion-searchbar debounce="500" :onIonChange="(e) => fetchSearchResults(e.detail.value)"></ion-searchbar>
      </ion-toolbar>
    </template>
  </base-layout>
</template>

<script>
import { defineComponent } from 'vue';
import { IonToolbar, IonSearchbar, IonSpinner } from '@ionic/vue';

export default defineComponent({
  name: 'Tab3Page',
  data () {
    return {
      loading: true
    }
  },
  components: { IonToolbar, IonSearchbar, IonSpinner },
  methods: {
    fetchSearchResults(text) {
      console.log(text)
    }
  }
});
</script>
