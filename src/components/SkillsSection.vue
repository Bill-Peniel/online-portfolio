<template>
  <section id="skills" class="section-padding bg-gray-50 dark:bg-gray-900 transition-colors duration-300">
    <div class="max-w-7xl mx-auto">
      <div class="text-center mb-12">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 dark:text-white mb-4">
          Mes Compétences
        </h2>
        <p class="text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Technologies et outils que j'utilise pour créer des expériences exceptionnelles
        </p>
      </div>
      <transition name="fade-slide" appear>
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="category in skillCategories" :key="category.title" 
               class="bg-white/80 dark:bg-gray-800/80 rounded-xl p-6 shadow-lg border border-gray-200 dark:border-gray-700 hover:shadow-xl transition-shadow duration-300 animate-slide-up">
            <div class="text-center mb-6">
              <div class="w-16 h-16 bg-primary-100 dark:bg-primary-900 rounded-full flex items-center justify-center mx-auto mb-4">
                <component :is="category.icon" :size="32" class="text-primary-600 dark:text-primary-400" />
              </div>
              <h3 class="text-xl font-bold text-gray-900 dark:text-white">
                {{ category.title }}
              </h3>
            </div>
            <div class="space-y-4">
              <div v-for="skill in category.skills" :key="skill.name" class="space-y-2">
                <div class="flex justify-between items-center">
                  <span class="text-gray-700 dark:text-gray-300 font-medium">{{ skill.name }}</span>
                  <span class="text-primary-600 dark:text-primary-400 text-sm font-medium">{{ skill.level }}%</span>
                </div>
                <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                  <div class="bg-gradient-to-r from-primary-500 to-primary-600 dark:from-primary-400 dark:to-primary-600 h-2 rounded-full transition-all duration-1000"
                       :style="{ width: skill.level + '%' }"></div>
                </div>
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
import { Code, Palette, Server } from 'lucide-vue-next'

const skillCategories = ref([
  {
    title: 'Frontend',
    icon: Code,
    skills: [
      { name: 'Vue.js', level: 80 },
      { name: 'React', level: 50 },
      { name: 'JavaScript', level: 80 },
      { name: 'TypeScript', level: 70 },
      { name: 'Tailwind CSS', level: 85 }
    ]
  },
  {
    title: 'Design',
    icon: Palette,
    skills: [
      { name: 'Figma', level: 70 },
      { name: 'Responsive Design', level: 80 },
    ]
  },
  {
    title: 'Backend',
    icon: Server,
    skills: [
      { name: 'Node.js', level: 45 },
      { name: 'PostgreSQL', level: 65 },
      { name: 'MongoDB', level: 30 }
    ]
  }
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
