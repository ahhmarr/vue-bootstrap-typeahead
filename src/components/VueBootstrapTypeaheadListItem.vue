<template>
  <a
    tabindex="0"
    href="#"
    :class="textClasses"
    @mouseover="active = true"
    @mouseout="active = false"
    :id="`result-${index}`"
  >
    <slot name="suggestion" v-bind="{ data: data, htmlText: htmlText }">
      <span v-html="htmlText"></span>
    </slot>
  </a>
</template>

<script>
export default {
  name: "VueBootstrapTypeaheadListItem",

  props: {
    data: {},
    htmlText: {
      type: String
    },
    backgroundVariant: {
      type: String
    },
    textVariant: {
      type: String
    },
    index: {
      type: Number
    }
  },

  data() {
    return {
      active: false
    };
  },

  computed: {
    textClasses() {
      let classes = "";
      classes += this.active ? "active" : "";
      classes += this.backgroundVariant ? ` bg-${this.backgroundVariant}` : "";
      classes += this.textVariant ? ` text-${this.textVariant}` : "";
      return `vbst-item list-group-item list-group-item-action ${classes}`;
    }
  }
};
</script>
