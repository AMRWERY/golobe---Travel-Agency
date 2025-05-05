<script setup lang="ts">

</script>

<template>
  <div>
    <!-- Hero Section for non-home pages -->
    <hero />
    
    <div class="h-1 sm:h-10 md:h-80"></div>

    <div class="mx-auto md:w-full md:max-w-[1232px] px-4 md:px-0">

      <!-- results component -->
      <results type="flights" />
      
      <!-- fallInto component -->
      <fall-into type="flights" />
    </div>
  </div>
</template>