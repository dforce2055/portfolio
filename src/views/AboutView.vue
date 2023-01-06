<template>
  <div class="about ">
    <section class="flex justify-center my-5">
      <article class="prose lg:prose-xl">
        <div class="flex">
          <div
            class="flex-initial w-64 ..."
          >
            <div
              class="tooltip tooltip-right"
              data-tip="Diego Pérez dev"
            >
              <img
                class="mask mask-parallelogram"
                src="/images/profile.png"
              >
            </div>
          </div>
          <div class="flex-initial w-full ...">
            <h2 class="lg:pt-10">
              {{ $t('about-meself') }}
            </h2>
            <h3 class="lg:pt-5">
              {{ $t('who-i-am') }}
            </h3>
          </div>
        </div>
        <p>
          {{ $t('bio') }}
        </p>
      </article>
    </section>
    <section class="flex justify-center my-5 gap-3">
      <div
        v-for="(socialMedia, index) in socialsMedia"
        :key="index"
      >
        <a
          :href="socialMedia.url"
          target="_blank"
          class="hover:text-primary"
        >
          <mdicon
            :name="socialMedia.icon"
            :size="mediaSize"
          />
        </a>
      </div>
    </section>
    <section class="container px-5 py-24 mx-auto">
      <h2 class="text-3xl font-medium text-gray-700 dark:text-gray-300 tracking-widest mb-5">
        Technologies Stack
      </h2>
      <div class="flex flex-wrap m-4">
        <div
          v-for="(skill, index) in skills"
          :key="index"
          class="p-4 lg:w-1/6 sm:w-1/2 w-full"
        >
          <h2 class="font-medium title-font tracking-widest text-gray-700 dark:text-gray-300 mb-4 text-sm text-center sm:text-left">
            {{ skill.area }}
          </h2>
          <nav class="flex flex-col sm:items-start sm:text-left text-center items-center -mb-1 space-y-2.5">
            <a
              v-for="(technologie, indexTech) in skill.technologies"
              :key="indexTech"
            >
              <span class="bg-sky-100 text-sky-500 w-4 h-4 mr-2 rounded-full inline-flex items-center justify-center">
                <svg
                  fill="none"
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="3"
                  class="w-3 h-3"
                  viewBox="0 0 24 24"
                >
                  <path d="M20 6L9 17l-5-5" />
                </svg>
              </span>{{ technologie }}
            </a>
          </nav>
        <!-- ... -->
        </div>
      </div>
    </section>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import { themeChange } from 'theme-change'

export default defineComponent({
  name: 'AboutView',
  components: {
  },
  props: {
    mediaSize: {
      type: Number,
      default: 48,
      required: false
    }
  },
  data: () => ({
    color: 'red',
    skills: [
      { area: 'WebApps and Mobile', technologies: ['VUE', 'VUEX', 'NUXT SSR', 'REACT', 'NEXT SSR', 'REDUX/CONTEXT', 'Gatsby', 'Strapi', 'Ionic']},
      { area: 'UI/UX', technologies: ['Tailwind', 'ElemntUI', 'Bootstrap', 'Vuetify', 'Vuesax', 'Quasar'] },
      { area: 'API', technologies: ['REST', 'GraphQL', 'Apollo', ] },
      { area: 'Testing', technologies: ['Jest', 'SonarQube', 'Cypress', ] },
      { area: 'Server Side', technologies: ['Firebase', 'NodeJS', 'NestJS', ] },
      { area: 'Containers', technologies: ['Docker Service Infrastructure', ] },
      { area: 'SO', technologies: ['Linux', 'iOS' ] },
      { area: 'Preferred language', technologies: ['JavaScript', 'TypeScript' ] },
    ],
    socialsMedia: [
      { name: 'Linkedin', icon: 'linkedin', url: 'https://www.linkedin.com/in/diego-p%C3%A9rez-22180a142/'},
      { name: 'Github', icon: 'github', url: 'https://github.com/dforce2055'},
    ]
  }),
  async mounted() {
    themeChange(false)
  },
})
</script>
