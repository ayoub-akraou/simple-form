<template>
  <div class="wrapper bg-white rounded-2xl max-w-xl md:max-w-5xl mx-10 shadow-2xl">
    <BaseHeader text="Send us a Message" />
    <form
      action="./index.php"
      method="POST"
      class="p-8 flex flex-wrap justify-between gap-y-12 gap-x-8 text-gray-800"
    >
      <InputField
        type="text"
        name="name"
        placeholder="Enter your name"
        @toggle="toggle('isActiveName')"
        :isActive="isActiveName"
        ><span :class="['material-symbols-outlined', 'icon', { '!text-emerald-400': isActiveName }]">
          person
        </span>
      </InputField>
      <InputField
        type="email"
        name="email"
        placeholder="Enter your email"
        @toggle="toggle('isActiveEmail')"
        :isActive="isActiveEmail"
        >
        <span :class="['material-symbols-outlined', 'icon', { '!text-emerald-400': isActiveEmail }]">
          mail
        </span>
      </InputField>
      <InputField
        type="tel"
        name="number_phone"
        placeholder="Enter your number phone"
        @toggle="toggle('isActivePhone')"
        :isActive="isActivePhone"
        ><span
        :class="['material-symbols-outlined', 'icon', { '!text-emerald-400': isActivePhone }]"
        >
        phone
        </span></InputField
      >
      <InputField
        type="url"
        name="website"
        placeholder="Enter your website"
        @toggle="toggle('isActiveWebsite')"
        :isActive="isActiveWebsite"
        ><span
        :class="['material-symbols-outlined', 'icon', { '!text-emerald-400': isActiveWebsite }]"
        >
        language
        </span></InputField
      >
      <BaseTextarea placeholder="Enter your message" @toggle="toggle('isActiveMessage')" :isActive="isActiveMessage">
        <span :class="['material-symbols-outlined', 'icon', { '!text-emerald-400': isActiveMessage }]"> chat </span>
      </BaseTextarea>
      <BaseButton @click.prevent>Send Message</BaseButton>
    </form>
  </div>
</template>

<script>
import BaseHeader from '../components/UI/BaseHeader.vue'
import InputField from '../components/UI/InputField.vue'
import BaseTextarea from '../components/UI/BaseTextarea.vue'
import BaseButton from '../components/UI/BaseButton.vue'

export default {
  components: {
     BaseButton,
    BaseHeader,
    InputField,
    BaseTextarea
  },
  data() {
    return {
      isActiveName: false,
      isActiveEmail: false,
      isActivePhone: false,
      isActiveWebsite: false,
      isActiveMessage: false,
    }
  },
  methods: {
    toggle(id) {
      const element = this.InputsData.find(e => e.id === id);
      element.isActive = !element.isActive;
    },
    toggle
  }
}
</script>

<style>
@tailwind components;

@layer components {
  .icon {
    @apply text-gray-400 px-4;
  }
}
</style>
