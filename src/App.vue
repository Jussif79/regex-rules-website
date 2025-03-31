<template>
  <div class="container mx-auto">
    <LanguageSwitcher         
        :currentLanguage="currentLanguage" 
        @switch-language="switchLanguage"
        class="mb-8"
        />
    <RegexRule />
  </div>
  <footer>
    <p class="text-center text-gray-500 text-sm">
      &copy; 2025 Regex Rule Generator
    </p>
  </footer>
</template>

<script>
  import { ref } from 'vue'
  import LanguageSwitcher from './components/LanguageSwitcher.vue'
  import RegexRule from './components/RegexRule.vue'

  export default {
    components: {
      LanguageSwitcher,
      RegexRule
    },
    setup() {
      const currentLanguage = ref('de')
    }
  }
</script>