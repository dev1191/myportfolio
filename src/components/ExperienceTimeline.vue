<script setup>
const experiences = [
  {
    role: 'SENIOR BACKEND DEVELOPER',
    company: 'Source Monster',
    period: '2022 — 2025',
    status: 'LATEST',
    points: [
      'Designed secure web applications with Vue.js for admin panels and RESTful APIs for mobile apps.',
      'Optimized architecture within a microservices ecosystem for robust performance and scalability.',
      'Integrated third-party APIs (Twilio, SMS, Payment Gateways) into comprehensive taxi booking systems.'
    ]
  },
  {
    role: 'SENIOR NODEJS DEVELOPER',
    company: 'Rigo Tech (India) Pvt Ltd',
    period: '2020 — 2022',
    status: 'DEPLOYED',
    points: [
      'Architected backend systems leveraging microservices for scalability and high availability.',
      'Collaborated on cross-functional API integrations to ensure a seamless user experience.',
      'Created reusable code libraries, reducing development time by 40% and boosting productivity.'
    ]
  },
  {
    role: 'SENIOR PHP DEVELOPER',
    company: 'Milkyway Multidimensional',
    period: '2019 — 2020',
    status: 'DEPLOYED',
    points: [
      'Developed responsive designs, resulting in a 20% increase in mobile traffic.',
      'Designed and developed a custom CRM system, improving lead conversion rates by 30%.'
    ]
  },
  {
    role: 'PHP MOODLE DEVELOPER',
    company: 'LDS Engineers Pvt Ltd',
    period: '2017 — 2019',
    status: 'ARCHIVED',
    points: [
      'Developed Node.js REST APIs for Microsoft 365, managing data for 10,000+ users.',
      'Integrated Swagger OpenAPI 3.0 with Moodle/Iomad platforms using RESTful JSON.'
    ]
  },
  {
    role: 'MCA (MASTERS)',
    company: 'Indira Gandhi National Open University',
    period: '2014 — 2017',
    status: 'CERTIFIED',
    points: [
      'Master of Computer Applications - Specialized in Software Engineering and Database Management.'
    ]
  }
]
</script>

<template>
  <section class="stitched-grid border-b border-outline-variant">
    <div class="stitched-module p-margin-md flex justify-between items-center border-b border-outline-variant">
      <h2 class="text-headline-lg font-bold text-on-background">EXPERIENCE</h2>
      <span class="font-label-mono text-on-surface-variant">03 // TIMELINE</span>
    </div>

    <div 
      v-for="exp in experiences" 
      :key="exp.role"
      class="stitched-module p-margin-md border-b last:border-b-0 border-outline-variant"
    >
      <div class="flex flex-col md:flex-row md:justify-between mb-base">
        <div>
          <h4 class="text-2xl font-bold text-primary leading-none tracking-tight">{{ exp.role }}</h4>
          <p class="font-label-mono text-on-surface mt-2 text-[10px]">{{ exp.company }} // {{ exp.period }}</p>
        </div>
        <span class="font-label-mono text-on-surface-variant mt-2 md:mt-0 text-[10px]">[ {{ exp.status }} ]</span>
      </div>
      <ul class="space-y-base mt-4">
        <li v-for="point in exp.points" :key="point" class="flex items-start gap-3 text-sm text-on-surface-variant leading-relaxed">
          <span class="text-primary font-bold">/</span> {{ point }}
        </li>
      </ul>
    </div>
  </section>
</template>
