<template>
  <div class="app" @submit.prevent>
  <form>
    <h3>Create post</h3>
    <input
        v-bind:value="title"
        class="input"
        type="text"
        @input="inputTitle"
        placeholder="Name">
    <input
        v-bind:value="body"
        class="input"
        @input="inputBody"
        type="text"
        placeholder="Description">
    <button
        class="add_button"
        @click="createPost">Create</button>
  </form>
  <div class="post" v-for="post in posts">
    <div><strong>Name:</strong> {{post.title}}</div>
    <div><string>Description:</string> {{post.body}}</div>
  </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      posts: [
        {id: 1, title: 'Js1', body: 'Description12'},
        {id: 2, title: 'Js2', body: 'Description123'},
        {id: 3, title: 'Js3', body: 'Description1111'},
        {id: 4, title: 'Js4', body: 'Description1444'},
      ],
      title: '',
      body: '',
    }
  },
  methods: {
      createPost() {
        const newPost = {
          id: Date.now(),
          title: this.title,
          body: this.body,
        }
        this.posts.push(newPost);
      },
      inputTitle(event) {
        this.title = event.target.value;
      },
      inputBody(event) {
        this.body = event.target.value;
      }
  }
}
</script>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .post {
    border: 2px solid blueviolet;
    margin-top: 1rem;
    padding: 0.5rem;
    padding: 15px;
  }

  .input {
    width: 100%;
    border: 1px solid blueviolet;
    margin-top: 0.5rem;
    padding: 10px 15px;
  }

  form {
    display: flex;
    flex-direction: column;
  }

  .app {
    padding: 15px;
  }

  .add_button {
    margin-top: 1rem;
    padding: 0.5rem;
    font-size: 1.25rem;
    align-self: end;
    background: none;
    color: teal;
    border: 1px solid teal;
  }
</style>