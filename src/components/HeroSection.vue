<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { Button } from '@/components/ui/button'
import { Github, Linkedin, Mail, Facebook } from 'lucide-vue-next'

const roles = [
  'Fullstack Developer',
  'Software Developer',
  'Freelance Developer',
]

const displayedRole = ref('')
const roleIndex = ref(0)
const charIndex = ref(0)
const isDeleting = ref(false)

let timer = null

const typingSpeed = 90
const deletingSpeed = 45
const pauseAfterTyping = 1400
const pauseBeforeTyping = 250

function runTypingEffect() {
  const currentRole = roles[roleIndex.value]

  if (!isDeleting.value) {
    displayedRole.value = currentRole.slice(0, charIndex.value + 1)
    charIndex.value++

    if (charIndex.value === currentRole.length) {
      isDeleting.value = true
      timer = setTimeout(runTypingEffect, pauseAfterTyping)
      return
    }

    timer = setTimeout(runTypingEffect, typingSpeed)
  } else {
    displayedRole.value = currentRole.slice(0, charIndex.value - 1)
    charIndex.value--

    if (charIndex.value === 0) {
      isDeleting.value = false
      roleIndex.value = (roleIndex.value + 1) % roles.length
      timer = setTimeout(runTypingEffect, pauseBeforeTyping)
      return
    }

    timer = setTimeout(runTypingEffect, deletingSpeed)
  }
}

onMounted(() => {
  runTypingEffect()
})

onBeforeUnmount(() => {
  if (timer) clearTimeout(timer)
})
</script>

<template>
  <section
    id="home"
    class="relative flex min-h-[100vh] w-full items-center overflow-hidden bg-slate-950 text-white"
  >
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_75%_45%,rgba(34,211,238,0.16),transparent_26%)]" />

    <div
      class="relative grid w-full grid-cols-1 items-center gap-14 px-6 py-24 md:min-h-[100vh] md:grid-cols-2 md:px-16 lg:px-24 xl:px-32"
    >
      <div class="mx-auto w-full max-w-2xl md:mx-0">
        <p class="mb-4 text-lg font-medium text-slate-200">
          Hello, It's Me
        </p>

        <h1 class="text-5xl font-extrabold leading-none sm:text-6xl lg:text-[72px]">
          Ashley
        </h1>

        <h2 class="mt-4 text-2xl font-bold sm:text-3xl lg:text-4xl">
          And I'm a
          <span class="ml-2 inline-flex min-w-[340px] text-cyan-400">
            {{ displayedRole }}
            <span class="ml-1 inline-block h-[1em] w-[2px] animate-pulse bg-cyan-400 align-middle" />
          </span>
        </h2>

        <p class="mt-6 max-w-xl text-base leading-8 text-slate-400 sm:text-lg">
I build modern, scalable web applications with a focus on clean design and practical functionality. I leverage modern tools to work efficiently and deliver high-quality systems. I’m highly adaptable and can quickly work with different technologies and programming languages.
        </p>

        <div class="mt-8 flex flex-wrap items-center gap-3">
          <a
            href="https://www.facebook.com/ashley.paglicawann"
            target="_blank"
            class="flex h-11 w-11 items-center justify-center rounded-full border border-cyan-400/70 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
          >
            <Facebook class="h-4 w-4" />
          </a>

          <a
            href="https://github.com/AshleyJunie"
            target="_blank"
            class="flex h-11 w-11 items-center justify-center rounded-full border border-cyan-400/70 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
          >
            <Github class="h-4 w-4" />
          </a>

          <a
            href="https://www.linkedin.com/in/ashley-junie-paglicawan-4a49883b2/"
            target="_blank"
            class="flex h-11 w-11 items-center justify-center rounded-full border border-cyan-400/70 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
          >
            <Linkedin class="h-4 w-4" />
          </a>

          <a
            href="#"
            class="flex h-11 w-11 items-center justify-center rounded-full border border-cyan-400/70 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
          >
            <Mail class="h-4 w-4" />
          </a>
        </div>

        <div class="mt-10">
          <Button
            class="rounded-xl bg-cyan-400 px-8 py-6 text-base font-medium text-slate-950 shadow-[0_10px_30px_rgba(34,211,238,0.18)] transition-all duration-200 hover:bg-cyan-300 hover:shadow-[0_12px_36px_rgba(34,211,238,0.22)]"
          >
            Download CV
          </Button>
        </div>
      </div>

      <div class="flex items-center justify-center md:justify-end">
        <div class="relative">
          <div class="absolute inset-0 rounded-[2rem] bg-cyan-400/20 blur-3xl" />

          <div
            class="relative h-[360px] w-[280px] overflow-hidden rounded-[2rem] border border-cyan-400/40 bg-slate-900 shadow-[0_0_60px_rgba(34,211,238,0.18)] sm:h-[430px] sm:w-[330px] lg:h-[520px] lg:w-[400px]"
          >
            <img
              src="/profile.png"
              alt="Profile"
              class="h-full w-full object-cover"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>