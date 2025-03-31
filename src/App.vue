<template>
<div class="container mx-auto">
    <LanguageSwitcher :currentLanguage="currentLanguage" @switch-language="switchLanguage" class="mb-8" />
</div>

<h1 class="text-3xl font-bold mb-6 text-white">
    {{ currentLanguage === 'de' ? '10 Regeln für Regular Expressions' : '10 Rules for Regular Expressions' }}
</h1>

<div class="grid gap-6">
    <RegexRule v-for="(rule, index) in rules" :key="index" :rule="rule" :language="currentLanguage" />
</div>

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
            },
            {
                title: {
                    de: 'Punkt (beliebiges Zeichen)',
                    en: 'Dot (any character)'
                },
                description: {
                    de: 'Der Punkt . steht für ein beliebiges einzelnes Zeichen (ausser Zeilenumbruch).',
                    en: 'The dot . matches any single character (except newline).'
                },
                example: {
                    de: 'Das Muster "a.e" findet "ape" und "ate" in "ape ate".',
                    en: 'The pattern "a.e" matches "ape" and "ate" in "ape ate".'
                },
                pattern: 'a.e',
                testString: 'ape ate'
            },
            {
                title: {
                    de: 'Zeichenklassen',
                    en: 'Character classes'
                },
                description: {
                    de: 'Eckige Klammern [] definieren eine Zeichenklasse - eines der Zeichen innerhalb wird gematcht.',
                    en: 'Square brackets [] define a character class - any one character inside will be matched.'
                },
                example: {
                    de: 'Das Muster "[aeiou]" findet alle Vokale in "hello world".',
                    en: 'The pattern "[aeiou]" matches all vowels in "hello world".'
                },
                pattern: '[aeiou]',
                testString: 'hello world'
            },
            {
                title: {
                    de: 'Verneinte Zeichenklassen',
                    en: 'Negated character classes'
                },
                description: {
                    de: 'Ein ^ innerhalb von [] verneint die Zeichenklasse - es matcht alles ausser den angegebenen Zeichen.',
                    en: 'A ^ inside [] negates the character class - matches anything except the specified characters.'
                },
                example: {
                    de: 'Das Muster "[^0-9]" findet alle Nicht-Ziffern in "a1b2c3".',
                    en: 'The pattern "[^0-9]" matches all non-digits in "a1b2c3".'
                },
                pattern: '[^0-9]',
                testString: 'a1b2c3'
            },
            {
                title: {
                    de: 'Wiederholungen mit * und +',
                    en: 'Repetitions with * and +'
                },
                description: {
                    de: '* steht für 0 oder mehr, + steht für 1 oder mehr Wiederholungen des vorherigen Elements.',
                    en: '* means 0 or more, + means 1 or more repetitions of the preceding item.'
                },
                example: {
                    de: 'Das Muster "a+" findet alle "a"s in "aaaab".',
                    en: 'The pattern "a+" matches all "a"s in "aaaab".'
                },
                pattern: 'a+',
                testString: 'aaaab'
            },
            {
                title: {
                    de: 'Optionale Zeichen mit ?',
                    en: 'Optional characters with ?'
                },
                description: {
                    de: 'Ein ? macht das vorherige Zeichen optional (0 oder 1 Vorkommen).',
                    en: 'A ? makes the preceding character optional (0 or 1 occurrences).'
                },
                example: {
                    de: 'Das Muster "colou?r" findet sowohl "color" als auch "colour".',
                    en: 'The pattern "colou?r" matches both "color" and "colour".'
                },
                pattern: 'colou?r',
                testString: 'color colour'
            },
            {
                title: {
                    de: 'Ankerpunkte ^ und $',
                    en: 'Anchors ^ and $'

                },
                description: {
                    de: '^ matcht den Anfang, $ das Ende eines Strings.',
                    en: '^ matches the start, $ matches the end of a string.'
                },
                example: {
                    de: 'Das Muster "^Start" findet "Start" nur am Anfang des Strings.',
                    en: 'The pattern "^Start" matches "Start" only at the start of the string.'
                },
                pattern: '^Start',
                testString: 'Start end\nNot Start'
            },
            {
                title: {
                    de: 'Escape-Sonderzeichen',
                    en: 'Escaping special characters'
                },
                description: {
                    de: 'Ein Backslash \ vor einem Sonderzeichen matcht das Zeichen selbst.',
                    en: 'A backslash \ before a special character matches the character itself.'
                },
                example: {
                    de: 'Das Muster "\\." findet Punkte in "a.b.c".',
                    en: 'The pattern "\\." matches dots in "a.b.c".'
                },
                pattern: '\\.',
                testString: 'a.b.c'
            },
            {
                title: {
                    de: 'Gruppierung mit ()',
                    en: 'Grouping with ()'
                },
                description: {
                    de: 'Runde Klammern () gruppieren Teile eines Musters und fangen Gruppen für Rückreferenzen.',
                    en: 'Parentheses () group parts of a pattern and capture groups for backreferences.'
                },
                example: {
                    de: 'Das Muster "(ab)+" findet "abab" in "ababc".',
                    en: 'The pattern "(ab)+" matches "abab" in "ababc".'
                },
                pattern: '(ab)+',
                testString: 'ababc'
            },
            {
                title: {
                    de: 'Oder-Operator |',
                    en: 'OR operator |'
                },
                description: {
                    de: 'Der | Operator matcht entweder das Muster davor oder danach.',
                    en: 'The | operator matches either the pattern before or after it.'
                },
                example: {
                    de: 'Das Muster "cat|dog" findet "cat" und "dog" in "cat dog mouse".',
                    en: 'The pattern "cat|dog" matches "cat" and "dog" in "cat dog mouse".'
                },
                pattern: 'cat|dog',
                testString: 'cat dog mouse'
            }
        ]

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
