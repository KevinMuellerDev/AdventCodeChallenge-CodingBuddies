<template>
  <ion-app>
    <ion-header>
      <ion-toolbar>
        <ion-title>Header</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="content">
      <ion-router-outlet aria-label="content"/>
    </ion-content>
  </ion-app>
</template>

<script setup lang="ts">
import { IonApp, IonRouterOutlet,IonHeader,IonToolbar,IonTitle, IonContent } from '@ionic/vue';
</script>

<style lang="scss">
  ion-app{
    height: 100dvh;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
</style>
