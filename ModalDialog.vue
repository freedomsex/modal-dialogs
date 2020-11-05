<script>
export default {
  methods: {
    onEsc(event) {
      if (event.keyCode === 27) {
        this.$emit('close');
      }
    },
  },
  mounted() {
    document.addEventListener('keydown', this.onEsc);
  },
  beforeDestroy() {
    document.removeEventListener('keydown', this.onEsc);
  },
};
</script>

<template>
  <div class="modal is-active" transition="modal">
    <div class="modal-background" @click="$emit('close')"></div>
    <div class="modal-content">
      <slot></slot>
    </div>
    <slot name="extend"></slot>
    <button class="modal-close is-large" @click="$emit('close')"></button>
  </div>
</template>

<style lang="scss">
.modal {
  button {
    text-transform: uppercase;
  }

  .modal-content {
    text-align: left;
    white-space: normal;
    &.capped {
      padding-top: $size-normal;
    }
  }

  &__caption {
    font-size: 1.5em;
    font-weight: bold;
  }

  .body-spacer {
    margin-bottom: $size-normal;
  }

  &__section {
    margin: 0 0 $size-normal;
  }

  &__body {
    font-size: 1em;
    margin: $size-small 0 $size-small;
    .wide-content {
      margin: 0 -1.25rem;
    }
  }
  &__centred {
    text-align: center;
  }
  &__options {
    .material-icons {
      vertical-align: middle;
      position: relative;
      top: -1px;
      font-size: 20px;
    }
  }
}

.modal-enter,
.modal-leave {
  opacity: 0;
}

.modal-enter .modal-dialog__container,
.modal-leave .modal-dialog__container {
  transform: scale(1.1);
}
</style>
