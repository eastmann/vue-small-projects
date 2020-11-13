<template>
    <button
        :style="{ background, color }"
        :class="{ '-disabled' : disabled }">
        Button
    </button>
</template>

<script>
export default {
    props: {
        color: {
            type: String,
        },
        background: {
            type: String
        },
        disabled: {
            type: Boolean
        }
    }
}
</script>

<style scoped>
    button {
        padding: 10px 40px;

        color: black;
        font-size: 16px;

        background: none;
        border: none;
        border-radius: 5px;

        cursor: pointer;
    }

    button:hover {
        filter: brightness(125%);
    }

    .-disabled {
        opacity: 0.5;
        pointer-events: none;
    }
</style>
