<script setup>
import { ref, computed } from 'vue'
import { Link, Terminal, ArrowRight } from 'lucide-vue-next'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const errors = ref({
  name: '',
  email: '',
  message: ''
})

const status = ref('idle') // 'idle' | 'submitting' | 'success' | 'error'
const statusMessage = ref('')

const contactEndpoint = import.meta.env.VITE_CONTACT_ENDPOINT || ''
const contactEmail = import.meta.env.VITE_CONTACT_EMAIL || ''

const isSubmitting = computed(() => status.value === 'submitting')

function validateField(field) {
  const value = form.value[field].trim()
  if (field === 'name') {
    if (!value) {
      errors.value.name = 'Name is required.'
      return false
    }
    if (value.length > 100) {
      errors.value.name = 'Name must be 100 characters or fewer.'
      return false
    }
    errors.value.name = ''
    return true
  }

  if (field === 'email') {
    if (!value) {
      errors.value.email = 'Email is required.'
      return false
    }
    if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value)) {
      errors.value.email = 'Enter a valid email address.'
      return false
    }
    errors.value.email = ''
    return true
  }

  if (field === 'message') {
    if (!value) {
      errors.value.message = 'Message is required.'
      return false
    }
    if (value.length < 10) {
      errors.value.message = 'Please include at least 10 characters.'
      return false
    }
    errors.value.message = ''
    return true
  }

  return true
}

function validateAll() {
  const validName = validateField('name')
  const validEmail = validateField('email')
  const validMessage = validateField('message')
  return validName && validEmail && validMessage
}

async function handleSubmit() {
  if (isSubmitting.value) return

  status.value = 'idle'
  statusMessage.value = ''

  if (!validateAll()) {
    status.value = 'error'
    statusMessage.value = 'Please fix the highlighted fields before sending.'
    return
  }

  if (contactEndpoint) {
    status.value = 'submitting'
    try {
      const payload = new FormData()
      payload.append('name', form.value.name.trim())
      payload.append('email', form.value.email.trim())
      payload.append('message', form.value.message.trim())

      const response = await fetch(contactEndpoint, {
        method: 'POST',
        headers: {
          Accept: 'application/json'
        },
        body: payload
      })

      if (!response.ok) {
        const data = await response.json().catch(() => null)
        const serverError = data?.errors?.map((e) => e.message).join(', ') || data?.error
        throw new Error(serverError || `Request failed (${response.status})`)
      }

      status.value = 'success'
      statusMessage.value = 'Message sent. Thank you for reaching out — I will respond shortly.'
      form.value = { name: '', email: '', message: '' }
      errors.value = { name: '', email: '', message: '' }
    } catch (err) {
      status.value = 'error'
      statusMessage.value =
        err?.message && !err.message.startsWith('Failed to fetch')
          ? `Unable to send: ${err.message}`
          : 'Unable to send right now. Please try again or reach out directly via LinkedIn.'
    }
    return
  }

  if (contactEmail) {
    const subject = encodeURIComponent(`Portfolio Inquiry from ${form.value.name.trim()}`)
    const body = encodeURIComponent(
      `Name: ${form.value.name.trim()}\nEmail: ${form.value.email.trim()}\n\n${form.value.message.trim()}`
    )
    window.location.href = `mailto:${contactEmail}?subject=${subject}&body=${body}`
    status.value = 'success'
    statusMessage.value = 'Opening your email client with the drafted message.'
    return
  }

  status.value = 'error'
  statusMessage.value =
    'Direct form delivery is not configured on this static build yet. Please connect via LinkedIn or GitHub on the left.'
}
</script>

