<script setup>
    import Borderline from './Borderline.vue'
    import WeatherForecastDay from './WeatherForecastDay.vue';

    defineProps({
        place: Object
    })
</script>
<template>
    <div class="text-white p-10 rounded-lg shadow-lg mb-6 relative overflow-hidden bg-blue-500">
        <!-- location and time-->
         <div class="mb-2 flex justify-between items-center">
            <div class="flex items-center justify-center gap-2">
                <i class="fa-solid fa-location-dot"></i>
                <h1 class="text-3x1">{{ place.location.name}}</h1>
            </div>
            <div class="flex items-center justify-center gap-2">
                <i class="fa-solid fa-clock"></i>
                <h1 class="text-3x1">[{{new Date(place.location.localtime).getHours()}} :
                    {{new Date(place.location.localtime).getMinutes()}}
                </h1>
            </div>
         </div>

        <!-- current weather-->        
        <div class="text-center flex-1">
            <img :src="place.current.condition.icon" alt="icon" width="200" class="mx-auto -mb-10" />
            <h1 class="text-9x1 mb-2">{{Math.round(place.current.temp_c)}}&deg;</h1>
            <p class="tetx-2x1">{{place.current.condition.text}}</p>
        </div>

        <Borderline />

        <!--forecast-->
        <div>
            <!-- weather daily forecast components -->
             <div v-for="day in place.forecast.forecastday" :key="idx">
                <WeatherForecastDay :day="day" />
             </div>
        </div>

        <!-- info -->
        <div class="flex justify-end item-center gap-1 mt-10">
            <button>More <i class="fa-solid fa-arrow-right text-sm -mb-px"></i>
            </button>
        </div>
    </div>
 </template>