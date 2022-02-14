<template>
    <div class="app">
        
        
    </div>
</template>

<script>
export default {
    data() {
        return {
            posts: [
                {id: 1, title: 'JavaScript', body: 'описание поста'},
                {id: 2, title: 'JavaScript', body: 'описание поста 2'},
                {id: 3, title: 'JavaScript', body: 'описание поста 3'},
            ],
            title: '',
            body: '',
        }
    }, methods: {
        creatPost() {
            const newPost = {
                id: Date.now(),
                title: this.title,
                body: this.body,
            }
            this.posts.push(newPost);
            this.title = '';
            this.body = '';
        },
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    padding: 20px;
}

form {
    display: flex;
    flex-direction: column;
}



.input {
    widows: 100%;
    border: 1px solid teal;
    margin-top: 15px;
    padding: 10px 15px;
}

.btn {
    align-self: flex-end;
    margin-top: 15px;
    padding: 10px 15px;
    background: none;
    color: teal;
    border: 1px solid teal;
}
</style>