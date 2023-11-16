<script setup>
  const props = defineProps({
      post: {
        type: Object,
        default: () => {}
      },
  })
</script>

<template>

  <li class="w-full h-[44px] hover:bg-[#EEEEEE] hover:duration-300 hover:text-black text-[#2E2E2E] flex items-center pl-[16px] rounded-xl mb-[16px]">
    <img :src=props.post.imagePath width="16" height="16" alt="" class="mr-[18px]">
    <a href="" class="text-xl">{{props.post.text}}</a>
  </li>
</template>

<style scoped>

</style>