<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const sectionRef = ref(null)
const isVisible = ref(false)

let observer

onMounted(() => {
  observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        isVisible.value = true
      }
    },
    {
      threshold: 0.25,
    }
  )

  if (sectionRef.value) {
    observer.observe(sectionRef.value)
  }
})

onBeforeUnmount(() => {
  if (observer && sectionRef.value) {
    observer.unobserve(sectionRef.value)
  }
})
</script>

<template>
  <section
    id="about"
    ref="sectionRef"
    class="relative w-full overflow-hidden bg-slate-900 px-6 py-24 text-white md:px-16 lg:px-24 xl:px-32"
  >
    <div class="absolute inset-0 -z-10">
      <div
        class="absolute left-1/4 top-10 h-72 w-72 rounded-full bg-cyan-400/10 blur-3xl transition-all duration-1000"
        :class="isVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-75'"
      />
      <div
        class="absolute bottom-10 right-1/4 h-72 w-72 rounded-full bg-blue-500/10 blur-3xl transition-all duration-1000 delay-200"
        :class="isVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-75'"
      />
    </div>

    <div class="mx-auto grid max-w-7xl grid-cols-1 items-center gap-14 md:grid-cols-2">
      <div
        class="flex justify-center md:justify-start transition-all duration-1000 ease-out"
        :class="isVisible ? 'translate-x-0 opacity-100' : '-translate-x-12 opacity-0'"
      >
        <div class="relative group">
          <div
            class="absolute inset-0 rounded-[2rem] bg-cyan-400/10 blur-3xl transition-all duration-500 group-hover:bg-cyan-400/20"
          />

          <div
            class="relative h-[340px] w-[270px] overflow-hidden rounded-[2rem] border border-cyan-400/30 bg-slate-950 shadow-[0_0_50px_rgba(34,211,238,0.12)] transition-all duration-500 group-hover:-translate-y-2 group-hover:scale-[1.02] group-hover:shadow-[0_0_60px_rgba(34,211,238,0.22)] sm:h-[400px] sm:w-[320px] lg:h-[460px] lg:w-[360px]"
          >
            <img
              src="/profile.png"
              alt="About profile"
              class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-105"
            />
          </div>
        </div>
      </div>

      <div
        class="max-w-2xl transition-all duration-1000 ease-out"
        :class="isVisible ? 'translate-x-0 opacity-100' : 'translate-x-12 opacity-0'"
      >
        <p
          class="mb-3 text-sm font-semibold uppercase tracking-[0.2em] text-cyan-400/80 transition-all delay-100 duration-700"
          :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-4 opacity-0'"
        >
          About Me
        </p>

        <h2
          class="text-3xl font-extrabold leading-tight transition-all delay-200 duration-700 sm:text-4xl lg:text-5xl"
          :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-4 opacity-0'"
        >
          Building clean and modern
          <span class="text-cyan-400">web experiences</span>
        </h2>

        <h3
          class="mt-4 text-lg font-medium text-slate-300 transition-all delay-300 duration-700 sm:text-xl"
          :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-4 opacity-0'"
        >
          Fullstack Developer / Prompt Engineer
        </h3>

        <p
          class="mt-6 text-base leading-8 text-slate-400 transition-all delay-500 duration-700 sm:text-lg"
          :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-4 opacity-0'"
        >
          I’m passionate about building modern, responsive web applications that
          combine clean design with practical functionality. I focus on creating
          user-friendly interfaces and scalable systems that deliver real value.
        </p>

        <p
          class="mt-4 text-base leading-8 text-slate-400 transition-all delay-700 duration-700 sm:text-lg"
          :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-4 opacity-0'"
        >
          I work efficiently and can quickly turn ideas into fully functional
          applications while maintaining clean and maintainable code. I’m also
          highly adaptable and comfortable working with different technologies
          and programming languages depending on project needs.
        </p>
      </div>
    </div>
  </section>
</template>