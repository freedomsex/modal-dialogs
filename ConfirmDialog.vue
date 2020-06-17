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
      return this.yesText || this.$t('ok');
    },
    no() {
      return this.noText || this.$t('no');
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

<i18n>
{
  "ru": {
    "ok": "ХОРОШО",
    "no": "ОТМЕНА"
  },
  "en": {
    "ok": "OKAY",
    "no": "CANCEL"
  },
  "kz": {
    "ok": "ЖАҚСЫ",
    "no": "ЖОЮҒА"
  },
  "ua": {
    "ok": "ДОБРЕ",
    "no": "СКАСУВАТИ"
  }
}
</i18n>

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
          {{yes}}
        </button>
        <button class="button" @click="cancel" v-if="simple !== true">
          <slot name="noIcon"></slot>
          {{no}}
        </button>
      </div>
      <div class="modal__notation"><slot name="notation"></slot></div>
    </template>

    <template #extend>
      <slot name="extend"></slot>
    </template>
  </StandartDialog>
</template>

<style lang="less">
.modal {
  &__notation {
    font-size: 10px;
    color: #999;
    margin-top: @indent-sm;

    &:empty {
      display: none;
    }
  }
}
</style>
