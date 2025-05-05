<script lang="ts" setup>

</script>

<template>
  <div>
    <h3 class="text-[32px] font-700 mb-4 mt-10">Payment methods</h3>

    <div class="bg-white rounded-xl shadow p-6">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <!-- Existing Card -->
        <div
          class="bg-[#8dd3bb] rounded-2xl shadow-sm p-6 border border-[#8DD3BB] min-h-[200px] flex flex-col justify-between">
          <div class="flex justify-between items-start">
            <div class="text-gray-900 space-y-4">
              <span class="text-xl tracking-widest">**** **** ****</span>
              <p class="text-2xl font-bold">4321</p>
            </div>
            <button class="text-red-600 hover:text-red-700">
              <icon name="material-symbols:delete-sharp" class="w-6 h-6" />
            </button>
          </div>
          <div class="flex justify-between items-end">
            <div>
              <p class="text-sm text-gray-600">Valid Thru</p>
              <p class="text-lg font-semibold text-gray-900">02/27</p>
            </div>
            <div class="flex items-center justify-center">
              <icon name="logos:visa" class="w-[70px] h-[44px]" />
            </div>
          </div>
        </div>

        <!-- Add New Card -->
        <button
          class="bg-white rounded-2xl shadow-sm p-6 border-2 border-dashed border-[#8DD3BB] hover:border-[#7bc3ab] transition-colors">
          <div class="h-full flex flex-col items-center justify-center gap-3">
            <div class="w-12 h-12 bg-[#8DD3BB]/10 rounded-full flex items-center justify-center">
              <icon name="heroicons:plus" class="w-6 h-6 text-[#8DD3BB]" />
            </div>
            <p class="text-[#8DD3BB] font-semibold">Add a new card</p>
          </div>
        </button>
      </div>
    </div>
  </div>
</template>