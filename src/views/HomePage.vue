<template>
  <ion-page class="form-content">
    <ion-list>
      <ion-item class="input-col">
        <ion-input type="string" placeholder="Bitte Namen eingeben..." v-model="form.name" @input="validateName"
          :class="{ invalid: !isNameValid }" label="Name"></ion-input>
      </ion-item>
      <p v-if="!isNameValid" class="error-message">Name should only contain letters.</p>
      <ion-item class="input-col">
        <ion-input v-model="form.age" @input="validateAge" :class="{ invalid: !isAgeValid }"
          placeholder="Bitte geben Sie ihr Alter an..." type="number" label="Alter"></ion-input>
      </ion-item>
      <p v-if="!isAgeValid" class="error-message">Age must be between 0-99.</p>
      <ion-item>
        <ion-input type="string" v-model="form.address" @input="validateAddress" label="Adresse"></ion-input>
      </ion-item>
      <p v-if="!isAddressValid" class="error-message">Address can't be empty.</p>
    </ion-list>

  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonList, IonItem, IonInput, IonDatetime, IonDatetimeButton, IonModal } from '@ionic/vue';
import { ref, computed } from 'vue';

let form = {
  "name": '',
  "age": '',
  "address": ''
};

const isNameValid = ref(true);
const isAgeValid = ref(true);
const isAddressValid = ref(true);

const validateName = () => {
  isNameValid.value = /^[a-zA-Z\s]+$/.test(form.name.trim()) && form.name.length != 0;
};

const validateAge = () => {
  const ageValue = parseInt(form.age, 10);
  isAgeValid.value = !isNaN(ageValue) && ageValue >= 0 && ageValue <= 99 && ageValue != 0;
}

const validateAddress = () => {
  isAddressValid.value = form.address.length != 0;
}

</script>

<style scoped lang="scss">
ion-datetime-button::part(time-button) {
  display: none;
}

.error-message {
  margin: 0 20px;
  color: red;
  font-size: 0.6em;
}

.input-col {
  width: 90%;
}

.form-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
