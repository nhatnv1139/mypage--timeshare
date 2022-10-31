<template>
  <div class="layout_form_main">
    <div class="layout_form_header">
      <!-- <LabelRequired v-if="isRequired" /> -->
      <i v-if="iconPrev" :class="iconPrev" aria-hidden="true"></i>
      <span v-if="labelText" class="">
        {{ labelText }}
      </span>
      <i v-if="icon" :class="icon" aria-hidden="true"></i>
       <LabelRequired v-if="isRequired" />
    </div>
    <div class="layout_form_Child"> 
      <slot></slot>
    </div>
  </div>
</template>

<script>
import LabelRequired from "@/components/LabelRequired/LabelRequired.vue";
import "@/assets/components/FormLayout.css";
export default {
  name: "FormLayout",
  components: {
    LabelRequired,
  },
  props: {
    labelText: {
      type: String,
      default: "",
    },
    icon: {
      type: String,
      default: "",
    },
    iconPrev: {
      type: String,
      default: "",
    },
    isRequired: {
      type: Boolean,
      default: false,
    },
    customCss: {
      type: String,
      default: "mt-2",
    },
  },
};
</script>

<style>
</style>