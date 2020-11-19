<template>
    <button @click="increment">
        {{ count }}
    </button>
    <button @click="a++">
        {{ a }}
    </button>
    <button @click="b++">
        {{ b }}
    </button>
    <ul>
        <li v-for="value in history">
            {{ value }}
        </li>
    </ul>
</template>

<script>
import { useNumbers } from './numbers'

export default {
    setup() {
        const {
            a,
            b,
            count,
            history,
            increment
        } = useNumbers()

        return {
            a,
            b,
            count,
            history,
            increment
        }
    }
}
</script>
