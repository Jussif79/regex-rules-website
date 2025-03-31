<template>
<div class="flex space-x-4 justify-center mt-10">
    <button @click="$emit('switch-language', 'de')" class="px-6 py-2 bg-blue-500 text-white font-semibold rounded-lg">Deutsch</button>
    <button @click="$emit('switch-language', 'en')" class="px-6 py-2 bg-blue-500 text-white font-semibold rounded-lg">Englisch</button>
</div>
</template>

<script>
export default {
    props: {
        currentLanguage: {
            type: String,
            required: true
        }
    },
    emits: ['switch-language']
}
</script>
