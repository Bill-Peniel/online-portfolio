<template>
  <div id="app" :class="{ 'dark': isDark }" class="min-h-screen bg-white dark:bg-gray-900 transition-colors duration-300">
    <!-- Navigation -->
    <nav class="fixed top-0 w-full bg-white/80 dark:bg-gray-900/80 backdrop-blur-sm z-50 border-b border-gray-200 dark:border-gray-700">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <div class="font-bold text-xl text-gray-900 dark:text-white">
            Portfolio
          </div>
          
          <div class="hidden md:flex space-x-8">
            <a href="#home" class="nav-link">Accueil</a>
            <a href="#about" class="nav-link">À propos</a>
            <a href="#skills" class="nav-link">Compétences</a>
            <a href="#projects" class="nav-link">Projets</a>
            <a href="#contact" class="nav-link">Contact</a>
          </div>
          
          <div class="flex items-center space-x-4">
            <button @click="toggleDarkMode" class="p-2 rounded-lg bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors">
              <Sun v-if="isDark" :size="20" />
              <Moon v-else :size="20" />
            </button>
            
            <button @click="toggleMobileMenu" class="md:hidden p-2 rounded-lg bg-gray-100 dark:bg-gray-800">
              <Menu :size="20" />
            </button>
          </div>
        </div>
        
        <!-- Mobile menu -->
        <div v-if="isMobileMenuOpen" class="md:hidden py-4 border-t border-gray-200 dark:border-gray-700">
          <div class="flex flex-col space-y-2">
            <a href="#home" class="mobile-nav-link" @click="closeMobileMenu">Accueil</a>
            <a href="#about" class="mobile-nav-link" @click="closeMobileMenu">À propos</a>
            <a href="#skills" class="mobile-nav-link" @click="closeMobileMenu">Compétences</a>
            <a href="#projects" class="mobile-nav-link" @click="closeMobileMenu">Projets</a>
            <a href="#contact" class="mobile-nav-link" @click="closeMobileMenu">Contact</a>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="pt-16 min-h-screen flex items-center section-padding bg-white dark:bg-gray-900 transition-colors duration-300">
      <div class="max-w-3xl mx-auto w-full bg-white/80 dark:bg-gray-800/80 rounded-xl shadow-lg border border-gray-200 dark:border-gray-700 p-8 transition-colors">
        <div class="text-center">
          <div class="animate-fade-in">
            <h1 class="text-4xl md:text-6xl font-bold text-gray-900 dark:text-white mb-6">
              Bonjour, je suis
              <span class="text-primary-600 dark:text-primary-400">{{ name }}</span>
            </h1>
            <p class="text-xl md:text-2xl text-gray-600 dark:text-gray-300 mb-8 max-w-3xl mx-auto">
              {{ title }}
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center items-center animate-slide-up">
              <a href="#projects" class="btn-primary">
                Voir mes projets
              </a>
              <a href="#contact" class="btn-secondary">
                Me contacter
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <AboutSection />

    <!-- Skills Section -->
    <SkillsSection />

    <!-- Projects Section -->
    <ProjectsSection />

    <!-- Contact Section -->
    <ContactSection />

    <!-- Footer -->
    <footer class="bg-gray-50 dark:bg-gray-800 section-padding">
      <div class="max-w-7xl mx-auto text-center">
        <p class="text-gray-600 dark:text-gray-400">
          © 2023 {{ name }}. Tous droits réservés.
        </p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Sun, Moon, Menu } from 'lucide-vue-next'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'

const isDark = ref(false)
const isMobileMenuOpen = ref(false)

// Données du portfolio - à personnaliser
const name = ref('Bill Akpacheme')
const title = ref('Développeur Full-Stack passionné par la création d\'expériences numériques exceptionnelles')

const toggleDarkMode = () => {
  isDark.value = !isDark.value
  localStorage.setItem('darkMode', isDark.value)
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

onMounted(() => {
  // Récupérer le mode sombre depuis localStorage
  const savedDarkMode = localStorage.getItem('darkMode')
  if (savedDarkMode !== null) {
    isDark.value = savedDarkMode === 'true'
  } else {
    // Détecter la préférence système
    isDark.value = window.matchMedia('(prefers-color-scheme: dark)').matches
  }
})
</script>

<style scoped>
.nav-link {
  @apply text-gray-600 dark:text-gray-300 hover:text-primary-600 dark:hover:text-primary-400 transition-colors duration-200 font-medium;
}

.mobile-nav-link {
  @apply block px-3 py-2 text-gray-600 dark:text-gray-300 hover:text-primary-600 dark:hover:text-primary-400 hover:bg-gray-50 dark:hover:bg-gray-800 rounded-md transition-colors duration-200;
}
</style>
