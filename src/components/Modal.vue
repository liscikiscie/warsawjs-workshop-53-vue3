<template>
    <div class="h-screen w-full fixed left-0 top-0 flex justify-center items-center bg-black bg-opacity-50">
      <!-- modal -->
      <div class="bg-white rounded shadow-lg">
        <!-- modal header -->
        <div class="border-b px-4 py-2 flex justify-between items-center">
          <h3 class="font-semibold text-lg">{{ title }}</h3>
          <button class="text-black close-modal"
                  @click="updateState">
            &cross;
          </button>
        </div>
        <!-- modal body -->
        <div class="p-6">
          <slot/>
        </div>
      </div>
    </div>
</template>
<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Modal',
  props: {
    title: {
      type: String,
      default: ''
    }
  },
  emits: [ 'update:modelValue' ],
  methods: {
    updateState() {
      this.$emit('update:modelValue', false);
    }
  }
})
</script>
