<template>
<div class="p-6 rounded-lg">
    <h2 class="text-xl font-bold mb-2">{{ rule.title[language] }}</h2>
    <p class="mb-4">{{ rule.description[language] }}</p>
    <div>
        <p class="font-semibold mb-2">{{ language === 'de' ? 'Beispiel:' : 'Example:' }}</p>
        <p class="mb-2">{{ rule.example[language] }}</p>
        <div class="flex items-center space-x-4">
            <span class="font-mono px-2 py-1 rounded">{{ rule.pattern }}</span>
            <span>→</span>
            <span class="font-mono">{{ rule.testString }}</span>
        </div>
    </div>
</div>
</template>

<script>
export default {
    props: {
        rule: {
            type: Object,
            required: true
        },
        language: {
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>
.p-6 {
    background-color: #EFE7DA
}
</style>
