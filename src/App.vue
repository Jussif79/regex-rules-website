<template>
<div class="container mx-auto">
    <LanguageSwitcher :currentLanguage="currentLanguage" @switch-language="switchLanguage" class="mb-8" />
</div>

<h1 class="text-3xl font-bold mb-6">
    {{ currentLanguage === 'de' ? '10 Regeln für Regular Expressions' : '10 Rules for Regular Expressions' }}
</h1>

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
    }
}
</script>
