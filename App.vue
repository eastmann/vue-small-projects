<template>
    <form class="form" @submit.prevent="submit">
        <my-input
            name="Username"
            :rules="{ required: true, min: 5 }"
            :value="username.value"
            @update="update"
            type="text"
        />

        <my-input
            name="Password"
            :rules="{ required: true, min: 10 }"
            :value="password.value"
            @update="update"
            type="password"
        />

        <my-button
            color="white"
            background="darkslateblue"
            :disabled="!valid"
        />
    </form>
</template>

<script>
import MyButton from './MyButton.vue'
import MyInput from './MyInput.vue'

export default {
    components: {
        MyButton,
        MyInput
    },
    data() {
        return {
            username: {
                value: '',
                valid: false
            },
            password: {
                value: '',
                valid: false
            }
        }
    },
    methods: {
        update(payload) {
            // console.log(payload)
            this[payload.name.toLowerCase()] = {
                value: payload.value,
                valid: payload.valid
                }
        },
        submit($evt) {
            console.log($evt)
        }
    },
    computed: {
        valid() {
            return this.username.valid && this.password.valid
        }
    }
}
</script>

<style>
    body {
        font-family: Arial;
    }

    .form {
        max-width: 400px;
        width: 50%;
    }
</style>
