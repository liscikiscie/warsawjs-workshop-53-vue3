<template>
  <div class="flex border rounded">
    <label class="p-2 font-bold w-40 bg-gray-50">{{ label }}</label>
    <input
        class="p-2 outline-none"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        :placeholder="placeholder"
    />
  </div>
</template>

<script>
export default {
  props: ['label', 'placeholder', 'modelValue'],
  emits: ['update:modelValue']
}
</script>