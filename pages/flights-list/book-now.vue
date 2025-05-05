<script setup lang="ts">
const showEmailForm = ref(false)
</script>

<template>
    <div>
        <div class="mx-auto md:w-full md:max-w-[1232px] px-4 md:px-0">
            <div class="mt-6 mb-4 md:mb-8 md:mt-12">
                <!-- breadcrumb component -->
                <breadcrumb />
            </div>

            <section>
                <div class="mt-6 sm:mt-8 lg:flex lg:items-start lg:gap-8">
                    <div class="flex-1 min-w-0 space-y-8">
                        <div class="h-auto md:max-h-[287px] rounded-2xl bg-white shadow-lg p-5">
                            <div class="flex justify-between">
                                <p class="capitalize text-xl md:text-2xl font-700 text-color">
                                    return wed, dec 8
                                </p>
                                <p class="text-xl md:text-2xl font-500 text-color">
                                    2h 28m
                                </p>
                            </div>
                            <div class="mt-6 flex flex-col md:flex-row items-center">
                                <div
                                    class="rounded-lg border border-[#8DD3BB] px-4 md:px-8 py-4 flex items-center justify-center min-w-[262px] min-h-[86px]">
                                    <div class="h-[44.49px] w-[64px]">
                                        <img src="https://justfields.com/storage/projects/7M5rV059/emirates.png"
                                            alt="emirates" class="object-contain w-full h-full" />
                                    </div>
                                    <div class="ms-4 md:ms-6">
                                        <p class="text-xl md:text-2xl font-700">Emirates</p>
                                        <span class="text-sm font-500 mt-1 block">Airbus A320</span>
                                    </div>
                                </div>
                                <div class="flex items-center space-s-4 md:ms-auto mt-6 md:mt-0">
                                    <i>
                                        <icon name="zondicons:airplane"
                                            class="text-color w-[22px] h-5" />
                                    </i>
                                    <i>
                                        <icon name="material-symbols:wifi"
                                            class="text-color w-[22px] h-5" />
                                    </i>
                                    <i>
                                        <icon name="material-symbols:timer-rounded"
                                            class="text-color w-[22px] h-5" />
                                    </i>
                                    <i>
                                        <icon name="material-symbols:fastfood"
                                            class="text-color w-[22px] h-5" />
                                    </i>
                                    <i>
                                        <icon name="hugeicons:airplane-seat"
                                            class="text-color w-[22px] h-5" />
                                    </i>
                                </div>
                            </div>
                            <div
                                class="mt-4 md:mt-10 max-w-2xl flex flex-col md:flex-row items-center justify-between mx-auto">
                                <div class="flex items-center justify-center gap-4 mb-4 md:mb-0">
                                    <p class="text-2xl font-700">12:00 pm</p>
                                    <span class="text-base font-500 mt-1.5">Newark(EWR)</span>
                                </div>
                                <div class="flex items-center justify-center max-w-[168px] gap-6 mb-4 md:mb-0">
                                    <icon name="material-symbols:line-start-rounded" />
                                    <icon name="zondicons:airplane" class="w-12 h-12" />
                                    <icon name="material-symbols:line-end-rounded" />
                                </div>
                                <div class="flex items-center justify-center gap-4">
                                    <p class="text-2xl font-700">12:00 pm</p>
                                    <span class="text-base font-500 mt-1.5">Newark(EWR)</span>
                                </div>
                            </div>
                        </div>

                        <div class="space-y-4">
                            <div class="group">
                                <input type="radio" name="payment" id="full" class="hidden peer">
                                <label for="full"
                                    class="flex justify-between p-4 h-auto border border-gray-200 rounded-lg cursor-pointer peer-checked:bg-[#8DD3BB]">
                                    <div class="flex flex-col justify-center">
                                        <div class="text-base font-700 text-color">Pay in full</div>
                                        <div class="mt-3 text-sm font-400 text-color">Pay the total and you are
                                            all set</div>
                                    </div>
                                    <div class="flex items-center">
                                        <div
                                            class="w-5 h-5 border-2 border-gray-300 rounded-full peer-checked:border-[#2D6E6B] flex items-center justify-center bg-white">
                                            <div
                                                class="w-2.5 h-2.5 bg-[#2D6E6B] rounded-full opacity-0 peer-checked:opacity-100">
                                            </div>
                                        </div>
                                    </div>
                                </label>
                            </div>
                            <div class="group">
                                <input type="radio" name="payment" id="partial" class="hidden peer">
                                <label for="partial"
                                    class="flex justify-between p-4 border border-gray-200 rounded-lg cursor-pointer peer-checked:bg-[#8DD3BB] h-auto">
                                    <div class="flex flex-col justify-center">
                                        <div class="text-base font-700 text-color">Pay part now, part later</div>
                                        <div class="mt-3 text-sm font-400 text-color md:max-w-[632px]">
                                            Pay $207.43 now, and the rest ($207.43) will be automatically charged to the
                                            same payment method on Nov 14, 2022. No extra fees.
                                        </div>
                                        <div class="mt-3">
                                            <nuxt-link to=""
                                                class="text-xs font-500 text-color underline hover:text-blue-600">More
                                                info</nuxt-link>
                                        </div>
                                    </div>
                                    <div class="flex items-center">
                                        <div
                                            class="w-5 h-5 border-2 border-gray-300 rounded-full peer-checked:border-[#2D6E6B] flex items-center justify-center bg-white">
                                            <div
                                                class="w-2.5 h-2.5 bg-[#2D6E6B] rounded-full opacity-0 peer-checked:opacity-100">
                                            </div>
                                        </div>
                                    </div>
                                </label>
                            </div>
                        </div>

                        <div class="mt-10 rounded-2xl bg-white shadow-lg p-6">
                            <div class="space-y-4 items-start">
                                <p class="capitalize text-xl font-700 text-color">login or sign up to book</p>
                                <input type="tel" placeholder="Your phone number"
                                    class="flex-1 px-4 py-3 border border-gray-200 rounded w-full" />
                                <p class="text-sm text-color font-400">We’ll call or text you to confirm your number.
                                    Standard message and data rates apply.
                                    <span class="font-500">Privacy Policy</span>
                                </p>
                                <nuxt-link to="" type="button"
                                    class="w-full flex justify-center items-center h-12 px-2 text-sm font-600 tracking-wide text-color bg-[#8dd3bb] border-none rounded outline-none ms-auto">Continue</nuxt-link>
                            </div>
                            <div class="relative flex items-center justify-center my-[34px]">
                                <span class="absolute inset-x-0 h-px bg-gray-300"></span>
                                <span class="relative px-4 text-base font-500 text-color bg-white capitalize">or</span>
                            </div>
                            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                                <div class="w-full">
                                    <button
                                        class="w-full flex items-center justify-center gap-2 px-4 py-4 border-2 border-[#8DD3BB] rounded transition-all">
                                        <icon name="logos:facebook" class="w-6 h-6"></icon>
                                    </button>
                                </div>
                                <div class="w-full">
                                    <button
                                        class="w-full flex items-center justify-center gap-2 px-4 py-4 border-2 border-[#8DD3BB] rounded transition-all">
                                        <icon name="logos:google-icon" class="w-6 h-6"></icon>
                                    </button>
                                </div>
                                <div class="w-full">
                                    <button
                                        class="w-full flex items-center justify-center gap-2 px-4 py-4 border-2 border-[#8DD3BB] rounded transition-all">
                                        <icon name="logos:apple" class="w-6 h-6"></icon>
                                    </button>
                                </div>
                            </div>
                            <button type="button" @click="showEmailForm = true"
                                class="w-full flex justify-center items-center h-12 px-2 text-base font-500 tracking-wide text-color border border-[#8DD3BB] rounded ms-auto mt-4">
                                <icon name="ic:baseline-email"
                                    class="me-4 w-[21px] h-[21px]"></icon>
                                Continue with email
                            </button>

                            <!-- authForm component -->
                            <auth-form :show="showEmailForm" />
                        </div>

                        <!-- if login -->
                        <div class="mt-10 rounded-2xl bg-white shadow-lg p-6">
                            <div class="bg-[#8DD3BB] rounded-lg">
                                <label for="full"
                                    class="flex justify-between p-4 h-auto border border-gray-200 cursor-pointer">
                                    <div class="flex justify-center items-center">
                                        <icon name="logos:visaelectron"
                                            class="me-8 w-8 h-5"></icon>
                                        <div class="text-base font-700 text-color">**** 4321</div>
                                        <div class="text-sm font-400 text-color ms-2">02/27</div>
                                    </div>
                                    <div class="flex items-center">
                                        <div
                                            class="w-5 h-5 border-2 border-gray-300 rounded-full peer-checked:border-[#2D6E6B] flex items-center justify-center bg-white">
                                            <div
                                                class="w-2.5 h-2.5 bg-[#2D6E6B] rounded-full opacity-0 peer-checked:opacity-100">
                                            </div>
                                        </div>
                                    </div>
                                </label>
                            </div>

                            <div>
                                <div
                                    class="mt-4 flex justify-center rounded-lg border border-dashed border-[#8DD3BB] px-6 py-10">
                                    <!-- addNewCardDialog component -->
                                    <add-new-card-dialog />
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- left card -->
                    <div class="w-full mt-6 space-y-6 sm:mt-8 lg:mt-0 lg:max-w-sm bg-white shadow-lg p-3 rounded-lg">
                        <div class="flow-root">
                            <div class="flex items-start col-span-2 gap-4 border-b pb-4">
                                <div class="rounded-md w-[120px] h-[120px] shrink-0">
                                    <img src='https://justfields.com/storage/projects/7M5rV059/plane-img.png'
                                        alt="plane-img" class="object-contain w-full h-full" />
                                </div>
                                <div class="flex flex-col">
                                    <p class="text-base font-500 text-color mt-0.5">Economy</p>
                                    <h3 class="text-xl font-600 text-color">Emirates A380 Airbus</h3>
                                    <div class="flex items-center gap-4 mt-5">
                                        <div class="border border-[#cdece1] px-2 py-1 rounded-md">
                                            <span class="text-xs text-[#6a756a]">4.2</span>
                                        </div>
                                        <p class="text-base font-600 text-gray-800">
                                            Very Good <span class="font-400">54 reviews</span>
                                        </p>
                                    </div>
                                </div>
                            </div>
                            <div>
                                <dl class="flex items-center justify-between gap-4 py-3">
                                    <dt class="text-base font-700 text-gray-500 capitalize">price details</dt>
                                </dl>
                                <dl class="flex items-center justify-between gap-4 py-4">
                                    <dt class="text-base font-500 text-gray-500 capitalize">base fare</dt>
                                    <dd class="text-base font-500 text-gray-700">$400</dd>
                                </dl>
                                <dl class="flex items-center justify-between gap-4 py-4">
                                    <dt class="text-base font-500 text-gray-500 capitalize">discount</dt>
                                    <dd class="text-base font-500 text-gray-700">$400</dd>
                                </dl>
                                <dl class="flex items-center justify-between gap-4 py-4">
                                    <dt class="text-base font-500 text-gray-500 capitalize">taxes</dt>
                                    <dd class="text-base font-500 text-gray-700">$400</dd>
                                </dl>
                                <dl class="flex items-center justify-between gap-4 py-4">
                                    <dt class="text-base font-500 text-gray-500 capitalize">Service Fee</dt>
                                    <dd class="text-base font-500 text-gray-700">$400</dd>
                                </dl>
                                <dl class="flex items-center justify-between gap-4 py-3 border-t pt-4">
                                    <dt class="text-base font-700 text-gray-900">Total</dt>
                                    <dd class="text-base font-700 text-gray-900">$8,392.00</dd>
                                </dl>
                            </div>
                            <nuxt-link to="/booking-summary" type="button"
                                class="w-full flex justify-center items-center h-12 px-2 text-sm font-600 tracking-wide text-color bg-[#8dd3bb] border-none rounded outline-none ms-auto">Pay
                                now</nuxt-link>
                        </div>
                    </div>
                </div>
            </section>
        </div>
    </div>
</template>