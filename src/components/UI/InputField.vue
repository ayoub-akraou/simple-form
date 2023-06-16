<template>
  <div
    :class="{ 'border-2 !border-emerald-400': isActive }"
    class="input-field border border-gray-300 rounded-md w-full md:w-[45%] flex items-center overflow-hidden"
  >
    <slot></slot>
    <input
      class="text-2xl outline-none py-4 flex-1"
      @focus="toggle"
      @blur="toggle"
      :type="type"
      :name="name"
      :placeholder="placeholder"
    />
  </div>
</template>

<script>
export default {
  props: ['type', 'name', 'placeholder', 'isActive'],
  methods: {
    toggle() {
      this.$emit("toggle")
    }
  }
}
</script>

<style scoped></style>
