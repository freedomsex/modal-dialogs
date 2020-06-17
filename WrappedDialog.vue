<script>
import ModalDialog from './ModalDialog';

export default {
  components: {
    ModalDialog,
  },
};
</script>

<template>
  <ModalDialog @close="$emit('close')">
    <div class="box">
      <slot></slot>
    </div>
    <slot name="extend"></slot>
  </ModalDialog>
</template>

<style lang="less">
</style>
