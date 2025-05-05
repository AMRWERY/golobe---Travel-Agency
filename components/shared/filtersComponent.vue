<script setup lang="ts">
const props = defineProps<{
  type: 'flights' | 'hotels'
}>();

const isSidebarOpen = ref(false)
const priceRange = ref({
    min: 50,
    max: 1200
})
const timeRange = ref({
    min: 0, // 12:01 AM in hours
    max: 24 // 11:56 PM in hours
})
const selectedRating = ref('0+')

// Track collapsed state for each section
const collapsedSections = ref({
    price: false,
    time: true,
    rating: true,
    airlines: true,
    trips: true,
    freebies: true,
    amenities: true
})

const toggleSection = (section: keyof typeof collapsedSections.value) => {
    collapsedSections.value[section] = !collapsedSections.value[section]
}

const airlines = props.type === 'flights' 
  ? ['Emirated', 'Fly Dubai', 'Qatar', 'Etihad']
  : ['Hilton', 'Marriott', 'Hyatt', 'Sheraton'];

const trips = props.type === 'flights'
  ? ['Round trip', 'On Way', 'Multi-City', 'My Dates Are Flexible']
  : ['1 Night', '2-3 Nights', '4-7 Nights', 'Week+'];

const freebies = [
    'Free breakfast',
    'Free parking',
    'Free internet',
    'Free airport shuttle',
    'Free cancellation'
];

const amenities = [
    '24hr front desk',
    'Air-conditioned',
    'Fitness',
    'Pool'
];

const formatTime = (hour: number) => {
    const period = hour >= 12 ? 'Pm' : 'Am';
    const displayHour = hour % 12 || 12;
    return `${displayHour}:${hour === 24 ? '56' : '01'}${period}`;
};
</script>

