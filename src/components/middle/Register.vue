<template>
    <div class="register form-box">
        <div class="header">Registration</div>
        <div class="body">
            <form @submit.prevent="onRegister">
                <div class="field">
                    <div class="name">
                        <label for="login">Login</label>
                    </div>
                    <div class="value">
                        <input id="login"
                               name="login"
                               v-model="login"/>
                    </div>
                </div>
                <div class="field">
                    <div class="name">
                        <label for="password">Name</label>
                    </div>
                    <div class="value">
                        <input id="name"
                               name="name"
                               v-model="name"/>
                    </div>
                </div>
                <div class="field">
                    <div class="name">
                        <label for="password">Password</label>
                    </div>
                    <div class="value">
                        <input id="password"
                               type="password"
                               name="password"
                               v-model="password"/>
                    </div>
                </div>

                <div class="error">{{error}}</div>
                <div class="button-field">
                    <input type="submit"
                           value="Register">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Register',
        data: function () {
            return {
                login: "",
                name: "",
                password: "",
                error: ""
            }
        },
        beforeMount() {
            this.login = this.name = this.password = this.error = "";
            this.$root.$on("onRegisterValidationError", error => this.error = error);
        },
        methods: {
            onRegister: function () {
                this.$root.$emit("onRegister", this.login, this.name);
            }
        }
    };
</script>

<style scoped>

</style>
