<script setup lang="ts">
const showAddCardModal = ref(false)
const isLoading = ref(false)

const cardForm = ref({
    cardNumber: '',
    expiration: '',
    cvv: '',
    cardholderName: '',
    country: ''
})

const openAddCardModal = () => {
    showAddCardModal.value = true
}

const closeAddCardModal = () => {
    showAddCardModal.value = false
    // Reset form when closing
    cardForm.value = {
        cardNumber: '',
        expiration: '',
        cvv: '',
        cardholderName: '',
        country: ''
    }
}

const handleSubmit = async () => {
    isLoading.value = true
    try {
        // Simulate API call
        await new Promise(resolve => setTimeout(resolve, 3000))
        console.log('Card details submitted:', cardForm.value)
    } finally {
        isLoading.value = false
        showAddCardModal.value = false
    }
}
</script>

<template>
    <div>
        <!-- dialog btn -->
        <div class="text-center cursor-pointer" @click="openAddCardModal">
                <icon name="material-symbols:add-circle-outline" class="text-[#8DD3BB] w-12 h-12 mx-auto" aria-hidden="true" />
            <div class="mt-2.5 flex text-sm/6 text-gray-600">
                <button role="button" class="text-xs font-500">Add a new
                    card</button>
            </div>
        </div>

        <div v-if="showAddCardModal"
            class="fixed inset-0 p-4 flex flex-wrap justify-center items-center w-full h-full z-[1000] before:fixed before:inset-0 before:w-full before:h-full before:bg-[rgba(0,0,0,0.5)] overflow-auto">
            <div class="w-full max-w-xl bg-white shadow-lg 2xl p-6 relative">
                <div class="flex items-center pb-3 border-b border-gray-300">
                    <h3 class="text-slate-900 text-2xl font-700 flex-1 text-start">Add new Card</h3>
                    <icon name="material-symbols:close-small-rounded"
                        class="ms-2 cursor-pointer shrink-0 text-gray-400 hover:text-red-500"
                        @click="closeAddCardModal"></icon>
                </div>

                <form @submit.prevent="handleSubmit">
                    <div class="my-6 space-y-4">
                        <div class="relative">
  <label class="block text-sm font-500 text-gray-700 mb-1 text-start">Card Number</label>
  <div class="relative">
    <input 
      v-model="cardForm.cardNumber" 
      type="text" 
      placeholder="1234 5678 9012 3456"
      class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#8DD3BB] focus:border-[#8DD3BB] pr-10"
    >
    <div class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none">
      <icon 
        name="cib:cc-visa" 
        class="text-[#1434CB] w-6 h-[15px]"
      />
    </div>
  </div>
</div>

                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label class="block text-sm font-500 text-gray-700 mb-1 text-start">Exp. Date</label>
                                <input v-model="cardForm.expiration" type="text" placeholder="MM/YY"
                                    class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#8DD3BB]" />
                            </div>

                            <div>
                                <label class="block text-sm font-500 text-gray-700 mb-1 text-start">CVV</label>
                                <input v-model="cardForm.cvv" type="text" placeholder="123"
                                    class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#8DD3BB]" />
                            </div>
                        </div>

                        <div>
                            <label class="block text-sm font-500 text-gray-700 mb-1 text-start">Cardholder
                                Name</label>
                            <input v-model="cardForm.cardholderName" type="text" placeholder="John Doe"
                                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#8DD3BB]" />
                        </div>

                        <div>
                            <label class="block text-sm font-500 text-gray-700 mb-1 text-start">Country or
                                Region</label>
                            <select v-model="cardForm.country"
                                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#8DD3BB] focus:border-[#8DD3BB]">
                                <option value="" disabled>Select Country</option>
                                <option value="US">United States</option>
                                <option value="CA">Canada</option>
                                <option value="GB">United Kingdom</option>
                                <option value="AU">Australia</option>
                                <option value="DE">Germany</option>
                            </select>
                        </div>

                        <div class="flex items-center py-4">
                            <input id="save_info" type="checkbox"
                                class="text-black border border-gray-300 shadow-sm focus:border-gray-300 focus:ring focus:ring-gray-200 focus:ring-opacity-50" />
                            <label for="save_info" class="block ms-2 text-sm font-500 leading-5 text-gray-900">
                                Securely save my information for 1-click checkout
                            </label>
                        </div>

                        <div class="border-gray-300 flex justify-end gap-4">
                            <button type="submit" @click="handleSubmit"
                                class="px-4 py-2 rounded-lg block w-full text-color font-600 bg-[#8DD3BB] hover:bg-[#7bc3ab]">
                                <div class="flex items-center justify-center" v-if="isLoading">
                                    <icon name="line-md:loading-twotone-loop"></icon>
                                </div>
                                <span v-else>Add Card</span>
                            </button>
                        </div>
                    </div>
                </form>
                <div>
                    <p class="text-center font-400 text-xs">By confirming your subscription, you allow The Outdoor Inn
                        Crowd Limited to charge your card for this payment and future payments in accordance with their
                        terms. You can always cancel your subscription.</p>
                </div>
            </div>
        </div>
    </div>
</template>