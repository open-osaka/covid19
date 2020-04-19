<template>
  <data-view class="SvgCard" :title="title" :title-id="titleId" :date="date">
    <slot />
    <div class="note">
      {{ note }}
    </div>
  </data-view>
</template>

<style lang="scss" scoped>
.SvgCard {
  ::v-deep svg {
    width: 100%;
  }
  .Graph-Desc {
    margin-top: 10px;
    margin-bottom: 0;
    font-size: 12px;
    color: $gray-3;
  }
}
</style>

<script>
import DataView from '@/components/DataView.vue'

export default {
  components: { DataView },
  props: {
    title: {
      type: String,
      default: ''
    },
    titleId: {
      type: String,
      default: ''
    },
    date: {
      type: String,
      default: ''
    },
    note: {
      type: String,
      required: false,
      default: ''
    }
  }
}
</script>
