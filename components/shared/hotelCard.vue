<script setup lang="ts">
interface HotelCard {
    image: string;
    name: string;
    rating: number;
    reviews: number;
    amenities: string[];
    location: string;
    distance: string;
    price: number;
}

defineProps<{
    card: HotelCard
}>();
</script>

<template>
    <div class="bg-white rounded-2xl border border-[#8DD3BB]/50 p-6">
        <div class="flex gap-8">
            <!-- Hotel Image -->
            <div class="w-[300px] h-[298.5px] shrink-0">
                <div class="relative w-full h-full">
                    <img :src="card.image" :alt="card.name" class="w-full h-full object-cover rounded-xl">
                    <div class="absolute top-3 left-3 bg-white/80 backdrop-blur-sm rounded px-2 py-1">
                        <span class="text-xs">9 images</span>
                    </div>
                </div>
            </div>

            <!-- Hotel Details -->
            <div class="flex-1 pt-1">
                <!-- Hotel Name and Price -->
                <div class="flex items-start justify-between mb-3">
                    <div>
                        <h3 class="text-[28px] leading-9 font-500">{{ card.name }}</h3>
                        <h4 class="text-[28px] leading-9 font-500">Istanbul</h4>
                    </div>
                    <div class="text-right">
                        <p class="text-sm text-[#112211]/60">starting from</p>
                        <div class="flex items-baseline gap-1">
                            <span class="text-[32px] leading-9 font-700 text-[#FF8682]">${{ card.price }}</span>
                            <span class="text-sm text-[#112211]/60">/night</span>
                        </div>
                        <p class="text-xs text-[#112211]/60">excl. tax</p>
                    </div>
                </div>

                <!-- Location -->
                <div class="flex items-center gap-2 mb-4">
                    <icon name="heroicons:map-pin" class="w-4 h-4" />
                    <span class="text-sm">{{ card.location }}</span>
                </div>

                <!-- Rating & Features -->
                <div class="flex items-center gap-6">
                    <div class="flex items-center gap-2">
                        <div class="px-2 py-1 bg-[#8DD3BB]/20 rounded">
                            <span class="text-sm font-500">{{ card.rating }}</span>
                        </div>
                        <span class="text-sm font-500">Very Good</span>
                        <span class="text-sm text-[#112211]/60">{{ card.reviews }} reviews</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <span class="text-[#FF8682] text-sm">★★★★★</span>
                        <span class="text-sm">5 Star Hotel</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <icon name="heroicons:sparkles" class="w-4 h-4" />
                        <span class="text-sm">20+ Amenities</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Bottom Actions -->
        <div class="flex items-center gap-4 mt-6 pt-6 border-t border-[#8DD3BB]/30">
            <button class="w-12 h-12 flex items-center justify-center border border-[#8DD3BB] rounded-lg hover:bg-[#8DD3BB]/10">
                <icon name="heroicons-outline:heart" class="w-5 h-5" />
            </button>
            <button class="flex-1 h-12 bg-[#8DD3BB] font-500 rounded-lg hover:bg-[#7bc0a9]">
                View Place
            </button>
        </div>
    </div>
</template> 