<template>
  <section id="contact" class="stitched-grid grid-cols-1 md:grid-cols-2">
    <!-- Links Column -->
    <div class="stitched-module p-margin-md md:border-r border-outline-variant">
      <div class="mb-12">
        <h2 class="text-headline-lg font-bold text-on-background mb-base tracking-tight">CONNECT</h2>
        <p class="text-body-md text-on-surface-variant leading-relaxed">
          Ready to architect your next high-performance system? Let's discuss technical specifications.
        </p>
      </div>
      <div class="space-y-margin-sm">
        <a href="https://www.linkedin.com/in/dev-raj-thapa-571645b5" target="_blank" rel="noopener noreferrer" class="flex items-center justify-between group p-base border border-outline-variant hover:border-primary transition-all">
          <div class="flex items-center gap-margin-sm">
            <Link class="text-primary" :size="18" />
            <span class="font-label-mono text-xs">LINKEDIN</span>
          </div>
          <ArrowRight class="text-on-surface-variant group-hover:text-primary transition-colors" :size="18" />
        </a>
        <a href="https://github.com/dev1191/" target="_blank" rel="noopener noreferrer" class="flex items-center justify-between group p-base border border-outline-variant hover:border-primary transition-all">
          <div class="flex items-center gap-margin-sm">
            <Terminal class="text-primary" :size="18" />
            <span class="font-label-mono text-xs">GITHUB</span>
          </div>
          <ArrowRight class="text-on-surface-variant group-hover:text-primary transition-colors" :size="18" />
        </a>
      </div>
    </div>

    <!-- Form Column -->
    <div class="stitched-module p-margin-md">
      <form @submit.prevent="handleSubmit" novalidate class="space-y-6">
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-base">
          <div class="space-y-2">
            <label for="contact-name" class="font-label-mono text-on-surface-variant text-[10px] block">NAME</label>
            <input 
              id="contact-name"
              v-model="form.name"
              type="text" 
              name="name"
              maxlength="100"
              required
              autocomplete="name"
              placeholder="Jane Doe"
              :aria-invalid="Boolean(errors.name)"
              :aria-describedby="errors.name ? 'contact-name-error' : undefined"
              @blur="validateField('name')"
              @input="errors.name && validateField('name')"
              class="w-full bg-surface-container border border-outline-variant text-on-surface p-base focus:border-primary focus:outline-none focus-visible:outline-2 focus-visible:outline-primary focus-visible:outline-offset-2 placeholder:text-on-surface-variant/60 font-jetbrains text-base sm:text-sm"
            />
            <p v-if="errors.name" id="contact-name-error" class="font-label-mono text-[10px] text-on-surface">
              [!] {{ errors.name }}
            </p>
          </div>
          <div class="space-y-2">
            <label for="contact-email" class="font-label-mono text-on-surface-variant text-[10px] block">EMAIL</label>
            <input 
              id="contact-email"
              v-model="form.email"
              type="email" 
              name="email"
              maxlength="150"
              required
              autocomplete="email"
              placeholder="jane@company.com"
              :aria-invalid="Boolean(errors.email)"
              :aria-describedby="errors.email ? 'contact-email-error' : undefined"
              @blur="validateField('email')"
              @input="errors.email && validateField('email')"
              class="w-full bg-surface-container border border-outline-variant text-on-surface p-base focus:border-primary focus:outline-none focus-visible:outline-2 focus-visible:outline-primary focus-visible:outline-offset-2 placeholder:text-on-surface-variant/60 font-jetbrains text-base sm:text-sm"
            />
            <p v-if="errors.email" id="contact-email-error" class="font-label-mono text-[10px] text-on-surface">
              [!] {{ errors.email }}
            </p>
          </div>
        </div>
        <div class="space-y-2">
          <label for="contact-message" class="font-label-mono text-on-surface-variant text-[10px] block">MESSAGE</label>
          <textarea 
            id="contact-message"
            v-model="form.message"
            name="message"
            rows="4" 
            maxlength="2000"
            required
            placeholder="Tell me about the role, project scope, or timeline..."
            :aria-invalid="Boolean(errors.message)"
            :aria-describedby="errors.message ? 'contact-message-error' : undefined"
            @blur="validateField('message')"
            @input="errors.message && validateField('message')"
            class="w-full bg-surface-container border border-outline-variant text-on-surface p-base focus:border-primary focus:ring-0 outline-none placeholder:text-on-surface-variant/60 font-jetbrains text-base sm:text-sm resize-none"
          ></textarea>
          <p v-if="errors.message" id="contact-message-error" class="font-label-mono text-[10px] text-on-surface">
            [!] {{ errors.message }}
          </p>
        </div>

        <div
          v-if="statusMessage"
          role="status"
          aria-live="polite"
          :class="[
            'p-base border font-label-mono text-xs leading-relaxed',
            status === 'success'
              ? 'border-primary text-primary bg-surface-container'
              : 'border-on-surface text-on-surface bg-surface-container'
          ]"
        >
          {{ status === 'success' ? '[ OK ] ' : '[ ! ] ' }}{{ statusMessage }}
        </div>

        <button
          type="submit"
          :disabled="isSubmitting"
          class="w-full bg-primary text-on-primary font-label-mono py-margin-sm font-bold uppercase hover:opacity-90 disabled:opacity-50 disabled:cursor-not-allowed transition-all text-xs cursor-pointer"
        >
          {{ isSubmitting ? 'SENDING...' : 'SEND MESSAGE' }}
        </button>
      </form>
    </div>
  </section>
</template>
