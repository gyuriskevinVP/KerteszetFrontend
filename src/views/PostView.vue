<script setup>
import { ref } from 'vue'
import { usePlantStore } from '@/stores/plant';
import { useRouter } from 'vue-router';


const plantStore = usePlantStore()
const router = useRouter();
const plant = ref({
  id: 0,
  nev:"",
  evelo: "",
  kategoria: "",
  ar: 0,
})

const submitForm = async () => {
  try {
    alert("Plant added")
    await plantStore.postPlant(plant.value)
    router.push("/")
  } catch(err){
    console.error(err.message)
    alert("Failed to add plant.")
  }
} 

</script>

<template>
  <div>
    <h2>Plant Info</h2>
    <form @submit.prevent = "submitForm">
      <label>
        Name
        <input v-model = "plant.nev" type="text" required />
      </label>

      <label>
        Perennial
        <input v-model = "plant.evelo" type="checkbox"/>
      </label>

      <label>
        Category
        <input v-model = "plant.kategoria" type="text" required/>
      </label>

      <label>
        Price
        <input v-model = "plant.ar" type="number" required/>
      </label>

      <button type="submit">Submit</button>

    </form>
  </div>
</template>

<style scoped>
  label, input{
    display: block;
  }


</style>
