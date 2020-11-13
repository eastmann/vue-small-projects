<template>
    <div class="input-wrapper">
        <div class="label">
            <label :for="name">{{ name }}</label>
            <span class="error">{{ error }}</span>
        </div>
        <input
            @input="input"
            :value="value"
            :id="name"
            :type="type"
        />
    </div>
</template>

<script>
export default {
    props: {
        name: {
            type: String,
            required: true
        },
        rules: {
            type: Object // min, required
        },
        value: {
            type: String
        },
        type: {
            type: String
        }
    },
    methods: {
        input($evt) {
            this.$emit('update', {
                value: $evt.target.value,
                name: this.name,
                valid: !this.validate($evt.target.value)
            })
        },
        validate(value) {
            if (this.rules.required && !value) {
                return 'Required'
            }

            if (this.rules.min && value.length < this.rules.min) {
                return `Minimum length is ${this.rules.min}`
            }
        }
    },
    computed: {
        error() {
            return this.validate(this.value)
        }
    }
}
</script>

<style scoped>
    .input-wrapper {
        display: flex;
        flex-direction: column;
    }

    .label {
        display: flex;
        justify-content: space-between;
    }

    .error {
        color: red;
    }

    input {
        margin: 5px 0;
        padding: 10px;

        color: black;
        font-size: 16px;

        background: none;
        border: 1px solid silver;
        border-radius: 5px;
    }
</style>
