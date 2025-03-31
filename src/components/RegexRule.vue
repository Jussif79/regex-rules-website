<template>
<div class="p-6 rounded-lg shadow-md bg-white border-l-4 border-e55812">
    <h2 class="text-xl font-bold mb-2 text-0e4749">{{ rule.title[language] }}</h2>
    <p class="mb-4">{{ rule.description[language] }}</p>
    <div class="bg-gray-100 p-4 rounded">
        <p class="font-semibold mb-2">{{ language === 'de' ? 'Beispiel:' : 'Example:' }}</p>
        <p class="mb-2">{{ rule.example[language] }}</p>
        <div class="flex items-center space-x-4">
            <span class="font-mono bg-95c623 px-2 py-1 rounded text-white">{{ rule.pattern }}</span>
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
