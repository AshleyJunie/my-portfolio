<script setup>
import { ref, onMounted, onBeforeUnmount, computed } from 'vue'
import {
  NavigationMenu,
  NavigationMenuItem,
  NavigationMenuLink,
  NavigationMenuList,
} from '@/components/ui/navigation-menu'
import { Button } from '@/components/ui/button'

const activeSection = ref('home')
const aboutOpen = ref(false)
const mobileOpen = ref(false)
const mobileAboutOpen = ref(false)

const mainLinks = [
  { label: 'Home', href: '#home', id: 'home' },
  { label: 'Projects', href: '#projects', id: 'projects' },
  { label: 'Contact', href: '#contact', id: 'contact' },
]

const aboutLinks = [
  { label: 'About Me', href: '#about', id: 'about' },
  { label: 'Education', href: '#education', id: 'education' },
  { label: 'Work Experience', href: '#experience', id: 'experience' },
]

const allLinks = [...mainLinks, ...aboutLinks]

const aboutIsActive = computed(() =>
  aboutLinks.some((link) => link.id === activeSection.value)
)

const navClass = (id) =>
  [
    'inline-flex h-10 items-center justify-center rounded-md px-4 py-2 text-sm font-medium transition-all duration-200',
    activeSection.value === id
      ? 'bg-white/10 text-cyan-400'
      : 'text-slate-300 hover:bg-white/5 hover:text-white',
  ].join(' ')

const dropdownTriggerClass = computed(() =>
  [
    'inline-flex h-10 items-center justify-center rounded-md px-4 py-2 text-sm font-medium transition-all duration-200',
    aboutIsActive.value || aboutOpen.value
      ? 'bg-white/10 text-cyan-400'
      : 'text-slate-300 hover:bg-white/5 hover:text-white',
  ].join(' ')
)

const mobileClass = (id) =>
  [
    'block rounded-md px-4 py-3 text-sm font-medium transition-all duration-200',
    activeSection.value === id
      ? 'bg-white/10 text-cyan-400'
      : 'text-slate-300 hover:bg-white/5 hover:text-white',
  ].join(' ')

function updateActiveSection() {
  const sections = allLinks
    .map((link) => document.getElementById(link.id))
    .filter(Boolean)

  const scrollY = window.scrollY + 140

  for (const section of sections) {
    if (
      scrollY >= section.offsetTop &&
      scrollY < section.offsetTop + section.offsetHeight
    ) {
      activeSection.value = section.id
      return
    }
  }
}

function closeMenus() {
  aboutOpen.value = false
  mobileOpen.value = false
  mobileAboutOpen.value = false
}

function toggleAboutDropdown() {
  aboutOpen.value = !aboutOpen.value
}

function handleClickOutside(event) {
  const desktopDropdown = document.getElementById('navbar-about-dropdown')
  const desktopTrigger = document.getElementById('navbar-about-trigger')
  const mobileDropdown = document.getElementById('navbar-mobile-about-dropdown')
  const mobileTrigger = document.getElementById('navbar-mobile-about-trigger')
  const target = event.target

  const clickedDesktop =
    (desktopDropdown && desktopDropdown.contains(target)) ||
    (desktopTrigger && desktopTrigger.contains(target))

  const clickedMobile =
    (mobileDropdown && mobileDropdown.contains(target)) ||
    (mobileTrigger && mobileTrigger.contains(target))

  if (!clickedDesktop) {
    aboutOpen.value = false
  }

  if (!clickedMobile) {
    mobileAboutOpen.value = false
  }
}

onMounted(() => {
  updateActiveSection()
  window.addEventListener('scroll', updateActiveSection)
  document.addEventListener('click', handleClickOutside)
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', updateActiveSection)
  document.removeEventListener('click', handleClickOutside)
})
</script>

