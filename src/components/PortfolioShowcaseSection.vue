<script setup>
import { computed, ref } from 'vue'
import {
  Tabs,
  TabsContent,
  TabsList,
  TabsTrigger,
} from '@/components/ui/tabs'
import { Badge } from '@/components/ui/badge'
import { Button } from '@/components/ui/button'
import {
  FolderKanban,
  Award,
  Boxes,
  ExternalLink,
  Github,
  ArrowLeft,
  ChevronRight,
  Code2,
  Layers3,
  Star,
} from 'lucide-vue-next'

const selectedProject = ref(null)

const projects = [
  {
    slug: 'holy-trinity-church-website',
    title: 'Holy Trinity Christian Community Church Website',
    category: 'Capstone Project',
    image: '/projects/church-website.png',
    description:
      'A church website developed to provide an online presence, share announcements, present ministry information, and make important content accessible to the community.',
    techStack: ['Laravel', 'Vue', 'MySQL', 'Tailwind CSS'],
    role: 'Fullstack Developer',
    features: [
      'Responsive and modern website layout',
      'Church information and content sections',
      'Announcement and update presentation',
      'Clean and user-friendly design',
    ],
    github: '#',
    liveDemo: '#',
  },
  {
    slug: 'ojt-attendance-tracking-system',
    title: 'OJT Attendance Tracking System',
    category: 'DENR',
    image: '/projects/ojt-attendance.png',
    description:
      'A web-based attendance tracking system created to monitor and manage OJT attendance records efficiently.',
    techStack: ['Laravel', 'MySQL', 'Blade', 'Bootstrap'],
    role: 'Fullstack Developer',
    features: [
      'Attendance monitoring and record management',
      'Student/intern tracking',
      'Admin dashboard',
      'Report generation support',
    ],
    github: '#',
    liveDemo: '#',
  },
  {
    slug: 'technical-assistance-ticketing-system',
    title: 'Technical Assistance Ticketing System',
    category: 'DENR',
    image: '/projects/technical-assistance.png',
    description:
      'A ticketing and history tracking system designed to record technical concerns, monitor progress, and maintain issue history for reference.',
    techStack: ['Laravel', 'MySQL', 'JavaScript', 'Bootstrap'],
    role: 'Fullstack Developer',
    features: [
      'Ticket creation and issue logging',
      'Concern history tracking',
      'Status monitoring',
      'Organized technical assistance records',
    ],
    github: '#',
    liveDemo: '#',
  },
]

const displayedProjects = computed(() => projects.slice(0, 6))

const certificates = [
  { title: 'Certificate 1', image: '/certificates/certificate-1.png' },
  { title: 'Certificate 2', image: '/certificates/certificate-2.png' },
  { title: 'Certificate 3', image: '/certificates/certificate-1.png' },
  { title: 'Certificate 4', image: '/certificates/certificate-2.png' },
  { title: 'Certificate 5', image: '/certificates/certificate-1.png' },
  { title: 'Certificate 6', image: '/certificates/certificate-2.png' },
]

const techStack = [
  {
    name: 'HTML',
    logo: '/tech/html.png',
  },
  {
    name: 'CSS',
    logo: '/tech/css-3.png',
  },
  {
    name: 'JavaScript',
    logo: '/tech/js.png',
  },
  {
    name: 'Tailwind CSS',
    logo: '/tech/tailwind.png',
  },
  {
    name: 'Java',
    logo: '/tech/java.png',
  },
  {
    name: 'Vite',
    logo: '/tech/vite.png',
  },
  {
    name: 'PHP',
    logo: '/tech/php.png',
  },
  {
    name: 'Python',
    logo: '/tech/python.png',
  },
  {
    name: 'Laravel',
    logo: '/tech/laravel.png',
  },
  {
    name: 'MySQL',
    logo: '/tech/mysql.png',
  },
]

const openProjectDetails = (project) => {
  selectedProject.value = project
}

const closeProjectDetails = () => {
  selectedProject.value = null
}
</script>

