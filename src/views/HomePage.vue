<template>
  <ion-page>
    <ion-list>
      <ion-item>
        <ion-input label="Name"></ion-input>
      </ion-item>
      <ion-item>
        <ion-datetime-button datetime="datetime"></ion-datetime-button>
        <ion-modal :keep-contents-mounted="true">
          <ion-datetime v-model="age" id="datetime" presentation="date"></ion-datetime>
        </ion-modal>
      </ion-item>
      <ion-item>
        <ion-input label="Address"></ion-input>
      </ion-item>
    </ion-list>
    <p>{{ now }}</p>

  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonList, IonItem, IonInput, IonDatetime, IonDatetimeButton, IonModal } from '@ionic/vue';
import { ref,computed } from 'vue';

const name = ref(''); // Initialisierter Name als leerer String
const age = ref(new Date(Date.now()).toISOString());   // Initialisiertes Alter als Zahl
const now = computed(() => new Date(age.value).toDateString());
</script>

<style scoped lang="scss">
ion-datetime-button::part(time-button) {
  display: none;
}
</style>
