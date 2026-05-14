<script setup>
import ProjectCard from './ProjectCard.vue'

const projects = [
  {
    title: 'Ridein - Taxi Booking System',
    tags: '[LARAVEL + ANDROID + IOS + FILAMENTPHP + MYSQL + REDIS + DOCKER]',
    description: 'Transform your traditional fleet business into a digital powerhouse with our innovative taxi booking application. Includes a comprehensive admin dashboard and white-label solution.',
    image: '/images/01JPV6EPJ3C4304AQ71CXAP9S5.png',
    imageAlt: 'Taxi Booking Dashboard',
    link:'https://ridein.in/',
    github:''
  },
  {
    title: 'Shuttle Bus Portal',
    tags: '[LARAVEL + ANDROID + VUEJS + REDIS + MONGODB + DOCKER]',
    description: 'Power your shuttle services with an on-demand mobile app that keeps seats full and modernizes daily commutes with easy, convenient bookings and AI-driven fleet management.',
    image: '/images/01JPVTMMPMS7XAWC08JEST0Q39.png',
    imageAlt: 'Shuttle Bus App',
    link:'https://shuttle.ridein.in/',
        github:''
  },
  {
    title: 'Affilspark — Affiliate Marketing',
    tags: '[LARAVEL + MYSQL + JQUERY + BOOTSTRAP]',
    description: 'A client wanted to build something like ClickBank but focused on the French market. Vendors sign up, list their products, and set their own commission rates. Affiliates browse the marketplace, grab their unique tracking link, and start promoting. Every click, conversion, and commission is tracked in real time. Payouts are automated through Stripe and PayPal so nobody has to chase anyone for money — affiliates just get paid when they earn. ',
    image: '/images/01JPV8W7XGJWG5WEJH07VJEDEW.png',
    imageAlt: 'Affilspark',
    link:'https://affilspark.com/',
        github:''
  },
    {
    title: 'Wow Ride - Taxi Booking System',
    tags: '[LARAVEL + ANDROID + VUE + MONGODB + DOCKER + REDIS]',
    description: "Features different types of services like Daily, Rental, and Outstation, along with franchise modules. Built using a robust microservices architecture for high scalability.",
    image: '/images/01JPV6EPJ3C4304AQ71CXAP9E3.png',
    imageAlt: 'Wow Taxi Booking Dashboard',
    link:'https://admin.wowride.in/',
    github:''
  },
  {
    title:'Travel Membership portal (CRM)',
    tags: '[CODEIGNITER + PHP + JQUERY + BOOTSTRAP + MYSQL]',
    description: 'Designed and developed a custom CRM system for a client, resulting in a 30% increase in lead conversion rates. It\'s a multi-login portal for the employee and its subscribed members. Members can book multi-destination vacations as per the subscription plans, and renew the subscriptions per the destination pricing. ',
    image: '/images/01JPV6TV7WMPQ1H7ENNHZB0232.png',
    imageAlt: 'royalsclubinternational',
    link:'https://royalsclubinternational.com/',
        github:''
  },
  {
    title: 'School ERP System',
    tags: '[CODEIGNITER + PHP + MYSQL + JQUERY + BOOTSTRAP]',
    description: 'Revolutionizes education management by seamlessly integrating administrative tasks, student information, and academic processes, enhancing efficiency and communication.',
    image: '/images/01JPVTMMPMS7XAWC08JEST0Q39.png',
    imageAlt: 'School ERP Interface',
    link:'#',
    github:''
  }
]
</script>

<template>
  <section id="projects" class="stitched-grid border-b border-outline-variant grid-cols-1 md:grid-cols-2">
    <div class="stitched-module p-margin-md col-span-full border-b border-outline-variant">
      <div class="flex justify-between items-center">
        <h2 class="text-headline-lg font-bold text-on-background">SELECTED PROJECTS</h2>
        <span class="font-label-mono text-on-surface-variant">05 // DEPLOYED</span>
      </div>
    </div>
    
    <ProjectCard 
      v-for="(project, index) in projects" 
      :key="project.title"
      v-bind="project"
      :class="{ 'md:border-l border-outline-variant': index === 1 }"
    />
  </section>
</template>