<template>
  <section
    id="projects"
    class="relative w-full overflow-hidden bg-slate-950 px-5 py-20 text-white md:px-10 lg:px-16 xl:px-24"
  >
    <div
      class="absolute inset-0 bg-[radial-gradient(circle_at_12%_28%,rgba(168,85,247,0.18),transparent_24%),radial-gradient(circle_at_88%_24%,rgba(34,211,238,0.14),transparent_22%),radial-gradient(circle_at_20%_88%,rgba(236,72,153,0.10),transparent_22%)]"
    />

    <div class="relative mx-auto max-w-7xl">
      <!-- DETAILS VIEW -->
      <div v-if="selectedProject" class="mx-auto max-w-6xl">
        <div class="mb-10 flex flex-wrap items-center gap-3 text-sm text-slate-300">
          <button
            type="button"
            @click="closeProjectDetails"
            class="inline-flex items-center gap-2 rounded-xl border border-white/10 bg-white/[0.05] px-4 py-2 text-white transition hover:bg-white/[0.08]"
          >
            <ArrowLeft class="h-4 w-4" />
            Back
          </button>

          <div class="flex items-center gap-2 text-slate-400">
            <span>Projects</span>
            <ChevronRight class="h-4 w-4" />
            <span class="text-white">{{ selectedProject.title }}</span>
          </div>
        </div>

        <div class="grid gap-8 lg:grid-cols-[minmax(0,1fr)_460px]">
          <!-- LEFT -->
          <div>
            <h1 class="text-4xl font-extrabold leading-tight text-slate-100 sm:text-5xl">
              {{ selectedProject.title }}
            </h1>

            <div class="mt-4 h-1.5 w-24 rounded-full bg-violet-500/90" />

            <p class="mt-8 max-w-2xl text-base leading-8 text-slate-300 sm:text-lg">
              {{ selectedProject.description }}
            </p>

            <div class="mt-8 grid gap-4 sm:grid-cols-2">
              <div class="rounded-2xl border border-white/10 bg-white/[0.05] p-5">
                <div class="flex items-start gap-3">
                  <div class="rounded-xl bg-cyan-400/10 p-3 text-cyan-300">
                    <Code2 class="h-5 w-5" />
                  </div>
                  <div>
                    <p class="text-2xl font-bold text-white">
                      {{ selectedProject.techStack.length }}
                    </p>
                    <p class="mt-1 text-sm text-slate-400">Total Teknologi</p>
                  </div>
                </div>
              </div>

              <div class="rounded-2xl border border-white/10 bg-white/[0.05] p-5">
                <div class="flex items-start gap-3">
                  <div class="rounded-xl bg-violet-400/10 p-3 text-violet-300">
                    <Layers3 class="h-5 w-5" />
                  </div>
                  <div>
                    <p class="text-2xl font-bold text-white">
                      {{ selectedProject.features.length }}
                    </p>
                    <p class="mt-1 text-sm text-slate-400">Fitur Utama</p>
                  </div>
                </div>
              </div>
            </div>

            <div class="mt-8 flex flex-wrap gap-3">
              <a
                :href="selectedProject.liveDemo"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Button class="bg-indigo-500 px-6 py-6 text-white hover:bg-indigo-400">
                  <ExternalLink class="mr-2 h-4 w-4" />
                  Live Demo
                </Button>
              </a>

              <a
                :href="selectedProject.github"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Button class="bg-fuchsia-600/80 px-6 py-6 text-white hover:bg-fuchsia-500">
                  <Github class="mr-2 h-4 w-4" />
                  Github
                </Button>
              </a>
            </div>

            <div class="mt-10">
              <h3 class="flex items-center gap-2 text-xl font-semibold text-white">
                <Code2 class="h-5 w-5 text-violet-300" />
                Technologies Used
              </h3>

              <div class="mt-5 flex flex-wrap gap-3">
                <Badge
                  v-for="tech in selectedProject.techStack"
                  :key="tech"
                  class="rounded-full border border-white/10 bg-indigo-500/10 px-4 py-2 text-sm font-medium text-slate-200 hover:bg-indigo-500/15"
                >
                  {{ tech }}
                </Badge>
              </div>
            </div>
          </div>

          <!-- RIGHT -->
          <div class="space-y-6">
            <div class="overflow-hidden rounded-[24px] border border-white/10 bg-white/[0.05] p-3">
              <img
                :src="selectedProject.image"
                :alt="selectedProject.title"
                class="h-[230px] w-full rounded-[18px] object-cover"
              />
            </div>

            <div class="rounded-[24px] border border-white/10 bg-[#170f2a]/90 p-6">
              <h3 class="flex items-center gap-2 text-xl font-semibold text-white">
                <Star class="h-5 w-5 text-yellow-300" />
                Key Features
              </h3>

              <ul class="mt-6 space-y-6 text-slate-300">
                <li
                  v-for="feature in selectedProject.features"
                  :key="feature"
                  class="flex gap-3 leading-7"
                >
                  <span class="mt-2 h-2.5 w-2.5 rounded-full bg-violet-400" />
                  <span>{{ feature }}</span>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <!-- MAIN PORTFOLIO VIEW -->
      <div v-else>
        <div class="mx-auto max-w-10xl">
          <h2 class="text-3xl font-extrabold leading-tight text-cyan-400/80 sm:text-4xl lg:text-5xl">
            Portfolio Showcase
          </h2>

          <p class="mt-4 mb-5 max-w-3xl text-base leading-7 text-slate-400 sm:text-lg">
            Explore my journey through projects, certifications, and technical expertise.
            Each section represents a milestone in my continuous learning path.
          </p>
        </div>

        <Tabs default-value="projects" class="w-full">
          <TabsList
            class="grid h-auto w-full grid-cols-1 gap-0 rounded-[22px] border border-white/10 bg-[#120f2d]/80 p-1.5 backdrop-blur md:grid-cols-3"
          >
            <TabsTrigger
              value="projects"
              class="flex min-h-[72px] items-center justify-center gap-2 rounded-[18px] text-sm font-semibold text-slate-300 transition data-[state=active]:bg-indigo-400/15 data-[state=active]:text-white"
            >
              <FolderKanban class="h-4 w-4" />
              <span>Projects</span>
            </TabsTrigger>

            <TabsTrigger
              value="certificates"
              class="flex min-h-[72px] items-center justify-center gap-2 rounded-[18px] text-sm font-semibold text-slate-300 transition data-[state=active]:bg-indigo-400/15 data-[state=active]:text-white"
            >
              <Award class="h-4 w-4" />
              <span>Certificates</span>
            </TabsTrigger>

            <TabsTrigger
              value="tech-stack"
              class="flex min-h-[72px] items-center justify-center gap-2 rounded-[18px] text-sm font-semibold text-slate-300 transition data-[state=active]:bg-indigo-400/15 data-[state=active]:text-white"
            >
              <Boxes class="h-4 w-4" />
              <span>Tech Stack</span>
            </TabsTrigger>
          </TabsList>

          <!-- PROJECTS -->
          <TabsContent value="projects" class="mt-6">
            <div class="grid grid-cols-1 gap-5 md:grid-cols-2 xl:grid-cols-3">
              <div
                v-for="project in displayedProjects"
                :key="project.slug"
                class="group flex h-full flex-col overflow-hidden rounded-[20px] border border-white/10 bg-white/[0.06] text-left shadow-[0_0_0_1px_rgba(255,255,255,0.02)] transition duration-200 hover:border-cyan-400/30 hover:bg-white/[0.08]"
              >
                <div class="p-3 pb-0">
                  <div class="overflow-hidden rounded-[14px] bg-black/20">
                    <img
                      :src="project.image"
                      :alt="project.title"
                      class="h-44 w-full object-cover transition duration-300 group-hover:scale-[1.02]"
                    />
                  </div>
                </div>

                <div class="flex flex-1 flex-col px-4 pb-4 pt-4">
                  <h4 class="line-clamp-1 text-[1.35rem] font-semibold text-white">
                    {{ project.title }}
                  </h4>

                  <p class="mt-3 line-clamp-2 text-sm leading-6 text-slate-300">
                    {{ project.description }}
                  </p>

                  <div class="mt-5 flex items-center justify-between gap-3">
                    <a
                      :href="project.liveDemo"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="inline-flex items-center gap-1 text-sm font-medium text-cyan-300 hover:text-cyan-200"
                    >
                      Live Demo
                      <ExternalLink class="h-4 w-4" />
                    </a>

                    <button
                      type="button"
                      @click="openProjectDetails(project)"
                      class="inline-flex items-center gap-1 rounded-lg bg-white/10 px-3 py-2 text-sm font-medium text-white transition hover:bg-white/15"
                    >
                      Details
                      <span aria-hidden="true">→</span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </TabsContent>

          <!-- CERTIFICATES -->
          <TabsContent value="certificates" class="mt-6">
            <div class="grid grid-cols-1 gap-5 md:grid-cols-2 xl:grid-cols-3">
              <div
                v-for="certificate in certificates"
                :key="certificate.title"
                class="overflow-hidden rounded-[20px] border border-white/10 bg-white/[0.06] p-3 transition duration-200 hover:border-cyan-400/30 hover:bg-white/[0.08]"
              >
                <div class="overflow-hidden rounded-[14px] bg-white">
                  <img
                    :src="certificate.image"
                    :alt="certificate.title"
                    class="h-56 w-full object-cover"
                  />
                </div>
              </div>
            </div>
          </TabsContent>

          <!-- TECH STACK -->
          <TabsContent value="tech-stack" class="mt-6">
            <div class="mx-auto max-w-5xl">
              <div class="grid grid-cols-2 gap-4 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6">
                <div
                  v-for="tech in techStack"
                  :key="tech.name"
                  class="flex min-h-[140px] flex-col items-center justify-center rounded-[18px] border border-white/10 bg-white/[0.06] px-3 py-4 text-center transition duration-200 hover:border-cyan-400/30 hover:bg-white/[0.08]"
                >
                  <div class="mb-3 flex h-14 w-14 items-center justify-center overflow-hidden rounded-xl bg-white/10 p-2">
                    <img
                      :src="tech.logo"
                      :alt="tech.name"
                      class="h-full w-full object-contain"
                    />
                  </div>

                  <span class="text-sm font-semibold text-slate-200">
                    {{ tech.name }}
                  </span>
                </div>
              </div>
            </div>
          </TabsContent>
        </Tabs>
      </div>
    </div>
  </section>
</template>