<template>
  <header class="sticky top-0 z-50 w-full border-b border-white/10 bg-slate-950/80 backdrop-blur">
    <div class="mx-auto flex h-16 max-w-6xl items-center justify-between px-6">
      <a href="#home" class="text-lg font-bold tracking-tight text-white">
        My Portfolio<span class="text-cyan-400">.</span>
      </a>

      <!-- Desktop -->
      <NavigationMenu class="hidden md:flex">
        <NavigationMenuList class="gap-2">
          <NavigationMenuItem>
            <NavigationMenuLink as-child>
              <a href="#home" :class="navClass('home')">
                Home
              </a>
            </NavigationMenuLink>
          </NavigationMenuItem>

          <NavigationMenuItem class="relative">
            <button
              id="navbar-about-trigger"
              type="button"
              :class="dropdownTriggerClass"
              @click.stop="toggleAboutDropdown"
            >
              About
              <svg
                class="ml-2 h-4 w-4 transition-transform duration-200"
                :class="aboutOpen ? 'rotate-180' : ''"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M19 9l-7 7-7-7"
                />
              </svg>
            </button>

            <div
              v-if="aboutOpen"
              id="navbar-about-dropdown"
              class="absolute left-0 top-12 w-56 rounded-xl border border-white/10 bg-slate-900 p-2 shadow-xl"
            >
              <a
                v-for="link in aboutLinks"
                :key="link.id"
                :href="link.href"
                :class="[
                  'block rounded-md px-4 py-2 text-sm font-medium transition-all duration-200',
                  activeSection.value === link.id
                    ? 'bg-white/10 text-cyan-400'
                    : 'text-slate-300 hover:bg-white/5 hover:text-white',
                ]"
                @click="aboutOpen = false"
              >
                {{ link.label }}
              </a>
            </div>
          </NavigationMenuItem>

          <NavigationMenuItem>
            <NavigationMenuLink as-child>
              <a href="#projects" :class="navClass('projects')">
                Projects
              </a>
            </NavigationMenuLink>
          </NavigationMenuItem>

          <NavigationMenuItem>
            <NavigationMenuLink as-child>
              <a href="#contact" :class="navClass('contact')">
                Contact
              </a>
            </NavigationMenuLink>
          </NavigationMenuItem>
        </NavigationMenuList>
      </NavigationMenu>

      <div class="hidden md:block">
        <Button class="bg-cyan-400 text-slate-950 hover:bg-cyan-300">
          Hire Me
        </Button>
      </div>

      <!-- Mobile Toggle -->
      <button
        type="button"
        class="rounded-md p-2 text-slate-300 hover:bg-white/5 hover:text-white md:hidden"
        @click="mobileOpen = !mobileOpen"
      >
        <svg
          v-if="!mobileOpen"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
        </svg>

        <svg
          v-else
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div
      v-if="mobileOpen"
      class="border-t border-white/10 bg-slate-950/95 px-6 py-4 md:hidden"
    >
      <nav class="space-y-2">
        <a href="#home" :class="mobileClass('home')" @click="closeMenus">
          Home
        </a>

        <div class="rounded-lg border border-white/10">
          <button
            id="navbar-mobile-about-trigger"
            type="button"
            class="flex w-full items-center justify-between rounded-lg px-4 py-3 text-sm font-medium text-slate-300 transition-all duration-200 hover:bg-white/5 hover:text-white"
            @click.stop="mobileAboutOpen = !mobileAboutOpen"
          >
            <span :class="aboutIsActive ? 'text-cyan-400' : ''">About</span>
            <svg
              class="h-4 w-4 transition-transform duration-200"
              :class="mobileAboutOpen ? 'rotate-180' : ''"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M19 9l-7 7-7-7"
              />
            </svg>
          </button>

          <div
            v-if="mobileAboutOpen"
            id="navbar-mobile-about-dropdown"
            class="space-y-1 px-2 pb-2"
          >
            <a
              v-for="link in aboutLinks"
              :key="link.id"
              :href="link.href"
              :class="mobileClass(link.id)"
              @click="closeMenus"
            >
              {{ link.label }}
            </a>
          </div>
        </div>

        <a href="#projects" :class="mobileClass('projects')" @click="closeMenus">
          Projects
        </a>

        <a href="#contact" :class="mobileClass('contact')" @click="closeMenus">
          Contact
        </a>

        <Button class="mt-3 w-full bg-cyan-400 text-slate-950 hover:bg-cyan-300">
          Hire Me
        </Button>
      </nav>
    </div>
  </header>
</template>