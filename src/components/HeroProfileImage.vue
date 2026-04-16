<script setup>
defineProps({
  imageClass: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div class="relative">
    <div class="absolute inset-0 rounded-[2rem] bg-cyan-400/20 blur-3xl" />

    <div
      :class="[
        'relative overflow-hidden rounded-[2rem] border border-cyan-400/40 bg-slate-900 shadow-[0_0_60px_rgba(34,211,238,0.18)]',
        imageClass,
      ]"
    >
      <img
        src="/profile.png"
        alt="Profile"
        class="h-full w-full object-cover"
      />
    </div>
  </div>
</template>
