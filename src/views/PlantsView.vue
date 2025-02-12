<script setup>
  import { usePlantStore } from '@/stores/plant';

  const plantStore = usePlantStore();

  plantStore.fetchPlants();

</script>

<template>
  <div>
    <h1>Plants</h1>
    <div class="row">
      <div class="card col-12 col-sm-6 col-md-4 col-lg-3" v-for="plant in plantStore.plants" :key="plant.id">
        <p class = "h4">{{ plant.nev }}</p>
        <div class="card-body">
          <p class = "h2">Évelő: {{ plant.evelo }}</p>
          <p class = "h2">Kategória: {{ plant.kategoria }}</p>
        </div>
        <div class="card-footer">
          <p class = "h5">Ár: {{ plant.ar }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
