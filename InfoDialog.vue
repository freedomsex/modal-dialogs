<script>
import StandartDialog from './StandartDialog';

export default {
  props: ['type', 'strict', 'yesText'],
  components: {
    StandartDialog,
  },
  computed: {
    style() {
      const btn = {
        default: '',
        success: 'is-success',
        warning: 'is-warning',
        danger: 'is-danger',
        info: 'is-info',
      };
      return this.type ? btn[this.type] : 'is-primary';
    },
    yes() {
      return this.yesText || 'ХОРОШО';
    },
  },
  methods: {
    confirm() {
      this.$emit('confirm');
      if (!this.strict) {
        this.$emit('close');
      }
    },
  },
};
</script>


<template>
  <StandartDialog @close="$emit('close')">
    <template #title>
      <slot name="title"></slot>
    </template>

    <template #default>
      <slot></slot>
    </template>

    <template #footer>
      <button class="button" :class="style" @click="confirm">
        <slot name="yesIcon"></slot>
        <span>{{yes}}</span>
      </button>
    </template>

    <template #extend>
      <slot name="extend"></slot>
    </template>
  </StandartDialog>
</template>
