<template>
  <data-view
    :title="title"
    :title-id="titleId"
    :date="date"
    :url="url"
    :linktitle="linktitle"
  >
    <template v-slot:button>
      <span />
    </template>
    <v-overlay
      opacity="0"
      absolute
      :value="!loaded"
      justify-center
      align-center
    >
      <scale-loader color="#ff8d5b" />
    </v-overlay>
    <v-overlay absolute :value="error" justify-center align-center>
      <v-alert type="error" color="#AD2121">
        {{ title }} の読み込みに失敗しました <br />
        エラーメッセージ: {{ errormsg }}
      </v-alert>
    </v-overlay>
    <v-layout :class="{ loading: !loaded || error }" column>
      <v-data-table
        :headers="chartData.headers"
        :items="displayLists"
        :items-per-page="-1"
        :hide-default-footer="true"
        :height="480"
        :fixed-header="true"
        :mobile-breakpoint="0"
        class="cardTable"
      />
    </v-layout>
    <!-- <div class="note">※退院には、死亡退院を含む</div> -->
    <v-pagination
      v-model="pageNum"
      :length="length"
      :total-visible="7"
      color="#f96b2c"
      @input="pageChange"
    />
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
.loading {
  visibility: hidden;
}
</style>

<script>
import ScaleLoader from 'vue-spinner/src/ScaleLoader.vue'
import DataView from '@/components/DataView.vue'
import DataViewBasicInfoPanel from '@/components/DataViewBasicInfoPanel.vue'

export default {
  components: { DataView, DataViewBasicInfoPanel, ScaleLoader },
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
    },
    linktitle: {
      type: String,
      required: false,
      default: '三重県公式ホームページ'
    },
    loaded: {
      type: Boolean,
      default: false
    },
    error: {
      type: Boolean,
      default: false
    },
    errormsg: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      pageNum: 1,
      length: 5,
      pageSize: 50,
      displayLists: []
    }
  },
  mounted() {
    this.length = Math.ceil(this.chartData.datasets.length / this.pageSize)
    this.displayLists = this.chartData.datasets.slice(
      this.pageSize * (this.pageNum - 1),
      this.pageSize * this.pageNum
    )
  },
  methods: {
    pageChange() {
      this.displayLists = this.chartData.datasets.slice(
        this.pageSize * (this.pageNum - 1),
        this.pageSize * this.pageNum
      )
    }
  }
}
</script>
