<!-- eslint-disable max-len -->
<template>
  <section
    class="text-gray-600 body-font"
  >
    <div class="container px-5 py-12 mx-auto">
      <div class="flex flex-wrap -m-4">
        <div
          v-for="project in projects"
          :key="project.id"
          class="p-4 lg:w-1/3"
        >
          <div
            class="h-full dark:bg-gray-600 dark:text-gray-100 bg-gray-100 bg-opacity-75 px-8 pt-16 pb-24 rounded-lg overflow-hidden text-center relative"
          >
            <div class="md:p-2 p-1 w-2/2">
              <a
                :href="project.demoUrl"
                target="_blank"
              >
                <img
                  alt="gallery"
                  class="mx-auto w-full object-cover h-full object-center block"
                  :src="project.imgUrl || 'https://dummyimage.com/500x300'"
                  style="max-height: 180px;"
                >
              </a>
            </div>
            <h2 class="tracking-widest text-xs title-font font-medium text-gray-400 mb-1">
              {{ project.categories.toString() }}
            </h2>
            <h1 class="title-font sm:text-2xl text-xl font-medium text-gray-900 mb-3 capitalize">
              {{ project.title }}
            </h1>
            <p class="leading-relaxed mb-3">
              {{ project.description }}
            </p>
            <a
              :href="project.demoUrl"
              target="_blank"
              class="btn btn-ghost text-primary inline-flex items-center"
            >
              {{ $t('view-demo') }}
              <svg
                class="w-4 h-4 ml-2"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path d="M5 12h14" />
                <path d="M12 5l7 7-7 7" />
              </svg>
            </a>
            <div class="text-center mt-2 leading-none flex justify-center absolute bottom-10 left-0 w-full py-4 font-mono text-xs">
              {{ project.technologies }}
            </div>
            <div class="text-center mt-2 leading-none flex justify-center absolute bottom-0 left-0 w-full py-4">
              <div
                class="tooltip tooltip-top"
                :data-tip="`${$t('repository-visibility')}: ${project.visibility}`"
              >
                <a
                  :href="project.github"
                  target="_blank"
                >
                  <span
                    class="text-gray-400 inline-flex items-center leading-none text-sm"
                    :class="project.visibility === VISIBILITY.PUBLIC ? 'text-primary cursor-pointer hover:text-sky-600' : ''"
                  >
                    <svg
                      style="width:24px;height:24px"
                      viewBox="0 0 24 24"
                    >
                      <path
                        fill="currentColor"
                        d="M12,2A10,10 0 0,0 2,12C2,16.42 4.87,20.17 8.84,21.5C9.34,21.58 9.5,21.27 9.5,21C9.5,20.77 9.5,20.14 9.5,19.31C6.73,19.91 6.14,17.97 6.14,17.97C5.68,16.81 5.03,16.5 5.03,16.5C4.12,15.88 5.1,15.9 5.1,15.9C6.1,15.97 6.63,16.93 6.63,16.93C7.5,18.45 8.97,18 9.54,17.76C9.63,17.11 9.89,16.67 10.17,16.42C7.95,16.17 5.62,15.31 5.62,11.5C5.62,10.39 6,9.5 6.65,8.79C6.55,8.54 6.2,7.5 6.75,6.15C6.75,6.15 7.59,5.88 9.5,7.17C10.29,6.95 11.15,6.84 12,6.84C12.85,6.84 13.71,6.95 14.5,7.17C16.41,5.88 17.25,6.15 17.25,6.15C17.8,7.5 17.45,8.54 17.35,8.79C18,9.5 18.38,10.39 18.38,11.5C18.38,15.32 16.04,16.16 13.81,16.41C14.17,16.72 14.5,17.33 14.5,18.26C14.5,19.6 14.5,20.68 14.5,21C14.5,21.27 14.66,21.59 15.17,21.5C19.14,20.16 22,16.42 22,12A10,10 0 0,0 12,2Z"
                      />
                    </svg>
                  </span>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import {
  Project,
  VISIBILITY,
} from '../types'

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Cards',
  props: {
    projects: {
      type: Array as PropType<Project[]>,
      required: true
    }
  },
  data: () => ({
    VISIBILITY
  })
});
</script>