<template>
    <div>
        <!-- Search Form -->
        <div class="w-full mt-12 shadow-lg rounded-3xl">
            <div class="bg-white rounded-3xl">
                <!-- Form Content -->
                <div class="p-4 space-y-4 md:p-6 md:space-y-5">
                    <div class="grid grid-cols-1 gap-4 md:flex md:items-center md:gap-4">
                        <!-- From-To Input -->
                        <div class="md:flex-1 md:min-w-[240px]">
                            <label class="text-sm text-gray-600">{{ type === 'flights' ? 'From - To' : 'Destination' }}</label>
                            <div class="relative mt-1">
                                <input type="text" :value="type === 'flights' ? 'Lahore - Karachi' : 'Dubai, UAE'"
                                    class="w-full p-3 pe-10 text-base text-gray-900 border rounded-lg focus:ring-2 focus:ring-[#8dd3bb]">
                                <button v-if="type === 'flights'" class="absolute -translate-y-1/2 end-3 top-1/2">
                                    <icon name="mdi:exchange"
                                        class="mt-2 w-[15px] h-5"></icon>
                                </button>
                            </div>
                        </div>

                        <!-- Trip Select -->
                        <div class="md:flex-1 md:min-w-[180px]">
                            <label class="text-sm text-gray-600">{{ type === 'flights' ? 'Trip' : 'Stay' }}</label>
                            <select
                                class="w-full p-3 mt-1 text-base text-gray-900 border rounded-lg focus:ring-2 focus:ring-[#8dd3bb]">
                                <option v-for="option in trips" :key="option">{{ option }}</option>
                            </select>
                        </div>

                        <!-- Date Input -->
                        <div class="md:flex-1 md:min-w-[280px]">
                            <label class="text-sm text-gray-600">{{ type === 'flights' ? 'Depart - Return' : 'Check-in - Check-out' }}</label>
                            <input type="text" value="07 Nov 22 - 13 Nov 22"
                                class="w-full p-3 mt-1 text-base text-gray-900 border rounded-lg focus:ring-2 focus:ring-[#8dd3bb]">
                        </div>

                        <!-- Passenger Input -->
                        <div class="md:flex-1 md:min-w-[240px]">
                            <label class="text-sm text-gray-600">{{ type === 'flights' ? 'Passenger - Class' : 'Rooms - Guests' }}</label>
                            <input type="text" :value="type === 'flights' ? '1 Passenger, Economy' : '1 Room, 2 Guests'"
                                class="w-full p-3 mt-1 text-base text-gray-900 border rounded-lg focus:ring-2 focus:ring-[#8dd3bb]">
                        </div>

                        <!-- Search Button -->
                        <div class="md:flex-none md:ms-2">
                            <button
                                class="p-3 md:mt-7 bg-[#8dd3bb] rounded hover:bg-[#7bc0a9] transition-colors flex items-center ms-auto">
                                <icon name="tabler:search" class="w-[19px] h-[19px]"></icon>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="mt-8">
            <div class="relative min-h-screen">
                <!-- Mobile Menu Button -->
                <button @click="isSidebarOpen = true"
                    class="fixed bottom-4 start-4 p-3 bg-[#8dd3bb] rounded-full shadow-lg md:hidden z-50">
                    <icon name="ci:menu-alt-03"></icon>
                </button>

                <!-- Desktop Layout -->
                <div class="flex flex-col md:flex-row">
                    <!-- Scrollable Sidebar (Column 3) -->
                    <div class="fixed inset-y-0 end-0 w-[343px] md:w-[343px] md:relative md:inset-auto h-screen bg-white shadow-lg transform transition-transform duration-300 ease-in-out md:translate-x-0 z-50 overflow-hidden"
                        :class="{ 'translate-x-0': isSidebarOpen, 'translate-x-full': !isSidebarOpen }">

                        <!-- Scrollable Content Container -->
                        <div class="flex flex-col h-full">
                            <!-- Scrollable Content -->
                            <div class="flex-1 p-6 overflow-y-auto scroll-hidden">
                                <div class="flex items-center justify-between">
                                    <h3 class="mb-8 text-xl font-600">Filters</h3>
                                    <button @click="isSidebarOpen = false" class="mb-2 bg-white md:hidden">
                                        <icon name="ci:close-big"></icon>
                                    </button>
                                </div>

                                <!-- Price Filter -->
                                <div class="filter-section">
                                    <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('price')">
                                        <h4 class="text-base font-500">Price</h4>
                                        <icon :name="collapsedSections.price ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                    </div>
                                    <div v-show="!collapsedSections.price" class="mt-4">
                                        <div class="relative">
                                            <div class="multi-range">
                                                <input type="range" 
                                                       :min="50" 
                                                       :max="1200" 
                                                       v-model="priceRange.min"
                                                       class="range-left"
                                                       @input="priceRange.min = Math.min(priceRange.min, priceRange.max - 1)" />
                                                <input type="range" 
                                                       :min="50" 
                                                       :max="1200" 
                                                       v-model="priceRange.max"
                                                       class="range-right"
                                                       @input="priceRange.max = Math.max(priceRange.max, priceRange.min + 1)" />
                                            </div>
                                            <div class="flex justify-between mt-2">
                                                <span class="text-sm">${{ priceRange.min }}</span>
                                                <span class="text-sm">${{ priceRange.max }}</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>

                                <template v-if="type === 'flights'">
                                    <!-- Flight-specific filters -->
                                    <!-- Departure Time -->
                                    <div class="filter-section mt-6">
                                        <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('time')">
                                            <h4 class="text-base font-500">Departure Time</h4>
                                            <icon :name="collapsedSections.time ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                        </div>
                                        <div v-show="!collapsedSections.time" class="mt-4">
                                            <div class="relative">
                                                <div class="multi-range">
                                                    <input type="range" 
                                                           :min="0" 
                                                           :max="24" 
                                                           v-model="timeRange.min"
                                                           class="range-left"
                                                           @input="timeRange.min = Math.min(timeRange.min, timeRange.max - 1)" />
                                                    <input type="range" 
                                                           :min="0" 
                                                           :max="24" 
                                                           v-model="timeRange.max"
                                                           class="range-right"
                                                           @input="timeRange.max = Math.max(timeRange.max, timeRange.min + 1)" />
                                                </div>
                                                <div class="flex justify-between mt-2">
                                                    <span class="text-sm">{{ formatTime(timeRange.min) }}</span>
                                                    <span class="text-sm">{{ formatTime(timeRange.max) }}</span>
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                    <!-- Rating -->
                                    <div class="filter-section mt-6">
                                        <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('rating')">
                                            <h4 class="text-base font-500">Rating</h4>
                                            <icon :name="collapsedSections.rating ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                        </div>
                                        <div v-show="!collapsedSections.rating" class="flex gap-2 mt-4">
                                            <button v-for="rating in ['0+', '1+', '2+', '3+', '4+']" 
                                                    :key="rating"
                                                    class="px-3 py-1 border border-[#8DD3BB] rounded-sm text-sm"
                                                    :class="{ 'bg-[#8DD3BB] text-white': selectedRating === rating }"
                                                    @click="selectedRating = rating">
                                                {{ rating }}
                                            </button>
                                        </div>
                                    </div>

                                    <!-- Airlines Section -->
                                    <div class="filter-section mt-6">
                                        <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('airlines')">
                                            <h4 class="text-base font-500">Airlines</h4>
                                            <icon :name="collapsedSections.airlines ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                        </div>
                                        <div v-show="!collapsedSections.airlines" class="space-y-3 mt-4">
                                            <label v-for="airline in airlines" 
                                                   :key="airline" 
                                                   class="flex items-center gap-2">
                                                <input type="checkbox" 
                                                       class="w-4 h-4 border-2 border-[#8DD3BB] rounded text-[#8DD3BB] focus:ring-[#8DD3BB]">
                                                <span class="text-sm">{{ airline }}</span>
                                            </label>
                                        </div>
                                    </div>

                                    <!-- Trips -->
                                    <div class="filter-section mt-6">
                                        <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('trips')">
                                            <h4 class="text-base font-500">Trips</h4>
                                            <icon :name="collapsedSections.trips ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                        </div>
                                        <div v-show="!collapsedSections.trips" class="space-y-3 mt-4">
                                            <label v-for="trip in ['Round trip', 'On Way', 'Multi-City', 'My Dates Are Flexible']" 
                                                   :key="trip" 
                                                   class="flex items-center gap-2">
                                                <input type="checkbox" 
                                                       class="w-4 h-4 border-2 border-[#8DD3BB] rounded text-[#8DD3BB] focus:ring-[#8DD3BB]">
                                                <span class="text-sm">{{ trip }}</span>
                                            </label>
                                        </div>
                                    </div>
                                </template>

                                <template v-else>
                                    <!-- Hotel-specific filters -->
                                    <!-- Rating -->
                                    <div class="filter-section mt-6">
                                        <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('rating')">
                                            <h4 class="text-base font-500">Rating</h4>
                                            <icon :name="collapsedSections.rating ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                        </div>
                                        <div v-show="!collapsedSections.rating" class="flex gap-2 mt-4">
                                            <button v-for="rating in ['0+', '1+', '2+', '3+', '4+']" 
                                                    :key="rating"
                                                    class="px-3 py-1 border border-[#8DD3BB] rounded-sm text-sm"
                                                    :class="{ 'bg-[#8DD3BB] text-white': selectedRating === rating }"
                                                    @click="selectedRating = rating">
                                                {{ rating }}
                                            </button>
                                        </div>
                                    </div>

                                    <!-- Freebies -->
                                    <div class="filter-section mt-6">
                                        <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('freebies')">
                                            <h4 class="text-base font-500">Freebies</h4>
                                            <icon :name="collapsedSections.freebies ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                        </div>
                                        <div v-show="!collapsedSections.freebies" class="space-y-3 mt-4">
                                            <label v-for="freebie in freebies" 
                                                   :key="freebie" 
                                                   class="flex items-center gap-2">
                                                <input type="checkbox" 
                                                       class="w-4 h-4 border-2 border-[#8DD3BB] rounded text-[#8DD3BB] focus:ring-[#8DD3BB]">
                                                <span class="text-sm">{{ freebie }}</span>
                                            </label>
                                        </div>
                                    </div>

                                    <!-- Amenities -->
                                    <div class="filter-section mt-6">
                                        <div class="flex items-center justify-between cursor-pointer" @click="toggleSection('amenities')">
                                            <h4 class="text-base font-500">Amenities</h4>
                                            <icon :name="collapsedSections.amenities ? 'heroicons:chevron-down' : 'heroicons:chevron-up'" />
                                        </div>
                                        <div v-show="!collapsedSections.amenities" class="space-y-3 mt-4">
                                            <label v-for="amenity in amenities" 
                                                   :key="amenity" 
                                                   class="flex items-center gap-2">
                                                <input type="checkbox" 
                                                       class="w-4 h-4 border-2 border-[#8DD3BB] rounded text-[#8DD3BB] focus:ring-[#8DD3BB]">
                                                <span class="text-sm">{{ amenity }}</span>
                                            </label>
                                        </div>
                                    </div>
                                </template>
                            </div>
                        </div>
                    </div>

                    <!-- Main Content (Column 9) -->
                    <div class="flex-1 min-h-screen">
                        <filtered-cards :type="type" />
                    </div>
                </div>

                <!-- Mobile Backdrop -->
                <div @click="isSidebarOpen = false" class="fixed inset-0 z-30 bg-black/50 md:hidden"
                    :class="{ 'hidden': !isSidebarOpen }"></div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.scroll-hidden {
    overflow-y: scroll;
}

