<!-- eslint-disable max-len -->
<!-- eslint-disable vuejs-accessibility/anchor-has-content -->
<template>
  <footer class="text-gray-600 body-font">
    <div class="border-t border-gray-200">
      <div class="container px-5 py-8 flex flex-wrap mx-auto items-center">
        <div class="flex md:flex-nowrap flex-wrap justify-center items-end md:justify-start">
          <div class="relative sm:w-64 w-40 sm:mr-4 mr-2">
            <label
              for="footer-field"
              class="leading-7 text-sm text-gray-600"
            >
              Placeholder
            </label>
            <input
              type="text"
              id="footer-field"
              name="footer-field"
              class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:ring-2 focus:bg-transparent focus:ring-blue-200 focus:border-blue-500 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out"
            >
          </div>
          <button class="inline-flex text-white bg-blue-500 border-0 py-2 px-6 focus:outline-none hover:bg-blue-600 rounded">
            Button
          </button>
          <p class="text-gray-500 text-sm md:ml-6 md:mt-0 mt-2 sm:text-left text-center">
            Bitters chicharrones fanny pack
            <br class="lg:block hidden">waistcoat green juice
          </p>
        </div>
        <span class="inline-flex lg:ml-auto lg:mt-0 mt-6 w-full justify-center md:justify-start md:w-auto">
          <a
            v-for="(socialMedia, index) in socialsMedia"
            :key="index"
            :href="socialMedia.url"
            target="_blank"
            class="hover:text-primary mr-3"
          >
            <mdicon
              :name="socialMedia.icon"
              :size="mediaSize"
            />
          </a>
        </span>
      </div>
    </div>
    <div class="bg-gray-100 dark:bg-gray-900">
      <div class="container mx-auto py-4 px-5 flex flex-wrap flex-col sm:flex-row">
        <p class="text-gray-500 text-sm text-center sm:text-left">
          © {{ new Date().getFullYear() }} dforce2055 —
          <a
            href="https://www.linkedin.com/in/diego-p%C3%A9rez-22180a142/"
            class="text-gray-600 ml-1 dark:text-primary"
            target="_blank"
            rel="noopener noreferrer"
          >@dforce2055</a>
        </p>
        <span class="sm:ml-auto sm:mt-0 mt-2 sm:w-auto w-full sm:text-left text-center text-gray-500 text-sm">Enamel pin tousled raclette tacos irony</span>
      </div>
    </div>
  </footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'FooterComponent',
  props: {
    mediaSize: {
      type: Number,
      default: 48,
      required: false
    }
  },
  data: () => ({
    socialsMedia: [
      { name: 'Linkedin', icon: 'linkedin', url: 'https://www.linkedin.com/in/diego-p%C3%A9rez-22180a142/'},
      { name: 'Github', icon: 'github', url: 'https://github.com/dforce2055'},
    ]
  }),
});
</script>
