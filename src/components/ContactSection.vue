<template>
  <section id="contact" class="section-padding bg-gray-50 dark:bg-gray-900 transition-colors duration-300">
    <div class="max-w-7xl mx-auto">
      <div class="text-center mb-12">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 dark:text-white mb-4">
          Contactez-moi
        </h2>
        <p class="text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Prêt à collaborer ? N'hésitez pas à me contacter pour discuter de votre projet
        </p>
      </div>

      <div class="grid md:grid-cols-2 gap-12">
        <!-- Informations de contact -->
        <transition name="fade-slide" appear>
          <div class="animate-none bg-white/80 dark:bg-gray-800/80 rounded-xl shadow-lg border border-gray-200 dark:border-gray-700 p-8 transition-colors">
            <h3 class="text-2xl font-bold text-gray-900 dark:text-white mb-6">
              Restons en contact
            </h3>
            <p class="text-gray-600 dark:text-gray-300 mb-8 leading-relaxed">
              Je suis toujours ouvert aux nouvelles opportunités et collaborations intéressantes. 
              Que ce soit pour un projet, une question ou simplement pour dire bonjour, n'hésitez pas !
            </p>

            <div class="space-y-4">
              <div class="flex items-center gap-4">
                <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center">
                  <Mail :size="20" class="text-primary-600 dark:text-primary-400" />
                </div>
                <div>
                  <p class="font-medium text-gray-900 dark:text-white">Email</p>
                  <a href="mailto:billakpacheme84@gmail.com" class="text-primary-600 dark:text-primary-400 hover:underline">
                    billakpacheme84@gmail.com
                  </a>
                </div>
              </div>

              <div class="flex items-center gap-4">
                <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center">
                  <Phone :size="20" class="text-primary-600 dark:text-primary-400" />
                </div>
                <div>
                  <p class="font-medium text-gray-900 dark:text-white">Téléphone</p>
                  <a href="tel:+2290157068288" class="text-primary-600 dark:text-primary-400 hover:underline">
                    +229 01 57 06 82 88
                  </a>
                </div>
              </div>

              <div class="flex items-center gap-4">
                <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center">
                  <MapPin :size="20" class="text-primary-600 dark:text-primary-400" />
                </div>
                <div>
                  <p class="font-medium text-gray-900 dark:text-white">Localisation</p>
                  <p class="text-gray-600 dark:text-gray-300">Cotonou, Bénin</p>
                </div>
              </div>
            </div>

            <!-- Réseaux sociaux -->
            <div class="mt-8">
              <h4 class="font-medium text-gray-900 dark:text-white mb-4">Suivez-moi</h4>
              <div class="flex gap-4">
                <a href="#" class="w-10 h-10 bg-gray-100 dark:bg-gray-800 rounded-lg flex items-center justify-center text-gray-600 dark:text-gray-400 hover:bg-primary-100 dark:hover:bg-primary-900 hover:text-primary-600 dark:hover:text-primary-400 transition-colors">
                  <Github :size="20" />
                </a>
                <a href="https://www.linkedin.com/in/bill-akpacheme-145b8225a" class="w-10 h-10 bg-gray-100 dark:bg-gray-800 rounded-lg flex items-center justify-center text-gray-600 dark:text-gray-400 hover:bg-primary-100 dark:hover:bg-primary-900 hover:text-primary-600 dark:hover:text-primary-400 transition-colors">
                  <Linkedin :size="20" />
                </a>
              </div>
            </div>
          </div>
        </transition>

        <!-- Formulaire de contact -->
        <transition name="fade-slide" appear>
          <div class="animate-none bg-white/80 dark:bg-gray-800/80 rounded-xl shadow-lg border border-gray-200 dark:border-gray-700 p-8 transition-colors">
            <form @submit.prevent="submitForm" class="space-y-6">
              <div>
                <label for="name" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  Nom complet
                </label>
                <input
                  type="text"
                  id="name"
                  v-model="form.name"
                  required
                  class="w-full px-4 py-3 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-gray-800 text-gray-900 dark:text-white transition-colors"
                  placeholder="Votre nom"
                >
              </div>

              <div>
                <label for="email" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  Email
                </label>
                <input
                  type="email"
                  id="email"
                  v-model="form.email"
                  required
                  class="w-full px-4 py-3 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-gray-800 text-gray-900 dark:text-white transition-colors"
                  placeholder="votre@email.com"
                >
              </div>

              <div>
                <label for="subject" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  Sujet
                </label>
                <input
                  type="text"
                  id="subject"
                  v-model="form.subject"
                  required
                  class="w-full px-4 py-3 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-gray-800 text-gray-900 dark:text-white transition-colors"
                  placeholder="Sujet de votre message"
                >
              </div>

              <div>
                <label for="message" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  Message
                </label>
                <textarea
                  id="message"
                  v-model="form.message"
                  required
                  rows="5"
                  class="w-full px-4 py-3 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-gray-800 text-gray-900 dark:text-white transition-colors resize-none"
                  placeholder="Votre message..."
                ></textarea>
              </div>

              <button
                type="submit"
                :disabled="isSubmitting"
                class="w-full btn-primary disabled:opacity-50 disabled:cursor-not-allowed flex items-center justify-center gap-2"
              >
                <Send :size="20" />
                <span v-if="!isSubmitting">Envoyer le message</span>
                <span v-else>Envoi en cours...</span>
              </button>
            </form>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { Mail, Phone, MapPin, Github, Linkedin, Send } from 'lucide-vue-next'

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)

const submitForm = async () => {
  isSubmitting.value = true;

  try {
    // Créer un FormData pour FormSubmit
    const formData = new FormData();
    formData.append('name', form.value.name);
    formData.append('email', form.value.email);
    formData.append('subject', form.value.subject);
    formData.append('message', form.value.message);
    
    // Ajouter des champs pour FormSubmit
    formData.append('_subject', `Nouveau message de ${form.value.name}`);
    formData.append('_captcha', 'false'); // Désactiver le captcha pour les tests
    formData.append('_template', 'table'); // Utiliser un template de tableau

    const response = await fetch("https://formsubmit.co/billakpacheme84@gmail.com", {
      method: "POST",
      body: formData
    });

    if (response.ok) {
      alert("Message envoyé avec succès !");
      // Réinitialiser le formulaire
      form.value = {
        name: '',
        email: '',
        subject: '',
        message: ''
      };
    } else {
      console.error('Erreur de réponse:', response.status, response.statusText);
      alert("Une erreur est survenue lors de l'envoi. Vérifiez la console pour plus de détails.");
    }
  } catch (error) {
    console.error('Erreur de réseau:', error);
    alert("Erreur de réseau. Veuillez réessayer.");
  }

  isSubmitting.value = false;
};

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