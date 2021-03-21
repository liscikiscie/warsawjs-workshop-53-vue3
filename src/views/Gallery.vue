<template>
  <div v-if="create">
    <h1 class="text-3xl font-bold text-center">Create meme</h1>
    <meme-generator @update:model-value="save" @cancel="create = false"/>
  </div>

  <div v-else>
    <h1 class="text-3xl font-bold text-center">
      Meme gallery
      <button class="p-2 ml-2 bg-blue-500 text-lg text-white font-bold rounded" @click="create = true">
        Create new
      </button>
    </h1>
    <main class="container mx-auto grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-1 gap-4 p-6">
      <img class="rounded-xl" :src="meme.url" v-for="meme in memes"/>
    </main>
  </div>
</template>

<script>
import {defineComponent, toRaw} from 'vue'
import MemeGenerator from '@/components/MemeGenerator.vue';


export default defineComponent({
  components: {MemeGenerator },
  data() {
    const memes = localStorage.getItem('memes');
    return {
      create: false,
      memes: memes ? JSON.parse(memes) : []
    }
  },
  methods: {
    save(meme) {
      this.memes = this.memes.concat([meme])
      this.create = false
    }
  },
  watch: {
    memes(value) {
      const valueStringified = JSON.stringify(toRaw(value));
      localStorage.setItem('memes', valueStringified)
    }
  },
})
</script>
