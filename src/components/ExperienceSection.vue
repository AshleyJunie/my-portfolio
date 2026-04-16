<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { Badge } from '@/components/ui/badge'
import { BriefcaseBusiness, CalendarDays, MapPin } from 'lucide-vue-next'

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
    id="experience"
    ref="sectionRef"
    class="relative w-full overflow-hidden bg-slate-950 px-6 py-20 text-white md:px-12 lg:px-20 xl:px-28"
  >
    <!-- background glow -->
    <div
      class="absolute inset-0 transition-opacity duration-1000"
      :class="isVisible ? 'opacity-100' : 'opacity-0'"
    >
      <div class="absolute left-20 top-20 h-64 w-64 rounded-full bg-cyan-400/5 blur-3xl" />
      <div class="absolute right-20 bottom-20 h-64 w-64 rounded-full bg-purple-400/5 blur-3xl" />
    </div>

    <div class="relative mx-auto max-w-6xl">
      <!-- Header -->
      <div
        class="mb-12 text-center transition-all duration-1000"
        :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'"
      >
        <p class="mb-3 text-sm font-semibold uppercase tracking-[0.18em] text-cyan-400/80">
          Experience
        </p>

        <h2 class="text-3xl font-extrabold sm:text-4xl lg:text-5xl">
          Work <span class="text-cyan-400">Experience</span>
        </h2>

        <p class="mx-auto mt-4 max-w-3xl text-slate-400">
          A summary of my internship contribution in application development and technical operations.
        </p>
      </div>

      <!-- MAIN CARD (zoom-in effect) -->
      <div
        class="overflow-hidden rounded-3xl border border-white/10 bg-white/5 transition-all duration-1000"
        :class="isVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-95'"
      >
        <div class="grid lg:grid-cols-[300px_minmax(0,1fr)]">
          
          <!-- LEFT PANEL -->
          <div
            class="border-b border-white/10 bg-white/[0.03] p-6 lg:border-b-0 lg:border-r transition-all duration-1000"
            :class="isVisible ? 'translate-x-0 opacity-100' : '-translate-x-12 opacity-0'"
          >
            <div class="flex items-start gap-4">
              <div class="flex h-16 w-16 items-center justify-center rounded-2xl border border-white/10 bg-white/10 p-2">
                <img src="/favicon.ico" class="h-full w-full object-contain" />
              </div>

              <div>
                <h3 class="text-xl font-semibold text-white">
                  DENR MIMAROPA Regional Office
                </h3>
                <p class="text-sm text-slate-400">
                  On-the-Job Training
                </p>
              </div>
            </div>

            <div class="mt-6 space-y-5">
              <div class="flex gap-3 text-sm text-slate-400">
                <BriefcaseBusiness class="h-4 w-4 text-cyan-400" />
                <div>
                  <p class="text-slate-300 font-medium">Position</p>
                  <p>Application Developer</p>
                </div>
              </div>

              <div class="flex gap-3 text-sm text-slate-400">
                <CalendarDays class="h-4 w-4 text-cyan-400" />
                <div>
                  <p class="text-slate-300 font-medium">Duration</p>
                  <p>Feb – May 2026</p>
                </div>
              </div>

              <div class="flex gap-3 text-sm text-slate-400">
                <MapPin class="h-4 w-4 text-cyan-400" />
                <div>
                  <p class="text-slate-300 font-medium">Office</p>
                  <p>DENR MIMAROPA</p>
                </div>
              </div>
            </div>
          </div>

          <!-- RIGHT PANEL -->
          <div
            class="p-6 md:p-8 transition-all duration-1000 delay-150"
            :class="isVisible ? 'translate-x-0 opacity-100' : 'translate-x-12 opacity-0'"
          >
            <h3 class="text-2xl font-bold text-white">
              Application Developer (OJT)
            </h3>

            <p class="mt-6 text-slate-400">
              Completed internship delivering internal web solutions while supporting day-to-day technical requests.
            </p>

            <!-- RESPONSIBILITIES (stagger animation) -->
            <ul class="mt-6 space-y-3">
              <li
                v-for="(item, i) in [
                  'Built and maintained fullstack web modules',
                  'Prepared clear technical documentation',
                  'Resolved software and hardware issues',
                  'Supported basic network setup and configuration'
                ]"
                :key="i"
                class="flex gap-3 text-slate-400 transition-all duration-500"
                :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'"
                :style="{ transitionDelay: `${300 + i * 120}ms` }"
              >
                <span class="mt-[10px] h-1.5 w-1.5 rounded-full bg-cyan-400" />
                <span>{{ item }}</span>
              </li>
            </ul>

            <!-- BADGES (pop animation) -->
            <div class="mt-6 flex flex-wrap gap-2">
              <Badge
                v-for="(tech, i) in ['Laravel', 'Vue', 'MySQL', 'Tailwind']"
                :key="tech"
                class="transition-all duration-500"
                :class="isVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-75'"
                :style="{ transitionDelay: `${500 + i * 100}ms` }"
              >
                {{ tech }}
              </Badge>
            </div>

            <!-- Highlight box -->
            <div
              class="mt-8 rounded-2xl border border-white/10 bg-white/[0.03] p-5 transition-all duration-700"
              :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
              style="transition-delay: 700ms"
            >
              <h5 class="text-white font-semibold">Experience Highlight</h5>
              <p class="text-slate-400 mt-3">
                Strengthened fullstack delivery, communication, and real-world IT support capability.
              </p>
            </div>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>
