<template>
  <ion-page>
    <ion-content :fullscreen="true" class="content">
      <div class="header-wrapper">
        <ion-card class="header-card">
          <ion-card-header>
            <ion-card-title class="title">Metric Converter</ion-card-title>
            <ion-card-subtitle class="subtitle">By: Cleantha Polii</ion-card-subtitle>
          </ion-card-header>
        </ion-card>
      </div>

      <ion-card class="converter-card">
        <ion-card-content>
          <ion-item>
            <ion-label>Pilih Metrik</ion-label>
            <ion-select v-model="metricType">
              <ion-select-option value="length">Length</ion-select-option>
              <ion-select-option value="weight">Weight</ion-select-option>
              <ion-select-option value="temperature">Temperature</ion-select-option>
            </ion-select>
          </ion-item>

          <ion-item>
            <ion-label>Unit From</ion-label>
            <ion-select v-model="unitFrom">
              <ion-select-option v-for="unit in units[metricType]" :key="unit" :value="unit">{{ unit }}</ion-select-option>
            </ion-select>
          </ion-item>

          <ion-item>
            <ion-label>Unit To</ion-label>
            <ion-select v-model="unitTo">
              <ion-select-option v-for="unit in units[metricType]" :key="unit" :value="unit">{{ unit }}</ion-select-option>
            </ion-select>
          </ion-item>

          <ion-item>
            <ion-label>Value</ion-label>
            <ion-input v-model.number="inputValue" type="number" placeholder="Enter value"></ion-input>
          </ion-item>

          <div class="result">
            <h3>Hasil Konversi</h3>
            <p>{{ conversionResult }}</p>
          </div>
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import {
  IonPage,
  IonContent,
  IonItem,
  IonLabel,
  IonSelect,
  IonSelectOption,
  IonInput,
  IonCard,
  IonCardHeader,
  IonCardTitle,
  IonCardSubtitle,
  IonCardContent,
} from '@ionic/vue';

const metricType = ref<string | null>(null);
const unitFrom = ref<string | null>(null);
const unitTo = ref<string | null>(null);
const inputValue = ref<number | null>(null);

const units = {
  length: ['Meters', 'Kilometers', 'Miles'],
  weight: ['Grams', 'Kilograms', 'Pounds'],
  temperature: ['Celsius', 'Fahrenheit', 'Kelvin'],
};

const conversionResult = computed(() => {
  if (inputValue.value == null || !unitFrom.value || !unitTo.value || !metricType.value) {
    return 'N/A';
  }

  let result: number;

  if (metricType.value === 'length') {
    // Logika Konversi Panjang
    // ... (implementasi sesuai kebutuhan)
  }

  if (metricType.value === 'weight') {
    // Logika Konversi Berat
    // ... (implementasi sesuai kebutuhan)
  }

  if (metricType.value === 'temperature') {
    // Logika Konversi Suhu
    // ... (implementasi sesuai kebutuhan)
  }

  return 'Conversion not supported';
});
</script>

<style scoped>
/* Mengatur gambar background untuk seluruh halaman */
ion-page {
  background-image: url('../../assets/img/images.jpeg');
  background-size: cover;
  background-position: center;
}

.content {
  padding: 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh; /* Pastikan content penuh halaman */
}

.header-wrapper {
  display: flex;
  justify-content: flex-start; /* Header rata kiri */
  margin-bottom: 20px;
  width: 100%;
}

.header-card {
  background: rgba(46, 125, 50, 0.8); /* Sedikit transparan agar gambar latar terlihat */
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  max-width: 400px;
  width: 100%;
}

.title {
  color: #ffffff; /* Warna putih untuk judul */
  font-weight: 500;
}

.subtitle {
  color: #c8e6c9; /* Hijau terang untuk subjudul */
}

.converter-card {
  background: rgba(76, 175, 80, 0.9); /* Sedikit transparan */
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  max-width: 400px;
  width: 100%;
}

.result {
  margin-top: 20px;
  text-align: center;
}

h3 {
  color: #ffffff; /* Warna putih untuk judul hasil */
}

p {
  font-size: 18px;
  font-weight: 500;
  color: #333;
}

ion-item {
  margin-bottom: 16px;
}

ion-label {
  color: #ffffff; /* Warna putih untuk label */
  font-weight: 500;
}

ion-select,
ion-input {
  --color: #ffffff; /* Warna teks putih */
}

ion-input::part(native) {
  border-bottom: 1px solid #ffffff; /* Garis bawah putih untuk input */
}

ion-select::part(native) {
  border-bottom: 1px solid #ffffff; /* Garis bawah putih untuk select */
}

ion-select .select-icon {
  color: #ffffff; /* Warna ikon select putih */
}
</style>
