<template>
  <div class="wrapper bg-white rounded-2xl max-w-xl md:max-w-5xl mx-10 shadow-2xl">
    <BaseHeader text="Send us a Message" />
    <form
      action="./index.php"
      method="POST"
      class="p-8 flex flex-wrap justify-between gap-y-12 gap-x-8 text-gray-800"
      @submit.prevent=""
    >
      <InputField
        v-for="data in InputsData"
        :key="data.id"
        :id="data.id"
        :type="data.type"
        :name="data.name"
        :placeholder="data.placeholder"
        @toggle="toggle"
        :isActive="data.isActive"
        ><span
          :class="['material-symbols-outlined', 'icon', { '!text-emerald-400': data.isActive }]"
        >
          {{ data.icon }}
        </span>
      </InputField>
      <BaseTextarea
        placeholder="Enter your message"
        @toggle="() => this.isActiveMessage = !this.isActiveMessage"
        :isActive="isActiveMessage"
      >
        <span
          :class="['material-symbols-outlined', 'icon', { '!text-emerald-400': isActiveMessage }]"
        >
          chat
        </span>
      </BaseTextarea>
      <BaseButton>Send Message</BaseButton>
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
      InputsData: [
        {
          id: 1,
          type: 'text',
          name: 'full_name',
          placeholder: 'Enter your name',
          icon: 'person',
          isActive: false,
          value:""
        },
        {
          id: 2,
          type: 'email',
          name: 'email',
          placeholder: 'Enter your email',
          icon: 'mail',
          isActive: false,
          value: "",
        },
        {
          id: 3,
          type: 'tel',
          name: 'number_phone',
          placeholder: 'Enter your number phone',
          icon: 'phone',
          isActive: false,
          value: "",
        },
        {
          id: 4,
          type: 'text',
          name: 'website',
          placeholder: 'Enter your website',
          icon: 'language',
          isActive: false,
          value: "",
        }
      ],
      isActiveMessage: false,
    }
  },
  methods: {
    toggle(id) {
      const element = this.InputsData.find(e => e.id === id);
      element.isActive = !element.isActive;
    },
  },
  mounted() {
    console.log(this.$refs);
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