.scroll-hidden::-webkit-scrollbar {
    display: none;
}

.scroll-hidden {
    -ms-overflow-style: none;
    scrollbar-width: none;
}

.multi-range {
    position: relative;
    height: 30px;
    width: 100%;
    overflow: visible;
}

.multi-range input[type="range"] {
    position: absolute;
    width: 100%;
    height: 2px;
    background: #112211;
    pointer-events: none;
    -webkit-appearance: none;
    overflow: visible;
}

.multi-range input[type="range"]::-webkit-slider-thumb {
    height: 20px;
    width: 20px;
    border-radius: 50%;
    background: #8DD3BB;
    cursor: pointer;
    margin-top: -9px;
    pointer-events: auto;
    -webkit-appearance: none;
    box-shadow: 0 0 2px 0 #555;
}

.multi-range input[type="range"]::-webkit-slider-runnable-track {
    width: 100%;
    height: 2px;
    background: #112211;
    border: none;
    border-radius: 3px;
}

.multi-range .range-left::-webkit-slider-thumb {
    z-index: 3;
    position: relative;
}

.multi-range .range-right::-webkit-slider-thumb {
    z-index: 3;
}

/* Checkbox styling */
input[type="checkbox"] {
    accent-color: #8DD3BB;
}

.filter-section {
    padding-bottom: 1rem;
    border-bottom: 1px solid #D7E2EE;
}
</style>