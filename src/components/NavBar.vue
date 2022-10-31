<template>
  <header class="bg-gray-100 dark:bg-gray-900 shadow-sm text-gray-700 body-font">
    <div class="container mx-auto flex flex-wrap lg:p-5 py-3 flex-col md:flex-row items-center">
      <div class="lg:visible lg:mx-0 mx-auto">
        <router-link
          to="/"
        >
          <a class="flex title-font font-medium items-center text-gray-700 dark:text-gray-100">
            <span class="lg:ml-3 text-xl">DforceUI</span>
          </a>
        </router-link>
      </div>

      <nav class="md:ml-auto md:mr-auto flex flex-wrap items-center text-base justify-center">
        <router-link
          to="/"
        >
          <a class="mr-5 cursor-pointer font-bold text-gray-700 hover:text-sky-400 dark:hover:text-sky-400 dark:text-gray-200">
            {{ $t('projects') }}
          </a>
        </router-link>
        <router-link
          to="/about"
        >
          <a class="mr-5 cursor-pointer font-bold text-gray-700 hover:text-sky-400 dark:hover:text-sky-400 dark:text-gray-200">
            {{ $t('about-me') }}
          </a>
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
  <!-- <header class="bg-primary dark:bg-gray-900 shadow-lg">
    <nav class="container mx-auto flex flex-col sm:flex-row items-center justify-between gap-4 py-6">
      <router-link
        to="/"
      >
        <div class="flex-1 invisible lg:visible">
          <a class="btn btn-ghost normal-case text-xl">DforceUI</a>
        </div>
      </router-link>
      <div class="flex gap-2">
        <div class="form-control invisible lg:visible">
          <input
            type="text"
            placeholder="Search"
            class="input input-bordered"
          >
        </div>
        <DarkModeSelector
          :size="5"
        />
        <LanguageSelector />
        <ThemeSelector v-if="false" />
        <div
          v-if="false"
          class="dropdown dropdown-end"
        >
          <label
            tabindex="0"
            class="btn btn-ghost btn-circle avatar"
          >
            <div class="w-10 rounded-full">
              <img src="https://placeimg.com/80/80/people">
            </div>
          </label>
          <ul
            tabindex="0"
            class="mt-3 p-2 shadow menu menu-compact dropdown-content bg-base-100 rounded-box w-52"
          >
            <li>
              <a class="justify-between">
                Profile
                <span class="badge">New</span>
              </a>
            </li>
            <li><a>Settings</a></li>
            <li><a>Logout</a></li>
          </ul>
        </div>
      </div>
    </nav>
  </header> -->
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
