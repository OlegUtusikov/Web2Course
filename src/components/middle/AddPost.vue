<template>
    <form @submit.prevent="onAdd">
        <div>
            <label for="title">
                Title:
            </label>
            <input v-model="title"
                   class="title"
                   id="title"/>
        </div>
        <div>
            <label for="text">
                Text:
            </label>
            <textarea v-model="text"
                      id="text"
                      rows="20"></textarea>
        </div>
        <div class="error">{{error}}</div>
        <div>
            <input type="submit"
                   value="Add"/>
        </div>
    </form>
</template>

<script>
    export default {
        name: 'AddPost',
        data: function() {
            return {
                title: '',
                text: '',
                error: ''
            };
        },
        beforeMount() {
            this.title = this.text = this.error = '';
            this.$root.$on('onAddPostValidationError', error => this.error = error);
        }, methods: {
            onAdd: function() {
                this.$root.$emit('onAddPost', this.title, this.text);
            }
        }
    };
</script>

<style scoped>
    label {
        display: block;
        margin-top: 1rem;
    }

    .title, textarea {
        width: 60%;
        box-sizing: border-box;
    }

    input[type='submit'] {
        margin-top: 1rem;
        width: 6rem;
    }

    .error {
        color: var(--error-color);
    }
</style>
