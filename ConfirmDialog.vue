<script>
import StandartDialog from './StandartDialog';

export default {
  props: [
    'simple', // without NO btn
    'yesText',
    'noText',
    'notation',
  ],
  components: {
    StandartDialog,
  },
  computed: {
    yes() {
      return this.yesText || 'ХОРОШО';
    },
    no() {
      return this.noText || 'ОТМЕНА';
    },
  },
  methods: {
    cancel() {
      this.$emit('cancel');
      this.$emit('close');
    },
    confirm() {
      this.$emit('confirm');
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
      <div class="buttons">
        <button class="button is-primary" @click="confirm">
          <slot name="yesIcon"></slot>
          <span>{{yes}}</span>
        </button>
        <button class="button" @click="cancel" v-if="simple !== true">
          <slot name="noIcon"></slot>
          <span>{{no}}</span>
        </button>
      </div>
      <div class="modal__notation"><slot name="notation"></slot></div>
    </template>

    <template #extend>
      <slot name="extend"></slot>
    </template>
  </StandartDialog>
</template>

<style lang="scss">
.modal {
  &__notation {
    font-size: 10px;
    color: #999;
    margin-top: $size-normal;

    &:empty {
      display: none;
    }
  }
}
</style>
