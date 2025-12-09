<script setup>
  import { ref } from 'vue'
import SearchInput from './components/SearchInput.vue';
import WeatherCard from './components/WeatherCard.vue';

const places = ref ([])

const addPlace = (data) => {
  places.value.push(data)
}

</script>
<template>
  <main>
    <!-- Date-->
    <div class="text-center mb-6">
      {{ new Date().toLocaleDateString('en-us', {
        weekday:'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric'
        }) 
      }}
    </div>
    <!-- Search-->
     <div>
        <SearchInput @place-data="addPlace"/>
     </div>

     <!-- weather cards-->
     <div class="grid grid-cols-2 gap-4">
       <div v-for="(place, idx) in places" :key="idx">
        <WeatherCard :place="place"/>
      </div>
     </div>
  </main> 
</template>