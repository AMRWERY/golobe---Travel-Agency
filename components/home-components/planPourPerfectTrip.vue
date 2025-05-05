<script setup lang="ts">
const destinations = [
    {
        city: 'Istanbul',
        country: 'Turkey',
        image: 'https://images.unsplash.com/photo-1524231757912-21f4fe3a7200?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1456&q=80'
    },
    {
        city: 'Sydney',
        country: 'Australia',
        image: 'https://images.unsplash.com/photo-1506973035872-a4ec16b8e8d9?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80'
    },
    {
        city: 'Baku',
        country: 'Azerbaijan',
        image: 'https://justfields.com/storage/projects/7M5rV059/Baku,%20Azerbaijan.jpg'
    },
    {
        city: 'Malé',
        country: 'Maldives',
        image: 'https://images.unsplash.com/photo-1573843981267-be1999ff37cd?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1374&q=80'
    },
    {
        city: 'Paris',
        country: 'France',
        image: 'https://images.unsplash.com/photo-1502602898657-3e91760cbb34?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1473&q=80'
    },
    {
        city: 'New York',
        country: 'US',
        image: 'https://images.unsplash.com/photo-1496442226666-8d4d0e62e6e9?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80'
    },
    {
        city: 'London',
        country: 'UK',
        image: 'https://images.unsplash.com/photo-1513635269975-59663e0ac1ad?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80'
    },
    {
        city: 'Tokyo',
        country: 'Japan',
        image: 'https://images.unsplash.com/photo-1540959733332-eab4deabeeaf?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1471&q=80'
    },
    {
        city: 'Dubai',
        country: 'UAE',
        image: 'https://images.unsplash.com/photo-1512453979798-5ea266f8880c?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80'
    }
]
</script>

<template>
    <div>
        <div class="pt-12">
            <!-- Header section -->
            <div class="flex items-center justify-between mb-8">
                <div>
                    <h2 class="title-style">Plan your perfect trip</h2>
                    <p class="subtitle-style">Search Flights & Places Hire to our
                        most popular
                        destinations</p>
                </div>
                <button role="button" class="outline-btn-block">
                    See more places
                </button>
            </div>

            <!-- Destination cards grid -->
            <div class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-3">
                <div v-for="(destination, index) in destinations" :key="index"
                    class="flex items-center p-3 overflow-hidden transition-shadow bg-white shadow-lg opacity-100 rounded-3xl hover:shadow-md">
                    <!-- Destination image -->
                    <div class="flex-shrink-0 w-16 h-16 sm:w-[90px] sm:h-[90px]">
                        <img :src="destination.image" :alt="destination.city"
                            class="object-cover w-full h-full rounded-lg">
                    </div>
                    <!-- Destination info -->
                    <div class="ms-4">
                        <h3 class="font-600 text-[#697369] text-base">{{ destination.city }}, {{ destination.country }}
                        </h3>
                        <div class="flex flex-wrap mt-1 text-sm text-gray-600 font-500">
                            <nuxt-link to="" class="me-1 hover:text-[#314031]">Flights</nuxt-link>
                            <span class="mx-1">•</span>
                            <nuxt-link to="" class="mx-1 hover:text-[#314031]">Hotels</nuxt-link>
                            <span class="mx-1">•</span>
                            <nuxt-link to="" class="ms-1 hover:text-[#314031]">Resorts</nuxt-link>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Mobile "See more" button -->
            <div class="flex justify-center mt-6 md:hidden">
                <button role="button" class="outline-btn">
                    See more places
                </button>
            </div>

            <!-- Flights and Hotels cards -->
            <div class="grid grid-cols-1 gap-6 mt-12 md:grid-cols-2">
                <!-- Flights card -->
                <div class="relative overflow-hidden rounded-[20px] shadow-md h-[340px] md:h-[400px]">
                    <img src="https://justfields.com/storage/projects/7M5rV059/flights-card-mg.jpg" alt="Flights"
                        class="object-cover w-full h-full">
                    <div
                        class="absolute inset-0 flex flex-col justify-end p-6 text-center text-white bg-black bg-opacity-20">
                        <div class="w-[300px] md:w-[389px] mx-auto">
                            <h3 class="mb-2 text-[40px] font-700">Flights</h3>
                            <p class="mb-4 text-sm md:text-base font-400">Search flights & Places Hire to our most
                                popular destinations</p>
                            <div class="flex justify-center">
                                <button class="search-form-btn">
                                    <icon name="material-symbols:flight" class="me-2 w-3.5 h-3.5"></icon>
                                    Show Flights
                                </button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Hotels card -->
                <div class="relative overflow-hidden rounded-[20px] shadow-md h-[340px] md:h-[400px]">
                    <img src="https://justfields.com/storage/projects/7M5rV059/hotels-card-mg.jpg" alt="Hotels"
                        class="object-cover w-full h-full">
                    <div
                        class="absolute inset-0 flex flex-col justify-end p-6 text-center text-white bg-black bg-opacity-20">
                        <div class="w-[300px] md:w-[389px] mx-auto">
                            <h3 class="mb-2 text-[40px] font-700">Hotels</h3>
                            <p class="mb-4 text-sm md:text-base font-400">Search hotels & Places Hire to our most
                                popular destinations</p>
                            <div class="flex justify-center">
                                <button class="search-form-btn">
                                    <icon name="material-symbols:hotel" class="me-2 w-3.5 h-3.5"></icon>
                                    Show Hotels
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>