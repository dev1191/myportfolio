<script setup>
import ProjectCard from './ProjectCard.vue'

const projects = [
  {
    title: 'Ridein - Taxi Booking System',
    tags: '[LARAVEL + ANDROID + IOS + FILAMENT + MYSQL + REDIS + DOCKER]',
    description: 'Ridein is a full-featured taxi booking and ride-hailing platform connecting riders, drivers, and fleet operators through mobile apps and a web-based management system. It includes real-time ride tracking, automated driver dispatch, fare calculation, scheduled rides, wallet and online payments, driver management, analytics, and configurable service areas. Built with Laravel, Filament, Kotlin, MySQL, and modern web technologies, Ridein offers a scalable solution for launching and managing a ride-hailing business.',
    image: '/images/01JPV6EPJ3C4304AQ71CXAP9S5.png',
    imageAlt: 'Taxi Booking Dashboard',
    link:'https://ridein.in/',
    github:''
  },
  {
    title: 'Ouraride - Taxi Booking System',
    tags: '[LARAVEL + ANDROID + FILAMENT + MYSQL + DOCKER + REDIS + OSRM]',
    description: "OuraRide is a comprehensive ride-hailing and parcel delivery platform designed to connect passengers, drivers, fleet owners, and delivery services. It features ride booking, real-time GPS tracking, dynamic fare calculation, driver management, parcel delivery, and an admin dashboard. Built with Laravel 13, Filament 5, Flutter, MySQL, OSRM, Typesense and Redis, the platform provides a scalable solution for businesses looking to launch and manage their own mobility services.",
    image: '/images/ouraride_taxi_booking.png',
    imageAlt: 'Ouraride Taxi Booking Dashboard',
    link:'https://ouraride.wowsourcemonster.in/',
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
    link: '',
    github: ''
  }
]
</script>

<template>
  <section id="projects" class="stitched-grid border-b border-outline-variant grid-cols-1 md:grid-cols-2">
    <div class="stitched-module p-margin-md col-span-full border-b border-outline-variant">
      <div class="flex justify-between items-center">
        <h2 class="text-headline-lg font-bold text-on-background">SELECTED PROJECTS</h2>
        <span class="font-label-mono text-on-surface-variant">{{ String(projects.length).padStart(2, '0') }} // DEPLOYED</span>
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
