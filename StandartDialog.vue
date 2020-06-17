<script>
import BlankDialog from './BlankDialog';

export default {
  components: {
    BlankDialog,
  },
};
</script>

<template>
  <BlankDialog @close="$emit('close')">
    <template #title>
      <slot name="title"></slot>
    </template>

    <template #default>
      <slot></slot>
    </template>

    <template #extend>
      <div class="modal__footer">
        <slot name="footer"></slot>
      </div>
    </template>

    <slot name="extend"></slot>
  </BlankDialog>
</template>

<style lang="less">
</style>
