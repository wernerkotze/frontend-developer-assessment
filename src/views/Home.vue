<template>
  <div class="content-center">
        <form class="content-center">
          <div class="md:flex md:items-center mb-6">
            <div class="md:w-1/3">
              <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                Title
              </label>
            </div>
            <div class="md:w-1/3">
              <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" value="" v-model="title">
            </div>
          </div>
          <div class="md:flex md:items-center mb-6">
            <div class="md:w-1/3">
              <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-username" >
                Body
              </label>
            </div>
            <div class="md:w-1/3">
              <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-username" type="text" placeholder="" v-model="body">
            </div>
          </div>
          <div class="md:flex md:items-center">
            <div class="md:w-1/3"></div>
            <div class="md:w-1/3">
              <button class="shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="button" @click="post">
                Post
              </button>
            </div>
          </div>
        </form>
  </div>
</template>
<script>

export default {
    name: 'home',
    data() {
        return {
          title: '',
          body: ''
        }
    },
    methods: {
        post() {
            fetch('https://jsonplaceholder.typicode.com/posts', {
                method: 'POST',
                body: JSON.stringify({
                  title: this.title,
                  body:  this.body,
                  userId: 1
                }),
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  "Accept": "application/json"
                }
            })
            .then(response => response.json())
            .then((json) => console.log(json))
        }
    }
};
    
</script>
