<template>
    <div class="flex space-x-4">
        <button @click = "$emit('switch-language', 'de')" class="px-4 py-2 rounded">Deutsch</button>
        <button @click="$emit('switch-language', 'en')" class="px-4 py-2 rounded" >Englisch</button>
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