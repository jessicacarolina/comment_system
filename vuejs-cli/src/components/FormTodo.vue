<template>
    <div class="form-todo form-group">
            <p>
                <input type="text" name="author" class="form-control" placeholder="nome" v-model="name">
            </p>
            <p>
                <textarea name="message" class="form-control" placeholder="Comentário" v-model="message"></textarea>
            </p>
            <button v-on:click="addComment" class="btn btn-primary" type="submit">Comentar</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                message: ''
            }
        },
        methods: {
            addComment() {
                if (this.message.trim() === '') {
                    return;
                }

                this.$emit('add-todo', {
                    name: this.name,
                    message: this.message,
                });

                this.name = '';
                this.message = '';
            }
        }
    }
</script>