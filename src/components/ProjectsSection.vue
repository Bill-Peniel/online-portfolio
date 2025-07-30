<template>
  <section id="projects" class="section-padding bg-gray-50 dark:bg-gray-900 transition-colors duration-300">
    <div class="max-w-7xl mx-auto">
      <div class="text-center mb-12">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 dark:text-white mb-4">
          Mes Projets
        </h2>
        <p class="text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Découvrez quelques-unes de mes réalisations récentes
        </p>
      </div>
      <transition name="fade-slide" appear>
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="project in projects" :key="project.id" 
               class="bg-white dark:bg-gray-900 rounded-xl overflow-hidden shadow-lg hover:shadow-xl transition-all duration-300 hover:-translate-y-2 animate-slide-up">
            <div class="aspect-video bg-gradient-to-br from-primary-400 to-primary-600 relative overflow-hidden">
              <div class="absolute inset-0 flex items-center justify-center">
                <component :is="project.icon" :size="48" class="text-white" />
              </div>
            </div>
            
            <div class="p-6">
              <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">
                {{ project.title }}
              </h3>
              <p class="text-gray-600 dark:text-gray-300 mb-4 text-sm leading-relaxed">
                {{ project.description }}
              </p>
              
              <div class="flex flex-wrap gap-2 mb-4">
                <span v-for="tech in project.technologies" :key="tech"
                      class="px-2 py-1 bg-gray-100 dark:bg-gray-700 text-gray-700 dark:text-gray-300 rounded text-xs font-medium">
                  {{ tech }}
                </span>
              </div>
              
              <div class="flex gap-3">
                <a :href="project.externalLink" 
                  class="flex items-center gap-2 text-primary-600 dark:text-primary-400 hover:text-primary-700 dark:hover:text-primary-300 transition-colors text-sm font-medium">
                  <ExternalLink :size="16" />
                  Demo
                </a>
                <a :href="project.github" 
                  class="flex items-center gap-2 text-gray-600 dark:text-gray-400 hover:text-gray-700 dark:hover:text-gray-300 transition-colors text-sm font-medium">
                  <Github :size="16" />
                  Code
                </a>

              </div>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { ExternalLink, Github, CoinsIcon, LucideCalendar, Workflow } from 'lucide-vue-next'

const projects = ref([
  {
    id: 1,
    title: 'CKD-Care',
    description: 'Une plateforme de gestion et de suivi des patients atteints de Maladie Rénale Chronique (MRC).',
    technologies: ['React', 'Express.js', 'MongoDB'],
    icon: LucideCalendar,
    externalLink: "https://ckd-care.onrender.com",
    github: "https://github.com/Bill-Peniel/myCKDserver.git"
  },
  {
    id: 2,
    title: 'C-TONTINE',
    description: 'Système de gestion efficace de la tontine.',
    technologies: ['React', 'Node.js'],
    icon: CoinsIcon,
    github: "https://github.com/Bill-Peniel/C-TONTINE.git"
  },
  {
    id: 3,
    title: 'Programmation Python et R',
    description: "Implémentation d'un sous-ensemble de Numpy en Python, tracé de graphique et analyse de données, petit programme GUI en Python avec Tkinter.",
    technologies: ['React Native', 'Firebase', 'Socket.io'],
    icon: Workflow,
    github: "https://github.com/Yoannoza/groupe_1.git"
  },
  /*{
    id: 4,
    title: 'Site Web Corporate',
    description: 'Site vitrine responsive avec CMS personnalisé et optimisations SEO.',
    technologies: ['Vue.js', 'Nuxt.js', 'Tailwind CSS', 'Strapi'],
    icon: Globe
  },
  {
    id: 5,
    title: 'App de Productivité',
    description: 'Outil de gestion de tâches avec collaboration d\'équipe et intégrations.',
    technologies: ['Vue.js', 'Express.js', 'MongoDB', 'Docker'],
    icon: Calendar
  },
  {
    id: 6,
    title: 'Plateforme SaaS',
    description: 'Solution complète avec authentification, abonnements et API REST.',
    technologies: ['React', 'Node.js', 'PostgreSQL', 'AWS'],
    icon: Smartphone
  }*/
])
</script>

<style>
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: opacity 0.7s cubic-bezier(0.4,0,0.2,1), transform 0.7s cubic-bezier(0.4,0,0.2,1);
}
.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(40px) scale(0.98);
}
.fade-slide-enter-to,
.fade-slide-leave-from {
  opacity: 1;
  transform: translateY(0) scale(1);
}
</style>
