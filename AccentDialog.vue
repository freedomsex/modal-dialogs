<script>
import ModalDialog from './ModalDialog';

export default {
  props: ['title', 'type', 'yesText'],
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
      return this.yesText || 'Хорошо';
    },
  },
  methods: {
    confirm() {
      this.$emit('confirm');
      this.$emit('close');
    },
  },
  components: {
    ModalDialog,
  },
};
</script>

<template>
  <ModalDialog @close="$emit('close')">
    <div class="dialog-caption">
      <div class="dialog-caption__title">
        {{title}}
      </div>
      <div class="dialog-caption__option">
        <slot name="option"></slot>
      </div>
    </div>
    <div class="modal-dialog__wrapper capped">
      <slot name="content"></slot>
    </div>
    <slot></slot>
  </ModalDialog>
</template>

<style lang="scss">
.dialog-caption {
  background: $primary;
  color: $scheme-main;
  font-size: 16px;
  padding: ($size-normal + $size-normal * 0.2) $size-normal $size-normal;
  display: flex;
  &__title {
    flex: 3 1 auto;
    margin-right: 10px;
    font-weight: bold;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
  &__option {
    flex: 0 0 auto;
    color: $scheme-main;
    cursor: pointer;
    a {
      color: $scheme-main;
      display: inline-block;
    }
    .material-icons {
      vertical-align: middle;
      position: relative;
      top: -1px;
    }
    .account {
      border-bottom: 1px dashed #bbcccc;
      font-size: 15px;
      padding-bottom: 1px;
    }
  }

  &.warning {
    background: $warning;
  }
}
</style>
