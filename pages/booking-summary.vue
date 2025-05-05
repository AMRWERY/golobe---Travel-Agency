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
                        <p class="md:hidden text-3xl font-700">$240</p>
                    </div>
                    <p class="text-sm font-500 flex items-center text-gray-600 mt-4 mb-2">
                        <icon name="material-symbols-light:location-on-rounded"
                            class="me-2"></icon>
                        Gümüssuyu Mah. Inönü Cad. No:8, Istanbul 34437
                    </p>
                </div>
                <div class="w-full md:w-auto">
                    <div class="flex flex-col items-end gap-4">
                        <!-- Desktop Price -->
                        <p class="hidden md:block text-[32px] font-700 text-end">$240</p>
                        <div class="flex flex-row-reverse md:flex-row items-center justify-end gap-3 w-full">
                            <div class="flex gap-3">
                                <button
                                    class="w-12 h-12 border rounded border-[#a2dbc7] hover:bg-gray-50 flex items-center justify-center">
                                    <icon name="material-symbols-light:share"
                                        class="text-[#4c4850]"></icon>
                                </button>
                            </div>
                            <nuxt-link to="" role="button" class="h-12 px-6 text-sm font-600 bg-[#8dd3bb] hover:bg-[#7dc3ab] 
                           text-gray-900 rounded flex items-center justify-center w-full md:w-[150px]">
                                Download
                            </nuxt-link>
                        </div>
                    </div>
                </div>
            </div>

            <div
                class="flex flex-col md:flex-row max-w-full mx-auto bg-white shadow-lg rounded-xl overflow-hidden mt-10">
                <div
                    class="bg-[#EBF6F2] px-6 py-[34.5px] flex flex-col justify-between w-full md:w-[246px] text-center md:text-start">
                    <div class="mb-4">
                        <p class="text-[32px] font-600 text-color">12:00 pm</p>
                        <p class="text-xs font-500">Newark (EWR)</p>
                    </div>
                    <div class="block space-y-4 md:space-y-0">
                        <img src="../assets/summary-03.svg" alt="img-03"
                            class="mx-auto md:mx-0 w-[36px] h-[46px] block">
                        <img src="../assets/summary-02.svg" alt="img-02" class="mx-auto md:mx-0 w-8 h-8 block md:my-4">
                        <img src="../assets/summary-01.svg" alt="img-01"
                            class="mx-auto md:mx-0 w-[36px] h-[46px] block">
                    </div>
                    <div class="mt-4">
                        <p class="text-[32px] font-600 text-color">12:00 pm</p>
                        <p class="text-xs text-color font-500">Newark (EWR)</p>
                    </div>
                </div>

                <div class="flex-1 bg-white relative w-full md:w-[610px] rounded-e-3xl">
                    <div>
                        <div class="bg-[#8DD3BB] p-4 rounded-e-lg">
                            <div class="flex items-center gap-4">
                                <img class="w-10 h-10 rounded-full" src="https://i.pravatar.cc/100?img=3" alt="avatar">
                                <div>
                                    <h2 class="text-xl font-700">Amr Mohamed</h2>
                                    <p class="text-sm font-400 text-gray-600">Boarding Pass N°123</p>
                                </div>
                                <div class="ms-auto text-sm font-700 text-gray-700">Business Class</div>
                            </div>
                        </div>
                        <div class="p-4 flex flex-col h-full min-h-[250px]">
                            <div class="flex-1">
                                <div class="mt-6 grid grid-cols-2 gap-4 md:grid-cols-4 text-sm text-gray-700">
                                    <div class="flex gap-2 items-center">
                                        <div
                                            class="w-[34px] h-[34px] bg-[#EBF6F2] flex items-center justify-center rounded">
                                            <icon name="material-symbols:calendar-month"
                                                class="text-[#8DD3BB]"></icon>
                                        </div>
                                        <div>
                                            <p class="text-sm text-gray-500 font-600">Date</p>
                                            <p class="text-xs font-500">Newark (EWR)</p>
                                        </div>
                                    </div>
                                    <div class="flex gap-2 items-center">
                                        <div
                                            class="w-[34px] h-[34px] bg-[#EBF6F2] flex items-center justify-center rounded">
                                            <icon name="material-symbols:nest-clock-farsight-analog-rounded"
                                                class="text-[#8DD3BB]"></icon>
                                        </div>
                                        <div>
                                            <p class="text-xs text-gray-500 font-600">Flight time</p>
                                            <p class="text-xs font-500">12:00</p>
                                        </div>
                                    </div>
                                    <div class="flex gap-2 items-center">
                                        <div
                                            class="w-[34px] h-[34px] bg-[#EBF6F2] flex items-center justify-center rounded">
                                            <icon name="material-symbols:door-open"
                                                class="text-[#8DD3BB]"></icon>
                                        </div>
                                        <div>
                                            <p class="text-xs text-gray-500 font-600">Gate</p>
                                            <p class="text-xs font-500">A12</p>
                                        </div>
                                    </div>
                                    <div class="flex gap-2 items-center">
                                        <div
                                            class="w-[34px] h-[34px] bg-[#EBF6F2] flex items-center justify-center rounded">
                                            <icon name="hugeicons:airplane-seat"
                                                class="text-[#8DD3BB]"></icon>
                                        </div>
                                        <div>
                                            <p class="text-xs text-gray-500 font-600">Seat</p>
                                            <p class="text-xs font-500">12B</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="mt-auto -mb-4">
                                <div class="flex justify-between items-center">
                                    <div>
                                        <div class="mb-6">
                                            <p class="text-[32px] font-600">EK</p>
                                            <p class="text-xs text-gray-500 font-500 mt-1">ABC12345</p>
                                        </div>
                                    </div>
                                    <div class="h-12 w-48 bg-black -mb-8"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="relative flex items-center justify-center w-full md:w-[375px] rounded-3xl">
                    <img src="../assets/summary.jpg" alt="Flight map"
                        class="rounded-lg w-full h-full object-cover object-center">
                    <div
                        class="absolute top-[13%] end-[5%] min-w-[93px] min-h-[32px] bg-white/80 backdrop-blur-sm rounded shadow-sm border border-gray-200 flex items-center justify-center text-sm font-500">
                        <div class="flex items-center gap-2 p-1">
                            <img src="https://justfields.com/storage/projects/7M5rV059/img-0100.jpg" alt="Reviewer"
                                class="w-8 h-8 rounded-sm">
                            <div>
                                <p class="font-600 text-xs">Amr Mohamed</p>
                                <p class="font-400 text-xs">Boarding Pass N’123</p>
                            </div>
                        </div>
                    </div>
                    <div
                        class="absolute bottom-[16%] start-[5%] min-w-[93px] min-h-[32px] bg-white/80 backdrop-blur-sm rounded shadow-sm border border-gray-200 flex items-center justify-center text-sm font-500 p-1">
                        <div class="flex items-center gap-2 p-1">
                            <img src="https://justfields.com/storage/projects/7M5rV059/img-0100.jpg" alt="reviewer"
                                class="w-8 h-8 rounded-sm">
                            <div>
                                <p class="font-600 text-xs">Amr Mohamed</p>
                                <p class="font-400 text-xs">Boarding Pass N’123</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="mt-16">
                <p class="text-2xl font-600 text-color">Terms and Conditions</p>
                <div class="mt-[34px]">
                    <h2 class="text-xl font-500 text-color mb-4">Payments</h2>
                    <ul class="space-y-4 text-color ps-0 list-disc">
                        <li class="text-sm font-400 ms-7">
                            If you are purchasing your ticket using a debit or credit card via the Website, we will
                            process these payments via the automated secure common payment gateway which will be
                            subject to fraud screening purposes.
                        </li>
                        <li class="text-sm font-400 ms-7">
                            If you do not supply the correct card billing address and/or cardholder information,
                            your booking will not be confirmed and the overall cost may increase. We reserve the
                            right to cancel your booking if payment is declined for any reason or if you have
                            supplied incorrect card information. If we become aware of, or is notified of, any fraud
                            or illegal activity associated with the payment for the booking, the booking will be
                            cancelled and you will be liable for all costs and expenses arising from such
                            cancellation, without prejudice to any action that may be taken against us.
                        </li>
                        <li class="text-sm font-400 ms-7">
                            Golobe may require the card holder to provide additional payment verification upon
                            request by either submitting an online form or visiting the nearest Golobe office, or at
                            the airport at the time of check-in. Golobe reserves the right to deny boarding or to
                            collect a guarantee payment (in cash or from another credit card) if the card originally
                            used for the purchase cannot be presented by the cardholder at check-in or when
                            collecting the tickets, or in the case the original payment has been withheld or
                            disputed by the card issuing bank. Credit card details are held in a secured environment
                            and transferred through an internationally accepted system.
                        </li>
                    </ul>
                </div>

                <div class="bg-gray-50 mt-[34px]">
                    <h2 class="text-xl font-500 text-color mb-4">Contact Us</h2>
                    <div class="text-color">
                        <p class="text-sm font-400">If you have any questions about our Website or our Terms of Use,
                            please
                            contact:</p>
                        <div class="text-sm font-400 space-y-1">
                            <p>Colobe Group QC.S.C</p>
                            <p>Colobe Tower</p>
                            <p>P.O. Box 22550</p>
                            <p>Doha Suite of Qatar</p>
                        </div>
                        <p class="text-sm font-400">
                            Further contact details can be found at
                            <a href="" class="text-blue-600 underline">golobec.com/help</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>