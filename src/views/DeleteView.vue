<script setup>
    import { ref } from 'vue'
    import { usePlantStore } from '@/stores/plant';
    import { useRouter } from 'vue-router';

    const router = useRouter();
    const plantStore = usePlantStore();
    const id = ref(Number)
    const deletePlantForm = async() => {
        try{
            await plantStore.deletePlant(id.value)
            alert("Plant deleted. ")
            router.push("/")
        } catch(err){
            console.error(err.message);
            alert("Delete is not happening lil bro")
        }
    }
</script>

<template>
    <div>
        <h2>Delete Plant</h2>
        <form @submit.prevent = "deletePlantForm">
            <label>
                Id: 
                <input v-model="id" type="number" min="1" required>
            </label>
            <button type="submit">Submit</button>
        </form>
    </div>
</template>
  
<style>
</style>
  