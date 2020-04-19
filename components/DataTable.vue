<template>
  <data-view :title="title" :title-id="titleId" :date="date" :url="url">
    <template v-slot:button>
      <span />
    </template>
    <v-data-table
      :headers="chartData.headers"
      :items="chartData.datasets"
      :items-per-page="-1"
      :hide-default-footer="true"
      :height="240"
      :fixed-header="true"
      :mobile-breakpoint="0"
      class="cardTable"
      :custom-sort="customSort"
    />
    <div class="note">
      {{ $t('※退院とは新型コロナウイルス感染症が治癒した者') }}<br />
      {{ $t('※退院には死亡退院を含む') }}
    </div>
    <template v-slot:infoPanel>
      <data-view-basic-info-panel
        :l-text="info.lText"
        :s-text="info.sText"
        :unit="info.unit"
      />
    </template>
  </data-view>
</template>

<style lang="scss">
.cardTable {
  &.v-data-table {
    th {
      padding: 8px 10px;
      height: auto;
      border-bottom: 1px solid $gray-4;
      white-space: nowrap;
      color: $gray-2;
      font-size: 12px;
      &.text-center {
        text-align: center;
      }
    }
    tbody {
      tr {
        color: $gray-1;
        td {
          padding: 8px 10px;
          height: auto;
          font-size: 12px;
          &.text-center {
            text-align: center;
          }
        }
        &:nth-child(odd) {
          td {
            background: rgba($gray-4, 0.3);
          }
        }
        &:not(:last-child) {
          td:not(.v-data-table__mobile-row) {
            border: none;
          }
        }
      }
    }
  }
}
.note {
  padding: 8px;
  font-size: 12px;
  color: #808080;
}
</style>

<script>
import DataView from '@/components/DataView.vue'
import DataViewBasicInfoPanel from '@/components/DataViewBasicInfoPanel.vue'

const excludeAges = ['就学児', '未就学児']

export default {
  components: { DataView, DataViewBasicInfoPanel },
  props: {
    title: {
      type: String,
      default: ''
    },
    titleId: {
      type: String,
      default: ''
    },
    chartData: {
      type: Object,
      default: () => {}
    },
    date: {
      type: String,
      default: ''
    },
    info: {
      type: Object,
      required: false,
      default: () => {}
    },
    url: {
      type: String,
      required: false,
      default: ''
    }
  },
  methods: {
    customSort(items, index, isDescending) {
      if (isDescending[0] === undefined) return items
      if (index[0] === '年代') {
        return this.createSortAgeData(items, index[0], isDescending[0])
      } else {
        items.sort((a, b) => {
          if (b[index[0]] < a[index[0]]) {
            return isDescending[0] ? -1 : 1
          } else {
            return isDescending[0] ? 1 : -1
          }
        })
      }
      return items
    },
    createSortAgeData(items, index, isDescending) {
      const excludeItems = {}
      const translatedAges = excludeAges.map(v => this.$t(v))

      const filterItems = items.filter(item => {
        if (translatedAges.includes(item[index])) {
          excludeItems[item[index]] = excludeItems[item[index]] || []
          excludeItems[item[index]].push(item)
          return false
        } else {
          return true
        }
      })

      filterItems.sort((a, b) => {
        if (b[index] < a[index]) {
          return 1
        } else {
          return -1
        }
      })

      translatedAges.forEach(v => {
        if (!excludeItems[v]) {
          return
        }

        excludeItems[v].forEach(item => {
          filterItems.unshift(item)
        })
      })

      if (isDescending) {
        filterItems.reverse()
      }

      return filterItems
    }
  }
}
</script>
