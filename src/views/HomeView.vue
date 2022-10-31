<template>
  <div class="home">
    <section class="flex justify-center my-1">
      <section class="flex flex-col sm:justify-between items-center sm:flex-row mt-12 sm:mt-10 mb-5 sm:mb-8">
        <div class="w-full md:w-1/3 text-left">
          <h1 class="font-general-semibold text-3xl md:text-3xl xl:text-4xl text-center sm:text-left text-ternary-dark dark:text-primary-light uppercase">
            {{ $t('hi-i-am') }}
          </h1><p class="font-general-medium mt-2 text-lg sm:text-xl xl:text-2xl text-center sm:text-left leading-none text-gray-400 px-5 lg:px-0">
            {{ $t('skills') }}
          </p>
          <div class="flex justify-center sm:block">
            <a
              download="diego-perez.resume.pdf"
              href="data/diego-perez-resume.pdf"
              class="flex justify-center items-center w-36 sm:w-48 mt-12 mb-6 sm:mb-0 text-lg border border-sky-200 dark:border-ternary-dark py-2.5 sm:py-3 shadow-lg rounded-lg bg-sky-50 focus:ring-1 focus:ring-sky-900 hover:bg-sky-500 text-gray-500 hover:text-white duration-500"
              aria-label="Download Resume"
            >
              <span class="text-sm sm:text-lg font-general-medium duration-100">
                {{ $t('download-cv') }}
              </span>
            </a>
          </div>
        </div>
        <DevAnimated />
      </section>
    </section>
    <section class="flex justify-center mb-2">
      <h1 class="text-3xl md:text-3xl xl:text-4xl text-center">
        {{ $t('projects-portfolio') }}
      </h1>
    </section>
    <section class="flex justify-center mb-5">
      <Cards
        v-if="projects"
        :projects="projects"
      />
    </section>
    <section class="flex justify-center mb-5">
      <Stats />
    </section>
    <section class="flex justify-center mb-5">
      <DownloadApp />
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import axios from 'axios'
import DevAnimated from '@/components/animated/DevAnimated.vue'
import Cards from '@/components/Cards.vue'
import DownloadApp from '@/components/DownloadApp.vue'
import Stats from '@/components/Stats.vue'
import { ElNotification } from 'element-plus'
import {
  LocationUI,
  Project
} from '../types'

export default defineComponent({
  name: 'HomeView',
  components: {
    DevAnimated,
    Cards,
    DownloadApp,
    Stats,
  },
  data: () => ({
    error: null,
    projects: null as unknown as Project[]
  }),
  async beforeMount() {
    this.projects = await this.fetchProjects()
  },
  methods: {
    onError(error: any) {
      ElNotification({
        title: 'Error',
        message: error.message,
        duration: 5000,
        type: 'error'
      })
    },
    async fetchProjects() {
      try {
        const url = `data/projects.json`
        const result = await axios.get(url)
        const { data } = result
        return data as Project[]
      } catch (error: any) {
        this.error = error
        return null as unknown as Project[]
      }
    },
    onSelecCity(location: LocationUI) {
      this.$router.push({
        name: 'city',
        params: {
          city: location.city.toLocaleLowerCase().replaceAll(' ', '-'),
          state: location.state.toLocaleLowerCase().replaceAll(' ', '-'),
          country: location.country.toLocaleLowerCase().replaceAll(' ', '-'),
        },
        query: {
          lat: location.geometry?.coordinates[1],
          lng: location.geometry?.coordinates[0],
          preview: 'true'
        }
      })
    }
  }
})
</script>
