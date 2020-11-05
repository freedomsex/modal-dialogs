<script>
import WrappedDialog from './WrappedDialog';

export default {
  components: {
    WrappedDialog,
  },
};
</script>

<template>
  <WrappedDialog @close="$emit('close')">
    <div class="modal__caption">
      <slot name="title"></slot>
    </div>
    <div class="modal__body">
      <slot></slot>
    </div>
    <slot name="extend"></slot>
  </WrappedDialog>
</template>
