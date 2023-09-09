<script setup lang="ts">
import { ref } from 'vue'

/**
 * Restaurants
 * 
 * Name - String
 * Address - String
 * Status - String (e.g., "Want to try" || "Must try!")
 * Dishes - Array of Dish Objects
 */

 interface Restaurant {
   name: string
   address: string
   status: string
   dishes: Dish[]
 }

class Dish {
  name: string
  price: number
} 

const restaurants = ref<Restaurant[]>([])
const restaurantName = ref<Restaurant>({
  name: '',
  address: '',
  status: '',
  dishes: []
})

function addRestaurant() {
  restaurants.value.push({
    name: restaurantName.value.name,
    address: '',
    status: '',
    dishes: []
  })
}


</script>

<template>
  <main>
    <!-- Create a form that allows users to add a restaurant to a list -->
    <form @submit.prevent="addRestaurant">
      <label for="restaurant-name">Restaurant Name</label>
      <input type="text" id="restaurant" v-model="restaurantName" />
      <button type="submit">Add Restaurant</button>
    </form>
    <!-- Display the list of restaurants -->
    <ol>
      <li v-for="restaurant in restaurants" :key="restaurant.name ">
        {{ restaurant.name }}
      </li>
    </ol>
  </main>
</template>
