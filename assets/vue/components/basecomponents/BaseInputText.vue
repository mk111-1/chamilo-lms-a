<template>
  <div class="field">
    <div class="p-float-label">
      <InputText
        :id="id"
        :model-value="modelValue"
        :class="{ 'p-invalid': isInvalid }"
        class="border-primary-gradient hover:border-primary focus:ring-primary"
        :aria-label="label"
        type="text"
        @update:model-value="$emit('update:modelValue', $event)"
      />
      <label
        v-t="label"
        :class="{ 'p-error': isInvalid }"
        :for="id"
        class="text-primary/40"
      />
    </div>
    <slot name="errors">
      <small v-if="isInvalid" v-t="errorText" class="p-error" />
    </slot>
  </div>
</template>

<script setup>
import InputText from "primevue/inputtext";

const props = defineProps({
  id: {
    type: String,
    require: true,
    default: "",
  },
  label: {
    type: String,
    required: true,
    default: "",
  },
  modelValue: {
    type: String,
    required: true,
  },
  errorText: {
    type: String,
    required: false,
    default: null,
  },
  isInvalid: {
    type: Boolean,
    required: false,
    default: false,
  },
});

defineEmits(["update:modelValue"])
</script>
