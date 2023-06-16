<template>
  <div class="textarea-field flex py-4 border border-gray-300 rounded-md w-full overflow-hidden"
  :class="{'!border-2 !border-emerald-400': isActive}">
    <slot></slot>
    <textarea
      name="message"
      id="message"
      class="w-full text-2xl outline-none h-44 max-h-72"
      :placeholder="placeholder"
      value=""
      @focus="toggle"
      @blur="toggle"
    >
    </textarea>
  </div>
</template>

<script>
export default {
  props: ['placeholder', 'isActive'],
  methods: {
    toggle() {
      this.$emit('toggle')
    }
  }
}
</script>

<style></style>
