<script setup>
import { Github, Linkedin, Mail, Facebook } from 'lucide-vue-next'
</script>

<template>
  <footer
    class="relative w-full border-t border-white/10 bg-slate-950 px-6 py-8 text-white md:px-12 lg:px-20 xl:px-28"
  >
    <div
      class="absolute inset-0 bg-[radial-gradient(circle_at_20%_20%,rgba(34,211,238,0.04),transparent_24%),radial-gradient(circle_at_80%_30%,rgba(168,85,247,0.03),transparent_24%)]"
    />

    <div
      class="relative mx-auto flex max-w-7xl flex-col gap-6 md:flex-row md:items-center md:justify-between"
    >
      <div>
        <h3 class="text-xl font-bold tracking-tight text-white">
          My Portfolio<span class="text-cyan-400">.</span>
        </h3>
        <p class="mt-2 text-sm leading-6 text-slate-400">
          Built with Vue, Tailwind CSS, and shadcn-vue.
        </p>
      </div>

      <div class="flex flex-wrap items-center gap-3">
        <a
          href="#"
          aria-label="Facebook"
          class="flex h-10 w-10 items-center justify-center rounded-full border border-cyan-400/60 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
        >
          <Facebook class="h-4 w-4" />
        </a>

        <a
          href="#"
          aria-label="GitHub"
          class="flex h-10 w-10 items-center justify-center rounded-full border border-cyan-400/60 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
        >
          <Github class="h-4 w-4" />
        </a>

        <a
          href="#"
          aria-label="LinkedIn"
          class="flex h-10 w-10 items-center justify-center rounded-full border border-cyan-400/60 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
        >
          <Linkedin class="h-4 w-4" />
        </a>

        <a
          href="mailto:ashleyjunie.paglicawan@gmail.com?subject=Portfolio%20Inquiry"
          aria-label="Email Ashley"
          class="flex h-10 w-10 items-center justify-center rounded-full border border-cyan-400/60 text-cyan-400 transition-all duration-200 hover:border-cyan-300 hover:bg-cyan-400/10 hover:text-cyan-300"
        >
          <Mail class="h-4 w-4" />
        </a>
      </div>
    </div>

    <div class="relative mx-auto mt-6 max-w-7xl border-t border-white/10 pt-6">
      <p class="text-center text-sm text-slate-500">
        © 2026 Ashley. All rights reserved.
      </p>
    </div>
  </footer>
</template>