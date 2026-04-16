<script setup>
import { ref } from 'vue'
import { Button } from '@/components/ui/button'
import { Input } from '@/components/ui/input'
import { Textarea } from '@/components/ui/textarea'
import { Mail, Phone, MapPin } from 'lucide-vue-next'

const recipientEmail = 'ashleyjunie.paglicawan@gmail.com'

const name = ref('')
const email = ref('')
const subject = ref('')
const message = ref('')

function sendEmail() {
  const finalSubject = encodeURIComponent(
    subject.value || `Portfolio Inquiry from ${name.value || 'Visitor'}`
  )

  const body = encodeURIComponent(
    `Name: ${name.value}\nEmail: ${email.value}\n\nMessage:\n${message.value}`
  )

  window.location.href = `mailto:${recipientEmail}?subject=${finalSubject}&body=${body}`
}
</script>

<template>
  <section
    id="contact"
    class="relative w-full bg-slate-950 px-6 py-20 text-white md:px-12 lg:px-20 xl:px-28"
  >
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_18%_20%,rgba(34,211,238,0.05),transparent_24%),radial-gradient(circle_at_80%_30%,rgba(168,85,247,0.04),transparent_24%)]" />

    <div class="relative mx-auto max-w-6xl">
      <div class="mb-12 text-center">
        <p class="mb-3 text-sm font-semibold uppercase tracking-[0.18em] text-cyan-400/80">
          Contact
        </p>

        <h2 class="text-3xl font-extrabold leading-tight sm:text-4xl lg:text-5xl">
          Get In <span class="text-cyan-400">Touch</span>
        </h2>

        <p class="mx-auto mt-4 max-w-3xl text-base leading-7 text-slate-400 sm:text-lg">
          Feel free to reach out for opportunities, collaborations, or project inquiries.
        </p>
      </div>

      <div class="overflow-hidden rounded-3xl border border-white/10 bg-white/5">
        <div class="grid lg:grid-cols-[0.9fr_1.1fr]">
          <!-- Left Info -->
          <div class="border-b border-white/10 bg-white/[0.03] p-6 md:p-8 lg:border-b-0 lg:border-r">
            <h3 class="text-2xl font-bold text-white">Contact Information</h3>
            <p class="mt-4 text-base leading-8 text-slate-400">
              I’m open to internships, entry-level roles, freelance opportunities,
              and collaborations in web development and IT-related work.
            </p>

            <div class="mt-8 space-y-5">
              <div class="flex items-start gap-4">
                <div class="rounded-xl border border-white/10 bg-white/5 p-3">
                  <Mail class="h-5 w-5 text-cyan-400" />
                </div>
                <div>
                  <p class="text-sm font-medium text-slate-300">Email</p>
                  <p class="mt-1 text-slate-400">ashleyjunie.paglicawan@gmail.com</p>
                </div>
              </div>

              <div class="flex items-start gap-4">
                <div class="rounded-xl border border-white/10 bg-white/5 p-3">
                  <Phone class="h-5 w-5 text-cyan-400" />
                </div>
                <div>
                  <p class="text-sm font-medium text-slate-300">Phone</p>
                  <p class="mt-1 text-slate-400">+63 967 607 5814</p>
                </div>
              </div>

              <div class="flex items-start gap-4">
                <div class="rounded-xl border border-white/10 bg-white/5 p-3">
                  <MapPin class="h-5 w-5 text-cyan-400" />
                </div>
                <div>
                  <p class="text-sm font-medium text-slate-300">Location</p>
                  <p class="mt-1 text-slate-400">Cavite City, Cavite, Philippines</p>
                </div>
              </div>    
            </div>
          </div>

          <!-- Right Form -->
          <div class="p-6 md:p-8">
            <h3 class="text-2xl font-bold text-white">Send a Message</h3>
            <p class="mt-3 text-slate-400">
              Fill out the form below and your default email app will open with your message pre-filled.
            </p>

            <form
              class="mt-8 space-y-5"
              @submit.prevent="sendEmail"
            >
              <div class="grid gap-5 md:grid-cols-2">
                <div class="space-y-2">
                  <label class="text-sm font-medium text-slate-300">Name</label>
                  <Input
                    v-model="name"
                    type="text"
                    placeholder="Your name"
                    class="border-white/10 bg-white/5 text-white placeholder:text-slate-500"
                  />
                </div>

                <div class="space-y-2">
                  <label class="text-sm font-medium text-slate-300">Email</label>
                  <Input
                    v-model="email"
                    type="email"
                    placeholder="Your email"
                    class="border-white/10 bg-white/5 text-white placeholder:text-slate-500"
                  />
                </div>
              </div>

              <div class="space-y-2">
                <label class="text-sm font-medium text-slate-300">Subject</label>
                <Input
                  v-model="subject"
                  type="text"
                  placeholder="Message subject"
                  class="border-white/10 bg-white/5 text-white placeholder:text-slate-500"
                />
              </div>

              <div class="space-y-2">
                <label class="text-sm font-medium text-slate-300">Message</label>
                <Textarea
                  v-model="message"
                  placeholder="Write your message here..."
                  class="min-h-[160px] border-white/10 bg-white/5 text-white placeholder:text-slate-500"
                />
              </div>

              <div class="pt-2">
                <Button
                  type="submit"
                  class="bg-cyan-400 px-6 py-6 text-base font-medium text-slate-950 hover:bg-cyan-300"
                >
                  Send Message
                </Button>
              </div>
            </form>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
