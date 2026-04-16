<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const educationTimeline = [
  {
    school: 'Datacom Institute of Computer Technology',
    details: 'Rosario Branch • 1 Semester',
    description:
      'Attended a 1-semester workshop during senior high school to further strengthen my technical and computer-related skills.',
    type: 'award',
  },
  {
    school: 'Dean’s Lister',
    details: '2022 – 2026',
    description:
      'Consistently recognized as Dean’s Lister across multiple academic years.',
    type: 'award',
  },
  {
    school: 'President’s Lister',
    details: '2023 – 2024',
    description:
      'Awarded President’s Lister for outstanding academic performance.',
    type: 'award',
  },
  {
    school: 'Cum Laude',
    details: 'Graduated with Latin Honors',
    description:
      'Graduated with Cum Laude distinction, reflecting strong academic performance throughout college.',
    type: 'highlight',
  },
]

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
    { threshold: 0.2 }
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
    id="education"
    ref="sectionRef"
    class="w-full overflow-hidden bg-slate-950 px-6 py-20 text-white md:px-12 lg:px-20 xl:px-28"
  >
    <div class="mx-auto max-w-6xl">
      <!-- Header -->
      <div
        class="mb-12 transition-all duration-1000 ease-out"
        :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'"
      >
        <p class="mb-2 text-sm font-semibold uppercase tracking-[0.18em] text-cyan-400/80">
          Education
        </p>

        <h2 class="text-3xl font-extrabold leading-tight sm:text-4xl lg:text-5xl">
          Education &
          <span class="text-cyan-400">Academic Honors</span>
        </h2>

        <p class="mt-4 max-w-3xl text-base leading-7 text-slate-400 sm:text-lg">
          My academic background reflects consistent excellence, strong technical foundations,
          and a commitment to continuous learning in the field of technology and software development.
        </p>
      </div>

      <!-- School cards -->
      <div class="space-y-5">
        <!-- Senior High School -->
        <div
          class="flex items-start gap-4 rounded-2xl border border-white/10 bg-white/5 p-4 transition-all duration-1000 ease-out hover:-translate-y-1 hover:border-cyan-400/20 hover:bg-white/[0.07]"
          :class="isVisible ? 'translate-x-0 opacity-100' : '-translate-x-16 opacity-0'"
        >
          <img
            src="/shs-logo.png"
            alt="Senior High School logo"
            class="h-14 w-14 rounded-xl bg-white p-1 object-contain"
          />

          <div>
            <h3 class="text-xl font-semibold text-white">
              Cavite National High School - Senior High School
            </h3>
            <p class="mt-1 text-slate-300">
              Information and Communications Technology (ICT) - TVL
            </p>
            <p class="text-slate-400">
              Cavite City, Cavite, Philippines
            </p>
          </div>
        </div>

        <!-- College -->
        <div
          class="flex items-start gap-4 rounded-2xl border border-white/10 bg-white/5 p-4 transition-all duration-1000 delay-150 ease-out hover:-translate-y-1 hover:border-cyan-400/20 hover:bg-white/[0.07]"
          :class="isVisible ? 'translate-x-0 opacity-100' : 'translate-x-16 opacity-0'"
        >
          <img
            src="/school-logo.png"
            alt="Cavite State University logo"
            class="h-14 w-14 rounded-xl bg-white p-1 object-contain"
          />

          <div>
            <h3 class="text-xl font-semibold text-white">
              Cavite State University – Cavite City Campus
            </h3>
            <p class="mt-1 text-slate-300">
              Bachelor of Science in Information Technology
            </p>
            <p class="text-slate-400">
              Cavite City, Cavite, Philippines
            </p>

            <div class="mt-3 flex flex-wrap gap-2">
              <span class="rounded-full border border-cyan-400/30 bg-cyan-400/10 px-3 py-1 text-sm font-medium text-cyan-300">
                Cum Laude
              </span>
              <span class="rounded-full border border-white/10 bg-white/5 px-3 py-1 text-sm font-medium text-slate-300">
                Dean's Lister
              </span>
              <span class="rounded-full border border-amber-400/30 bg-amber-400/10 px-3 py-1 text-sm font-medium text-amber-300">
                President's Lister
              </span>
            </div>
          </div>
        </div>
      </div>

      <!-- Timeline -->
      <div class="mt-12 space-y-8">
        <div
          v-for="(item, index) in educationTimeline"
          :key="`${item.school}-${index}`"
          class="grid grid-cols-[28px_1fr] gap-4 transition-all duration-700 ease-out"
          :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-8 opacity-0'"
          :style="{ transitionDelay: `${250 + index * 140}ms` }"
        >
          <div class="flex flex-col items-center">
            <div
              class="mt-1 h-3.5 w-3.5 rounded-full border-2 border-slate-950 transition-all duration-700"
              :class="[item.type === 'highlight' ? 'bg-amber-400' : 'bg-cyan-400']"
            />

            <div
              v-if="index !== educationTimeline.length - 1"
              class="mt-2 w-px origin-top bg-white/10 transition-transform duration-700"
              :class="isVisible ? 'scale-y-100' : 'scale-y-0'"
              :style="{ transitionDelay: `${350 + index * 140}ms` }"
            />
          </div>

          <div class="pb-2">
            <div class="flex flex-col gap-1 sm:flex-row sm:items-center sm:justify-between">
              <h3 class="text-lg font-semibold text-white">
                {{ item.school }}
              </h3>

              <span
                class="text-sm font-medium"
                :class="item.type === 'highlight' ? 'text-amber-300' : 'text-slate-300'"
              >
                {{ item.details }}
              </span>
            </div>

            <p class="mt-2 max-w-3xl text-sm leading-7 text-slate-400 sm:text-base">
              {{ item.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
