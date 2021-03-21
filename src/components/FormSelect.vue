<template>
  <div class="flex border rounded">
    <label for="background" class="p-2 font-bold w-40 bg-gray-50">{{  label  }}</label>
    <select
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        class="flex-grow bg-white p-2 outline-none border-none" id="background">
      <option class="py-1" :value="choice.value" v-for="choice in choices"> {{ choice.name }}</option>
    </select>
  </div>
</template>

<script>
export default {
  props: ['label', 'modelValue', 'choices'],
  emits: ['update:modelValue']
}
</script>