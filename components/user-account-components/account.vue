<script lang="ts" setup>

</script>

<template>
  <div>
    <h3 class="text-[32px] font-700 mb-4 mt-10">Account</h3>

    <div class="bg-white w-full h-auto px-6 py-8 rounded-2xl shadow">
      <ul class="space-y-8">
        <li class="flex items-center justify-between">
          <div class="flex-1 items-center">
            <p class="text-gray-600 text-base font-400 capitalize">name</p>
            <h3 class="text-xl font-600 text-gray-800">Emily Jones</h3>
          </div>
          <button role="button"
            class="px-4 gap-2 py-2 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize hidden md:flex items-center justify-center">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
            <span class="text-sm font-500">change</span>
          </button>
          <button role="button"
            class="p-2.5 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize flex md:hidden items-center justify-center rounded-full">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
          </button>
        </li>
        <li class="flex items-center justify-between">
          <div class="flex-1 items-center">
            <p class="text-gray-600 text-base font-400 capitalize">email</p>
            <h3 class="text-xl font-600 text-gray-800">john.doe@gmail.com</h3>
          </div>
          <div class="flex items-center gap-2">
            <button role="button"
              class="px-4 gap-2 py-2 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize hidden md:flex items-center justify-center">
              <icon name="material-symbols:add-circle" class="w-4 h-4" />
              <span class="text-sm font-500">Add another email</span>
            </button>
            <button role="button"
              class="p-2.5 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize flex md:hidden items-center justify-center rounded-full">
              <icon name="material-symbols:add-circle" class="w-4 h-4" />
            </button>
            <button role="button"
              class="px-4 gap-2 py-2 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize hidden md:flex items-center justify-center">
              <icon name="material-symbols:edit-square" class="w-4 h-4" />
              <span class="text-sm font-500">change</span>
            </button>
            <button role="button"
              class="p-2.5 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize flex md:hidden items-center justify-center rounded-full">
              <icon name="material-symbols:edit-square" class="w-4 h-4" />
            </button>
          </div>
        </li>
        <li class="flex items-center justify-between">
          <div class="flex-1 items-center">
            <p class="text-gray-600 text-base font-400 capitalize">password</p>
            <h3 class="text-xl font-600 text-gray-800">********</h3>
          </div>
          <button role="button"
            class="px-4 gap-2 py-2 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize hidden md:flex items-center justify-center">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
            <span class="text-sm font-500">change</span>
          </button>
          <button role="button"
            class="p-2.5 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize flex md:hidden items-center justify-center rounded-full">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
          </button>
        </li>
        <li class="flex items-center justify-between">
          <div class="flex-1 items-center">
            <p class="text-gray-600 text-base font-400 capitalize">Phone number</p>
            <h3 class="text-xl font-600 text-gray-800">+1 000-000-0000</h3>
          </div>
          <button role="button"
            class="px-4 gap-2 py-2 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize hidden md:flex items-center justify-center">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
            <span class="text-sm font-500">change</span>
          </button>
          <button role="button"
            class="p-2.5 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize flex md:hidden items-center justify-center rounded-full">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
          </button>
        </li>
        <li class="flex items-center justify-between">
          <div class="flex-1 items-center">
            <p class="text-gray-600 text-base font-400 capitalize">Address</p>
            <h3 class="text-xl font-600 text-gray-800">St 32 main downtown, Los Angeles, California, USA</h3>
          </div>
          <button role="button"
            class="px-4 gap-2 py-2 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize hidden md:flex items-center justify-center">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
            <span class="text-sm font-500">change</span>
          </button>
          <button role="button"
            class="p-2.5 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize flex md:hidden items-center justify-center rounded-full">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
          </button>
        </li>
        <li class="flex items-center justify-between">
          <div class="flex-1 items-center">
            <p class="text-gray-600 text-base font-400 capitalize">Date of birth</p>
            <h3 class="text-xl font-600 text-gray-800">01-01-1992</h3>
          </div>
          <button role="button"
            class="px-4 gap-2 py-2 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize hidden md:flex items-center justify-center">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
            <span class="text-sm font-500">change</span>
          </button>
          <button role="button"
            class="p-2.5 border border-[#8DD3BB] hover:bg-[#8DD3BB] hover:text-white transition-colors text-sm font-500 capitalize flex md:hidden items-center justify-center rounded-full">
            <icon name="material-symbols:edit-square" class="w-4 h-4" />
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>