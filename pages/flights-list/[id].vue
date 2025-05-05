<script setup lang="ts">

</script>

<template>
    <div>
        <div class="mx-auto md:w-full md:max-w-[1232px] px-4 md:px-0">
            <div class="mt-6 mb-4 md:mb-8 md:mt-12">
                <!-- breadcrumb component -->
                <breadcrumb />
            </div>

            <div class="flex flex-col md:flex-row justify-between items-start gap-4">
                <div class="flex-1 w-full">
                    <div class="flex justify-between items-center w-full md:block">
                        <p class="text-2xl font-700 text-gray-800">Emirates A380 Airbus</p>
                        <!-- Mobile Price -->
                        <p class="md:hidden text-3xl font-700 text-[#FF8682]">$240</p>
                    </div>
                    <p class="text-sm font-500 flex items-center text-gray-600 mt-4 mb-2">
                        <icon name="material-symbols-light:location-on-rounded"
                            class="me-2 w-4 h-5"></icon>
                        Gümüssuyu Mah. Inönü Cad. No:8, Istanbul 34437
                    </p>
                    <div class="flex items-center gap-4">
                        <div class="border border-[#cdece1] px-2 py-1 rounded-md">
                            <span class="text-xs text-[#6a756a]">4.2</span>
                        </div>
                        <p class="text-base font-600 text-gray-800">
                            Very Good <span class="font-400">54 reviews</span>
                        </p>
                    </div>
                </div>

                <div class="w-full md:w-auto">
                    <div class="flex flex-col items-end gap-4">
                        <!-- Desktop Price -->
                        <p class="hidden md:block text-[32px] font-700 text-[#FF8682] text-end">$240</p>
                        <div class="flex flex-row-reverse md:flex-row items-center justify-end gap-3 w-full">
                            <div class="flex gap-3">
                                <button
                                    class="w-12 h-12 border rounded border-[#a2dbc7] hover:bg-gray-50 flex items-center justify-center">
                                    <icon name="heroicons-outline:heart"
                                        class="text-[#4c4850]"></icon>
                                </button>
                                <button
                                    class="w-12 h-12 border rounded border-[#a2dbc7] hover:bg-gray-50 flex items-center justify-center">
                                    <icon name="material-symbols-light:share"
                                        class="text-[#4c4850]"></icon>
                                </button>
                            </div>
                            <nuxt-link to="/flights-list/book-now" class="h-12 px-6 text-sm font-600 bg-[#8dd3bb] hover:bg-[#7dc3ab] 
                           text-gray-900 rounded flex items-center justify-center w-full md:w-[150px]">
                                Book Now
                            </nuxt-link>
                        </div>
                    </div>
                </div>
            </div>

            <div class="inset-0 z-0 w-full mt-8 mb-10 h-[395px]">
                <img src="https://justfields.com/storage/projects/7M5rV059/img-01.jpg" alt="Emirates A380"
                    class="w-full h-full object-cover rounded-2xl">
            </div>

            <div class="flex flex-col md:flex-row justify-between items-start gap-4">
                <p class="text-2xl font-700 capitalize w-full">basic economy features</p>
                <div class="flex md:flex-row items-center justify-end gap-3 w-full">
                    <div class="flex items-center justify-center gap-6">
                        <label class="flex items-center gap-3 ms-0.5">
                            <input type="checkbox"
                                class="w-[18px] h-[18px] border-2 border-[#b8bdb8] rounded text-[#8dd3bb] focus:ring-[#8dd3bb] focus:ring-0 self-center" />
                            <div class="flex flex-col">
                                <span class="text-sm font-500 capitalize">economy</span>
                            </div>
                        </label>
                        <label class="flex items-center gap-3 ms-0.5">
                            <input type="checkbox"
                                class="w-[18px] h-[18px] border-2 border-[#b8bdb8] rounded text-[#8dd3bb] focus:ring-[#8dd3bb] focus:ring-0 self-center" />
                            <div class="flex flex-col">
                                <span class="text-sm font-500 capitalize">first Class</span>
                            </div>
                        </label>
                        <label class="flex items-center gap-3 ms-0.5">
                            <input type="checkbox"
                                class="w-[18px] h-[18px] border-2 border-[#b8bdb8] rounded text-[#8dd3bb] focus:ring-[#8dd3bb] focus:ring-0 self-center" />
                            <div class="flex flex-col">
                                <span class="text-sm font-500 capitalize">Busines Class</span>
                            </div>
                        </label>
                    </div>
                </div>
            </div>

            <!-- featuresCards componenet -->
            <featuresCards />

            <div class="space-y-10">
                <div class="mt-10 h-auto md:max-h-[287px] rounded-2xl bg-white shadow-lg p-5">
                    <div class="flex justify-between">
                        <p class="capitalize text-md md:text-xl font-700 text-color">
                            return wed, dec 8
                        </p>
                        <p class="text-md md:text-xl font-500 text-color">
                            2h 28m
                        </p>
                    </div>
                    <div class="mt-6 flex flex-col md:flex-row items-center">
                        <div
                            class="rounded-lg border border-[#8DD3BB] px-4 md:px-8 py-4 flex items-center justify-center min-w-[262px] min-h-[86px]">
                            <div class="h-[44.49px] w-[64px]">
                                <img src="https://justfields.com/storage/projects/7M5rV059/emirates.png" alt="emirates"
                                    class="object-contain w-full h-full" />
                            </div>
                            <div class="ms-4 md:ms-6">
                                <p class="text-xl md:text-2xl font-600">Emirates</p>
                                <span class="text-sm font-500 mt-1">Airbus A320</span>
                            </div>
                        </div>
                        <div class="flex items-center space-s-4 md:ms-auto mt-6 md:mt-0">
                            <i>
                                <icon name="zondicons:airplane" class="text-color w-[22px] h-[20px]" />
                            </i>
                            <div class="w-[1px] h-4 bg-[#112211]/20"></div>
                            <i>
                                <icon name="material-symbols:wifi" class="text-color w-[22px] h-[20px]" />
                            </i>
                            <div class="w-[1px] h-4 bg-[#112211]/20"></div>
                            <i>
                                <icon name="material-symbols:policy"
                                    class="text-color w-[22px] h-[20px]" />
                            </i>
                            <div class="w-[1px] h-4 bg-[#112211]/20"></div>
                            <i>
                                <icon name="material-symbols:fastfood"
                                    class="text-color w-[22px] h-[20px]" />
                            </i>
                            <div class="w-[1px] h-4 bg-[#112211]/20"></div>
                            <i>
                                <icon name="hugeicons:airplane-seat"
                                    class="text-color w-[22px] h-[20px]" />
                            </i>
                        </div>
                    </div>
                    <div class="mt-4 md:mt-10 max-w-2xl flex flex-col md:flex-row items-center justify-between mx-auto">
                        <div class="flex items-center justify-center gap-4 mb-4 md:mb-0">
                            <p class="text-2xl font-600">12:00 pm</p>
                            <span class="text-base font-500 opacity-60 mt-1.5">Newark(EWR)</span>
                        </div>
                        <div class="flex items-center justify-center max-w-[168px] gap-6 mb-4 md:mb-0">
                            <icon name="material-symbols:line-start-rounded" />
                            <icon name="zondicons:airplane" class="w-[45px] h-[39px]" />
                            <icon name="material-symbols:line-end-rounded" />
                        </div>
                        <div class="flex items-center justify-center gap-4">
                            <p class="text-2xl font-600">12:00 pm</p>
                            <span class="text-base font-500 opacity-60 mt-1.5">Newark(EWR)</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>