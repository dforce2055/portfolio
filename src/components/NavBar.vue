<template>
  <header class="bg-gray-100 dark:bg-gray-900 shadow-sm text-gray-700 body-font">
    <div class="container mx-auto flex flex-wrap lg:p-5 py-3 flex-col md:flex-row items-center">
      <div class="lg:visible lg:mx-0 mx-auto">
        <router-link
          to="/"
        >
          <a class="flex title-font font-medium items-center text-gray-700 dark:text-gray-100">
            <span class="lg:ml-3 text-xl text-primary">Dforce</span>
            <span class="text-2xl font-bold pt-1">UI</span>
          </a>
        </router-link>
      </div>

      <nav class="md:ml-auto md:mr-auto flex flex-wrap items-center text-base justify-center">
        <router-link
          to="/"
          class="mr-5 cursor-pointer font-bold text-gray-700 hover:text-sky-400 dark:hover:text-sky-400 dark:text-gray-200"
          exact-active-class="text-primary"
        >
          {{ $t('projects') }}
        </router-link>
        <router-link
          to="/about"
          class="mr-5 cursor-pointer font-bold text-gray-700 hover:text-sky-400 dark:hover:text-sky-400 dark:text-gray-200"
          exact-active-class="text-primary"
        >
          {{ $t('about-me') }}
        </router-link>
      </nav>
      <div class="inline-flex items-center py-1 px-3 rounded text-base lg:mt-4 md:mt-0 gap-3">
        <DarkModeSelector
          :size="5"
        />
        <LanguageSelector />
      </div>
    </div>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import DarkModeSelector from './DarkModeSelector.vue'
import LanguageSelector from './LanguageSelector.vue'

export default defineComponent({
  name: 'NavBar',
  components: {
    DarkModeSelector,
    LanguageSelector
  },
  data: () => ({
    darkMode: false
  }),
  async mounted() {
    const theme = document?.querySelector('html')?.getAttribute('data-theme') || 'light'
    theme === 'light' ? this.darkMode = false : this.darkMode = true
  },
  computed: {
    isDarkMode() {
      return this.darkMode
    }
  }
})
</script>
<style lang="scss">
.router-link-active {
  color: theme('colors.sky.300') !important;
}
</style>
