<template>
<div class="container mx-auto">
    <LanguageSwitcher :currentLanguage="currentLanguage" @switch-language="switchLanguage" class="mb-8" />
</div>

<h1 class="text-3xl font-bold mb-6">
    {{ currentLanguage === 'de' ? '10 Regeln für Regular Expressions' : '10 Rules for Regular Expressions' }}
</h1>

<div class="grid gap-6">
    <RegexRule 
          v-for="(rule, index) in rules" 
          :key="index" 
          :rule="rule" 
          :language="currentLanguage"
        />
</div>

<footer>
    <p class="text-center text-gray-500 text-sm">
        &copy; 2025 Regex Rule Generator
    </p>
</footer>
</template>

<script>
import {
    ref
} from 'vue'
import LanguageSwitcher from './components/LanguageSwitcher.vue'
import RegexRule from './components/RegexRule.vue'

export default {
    components: {
        LanguageSwitcher,
        RegexRule
    },
    setup() {
        const currentLanguage = ref('de')

        const rules = [{
            title: {
                de: 'Einfache Zeichenübereinstimmung',
                en: 'Simple character matching'
            },
            description: {
                de: 'Ein einzelnes Zeichen in einem Regex sucht nach genau diesem Zeichen.',
                en: 'A single character in a regex matches that exact character.'
            },
            example: {
                de: 'Das Muster "a" findet "a" in "apple".',
                en: 'The pattern "a" matches "a" in "apple".'
            },
            pattern: 'a',
            testString: 'apple'
        }, ]

        const switchLanguage = (lang) => {
            currentLanguage.value = lang
        }

        return {
            currentLanguage,
            rules,
            switchLanguage
        }
    }
}
</script>
