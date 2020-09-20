<template>
  <div class="MainPage">
    <page-header
      :icon="headerItem.icon"
      :title="headerItem.title"
      :date="headerItem.date"
    />
    <whats-new
      class="mb-4"
      :items="newsItems"
      :errormsg="newsErrorMsg"
      :error="newsError"
      :loaded="newsLoaded"
    />
    <v-row class="DataBlock">
      <!--<v-col cols="12" md="6" class="DataCard">
        <svg-card
          title="検査陽性者の状況"
          :title-id="'details-of-confirmed-cases'"
          :date="Data.inspections_summary.date"
        >
          <confirmed-cases-table v-bind="confirmedCases" />
        </svg-card>
      </v-col>-->

      <v-col cols="12" md="6" class="DataCard">
        <time-bar-chart
          title="陽性患者が確認された件数"
          :title-id="'number-of-confirmed-cases'"
          :chart-id="'time-bar-chart-patients'"
          :chart-data="patientsGraph"
          :date="date.patientsGraph"
          :unit="'件'"
          :url="'https://www.pref.mie.lg.jp/YAKUMUS/HP/m0068000066_00002.htm'"
          :linktitle="'三重県公式ホームページ'"
          :errormsg="dataErrorMsg"
          :error="dataError"
          :loaded="dataLoaded"
        />
      </v-col>
      <v-col cols="12" md="6" class="DataCard">
        <time-bar-chart
          title="検査実施数"
          :title-id="'number-of-tested-cases'"
          :chart-id="'time-bar-chart-tested'"
          :chart-data="inspectionsGraph"
          :date="date.inspectionsGraph"
          :unit="'件'"
          :url="'https://www.pref.mie.lg.jp/IT/HP/87587000001_00002.htm'"
          :linktitle="'三重県オープンデータライブラリ'"
          :errormsg="dataErrorMsg"
          :error="dataError"
          :loaded="dataLoaded"
        />
      </v-col>
      <!--<v-col cols="12" md="6" class="DataCard">
        <time-bar-chart
          title="日別の陽性患者数"
          :title-id="'nownumber-of-confirmed-cases'"
          :chart-id="'time-bar-chart-nowpatients'"
          :chart-data="nowpatientsGraph"
          :date="Data.nowinfectedperson.date"
          :unit="'人'"
          :show="false"
        />
      </v-col>-->
      <v-col cols="12" md="6" class="DataCard">
        <data-table
          title="陽性患者の属性"
          :title-id="'attributes-of-confirmed-cases'"
          :chart-data="patientsTable"
          :chart-option="{}"
          :date="date.patientsTable"
          :info="sumInfoOfPatients"
          :url="'https://www.pref.mie.lg.jp/IT/HP/87587000001_00002.htm'"
          :linktitle="'三重県オープンデータライブラリ'"
          :errormsg="dataErrorMsg"
          :error="dataError"
          :loaded="dataLoaded"
        />
      </v-col>
      <!--
      <v-col cols="12" md="6" class="DataCard">
        <time-bar-chart
          title="新型コロナコールセンター相談件数"
          :title-id="'number-of-reports-to-covid19-telephone-advisory-center'"
          :chart-id="'time-bar-chart-contacts'"
          :chart-data="contactsGraph"
          :date="Data.contacts.date"
          :unit="'件'"
          :url="''"
        />
      </v-col>
      <v-col cols="12" md="6" class="DataCard">
        <time-bar-chart
          title="新型コロナ受診相談窓口相談件数"
          :title-id="'number-of-reports-to-covid19-consultation-desk'"
          :chart-id="'time-bar-chart-querents'"
          :chart-data="querentsGraph"
          :date="Data.querents.date"
          :unit="'件'"
          :url="''"
        />
      </v-col>
      <v-col cols="12" md="6" class="DataCard">
        <metro-bar-chart
          title="都営地下鉄の利用者数の推移"
          :title-id="'predicted-number-of-toei-subway-passengers'"
          :chart-id="'metro-bar-chart'"
          :chart-data="metroGraph"
          :chart-option="metroGraphOption"
          :date="metroGraph.date"
        />
      </v-col>
      -->
    </v-row>
  </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue'
import TimeBarChart from '@/components/TimeBarChart.vue'
// import MetroBarChart from '@/components/MetroBarChart.vue'
// import TimeStackedBarChart from '@/components/TimeStackedBarChart.vue'
import WhatsNew from '@/components/WhatsNew.vue'
// import StaticInfo from '@/components/StaticInfo.vue'
// import Data from '@/data/data.json'
// import MetroData from '@/data/metro.json'
import DataTable from '@/components/DataTable.vue'
import formatGraph from '@/utils/formatGraph'
import formatTable from '@/utils/formatTable'
// import formatConfirmedCases from '@/utils/formatConfirmedCases'
// import News from '@/data/news.json'
// import SvgCard from '@/components/SvgCard.vue'
// import ConfirmedCasesTable from '@/components/ConfirmedCasesTable.vue'

export default {
  components: {
    PageHeader,
    TimeBarChart,
    // MetroBarChart,
    WhatsNew,
    // StaticInfo,
    DataTable
    // SvgCard,
    // ConfirmedCasesTable
  },
  data() {
    // 感染者数グラフ
    // const nowpatientsGraph = formatGraph(Data.nowinfectedperson.data)
    // const patientsGraph = formatGraph(Data.patients_summary.data)
    // 感染者数
    // const patientsTable = formatTable(Data.patients.data)
    // 退院者グラフ
    // const dischargesGraph = formatGraph(Data.discharges_summary.data)

    // 相談件数
    // const contactsGraph = formatGraph(Data.contacts.data)
    // 帰国者・接触者電話相談センター相談件数
    // const querentsGraph = formatGraph(Data.querents.data)
    // 都営地下鉄の利用者数の推移
    // const metroGraph = MetroData
    // 検査実施日別状況
    /* const inspectionsGraph = [
      Data.inspections_summary.data['県内'],
      Data.inspections_summary.data['その他']
    ]
    */

    // const inspectionsGraph = formatGraph(Data.inspections_summary.data)

    /* const inspectionsItems = [
      '県内発生（疑い例・接触者調査）',
      'その他（チャーター便・クルーズ便）'
    ]
    */
    // const inspectionsLabels = Data.inspections_summary.labels
    // 死亡者数
    // #MEMO: 今後使う可能性あるので一時コメントアウト
    // const fatalitiesTable = formatTable(
    //   Data.patients.data.filter(patient => patient['備考'] === '死亡')
    // )
    // 検査陽性者の状況
    // const confirmedCases = formatConfirmedCases(Data.main_summary)
    /*
    const sumInfoOfPatients = {
      lText: patientsGraph[
        patientsGraph.length - 1
      ].cumulative.toLocaleString(),
      sText: patientsGraph[patientsGraph.length - 1].label + 'までの累計',
      unit: '人'
    }
    */

    const data = {
      dataLoaded: false,
      newsLoaded: false,
      dataErrorMsg: '',
      newsErrorMsg: '',
      dataError: false,
      newsError: false,

      patientsTable: {},
      patientsGraph: [],
      // 追加、現在の陽性患者数のグラフに必要なやつ
      // nowpatientsGraph: {},
      // dischargesGraph,
      // contactsGraph,
      // querentsGraph,
      // metroGraph,
      inspectionsGraph: [],
      // inspectionsItems,
      // inspectionsLabels,
      // confirmedCases,
      sumInfoOfPatients: {
        lText: '',
        sText: '',
        unit: '人'
      },
      date: {
        patientsTable: '',
        patientsGraph: '',
        inspectionsGraph: ''
      },
      headerItem: {
        icon: 'mdi-chart-timeline-variant',
        title: '三重県内の最新感染動向',
        date: ''
      },
      newsItems: []
      /* metroGraphOption: {
        responsive: true,
        legend: {
          display: true
        },
        scales: {
          xAxes: [
            {
              position: 'bottom',
              stacked: false,
              gridLines: {
                display: true
              },
              ticks: {
                fontSize: 10,
                maxTicksLimit: 20,
                fontColor: '#808080'
              }
            }
          ],
          yAxes: [
            {
              stacked: false,
              gridLines: {
                display: true
              },
              ticks: {
                fontSize: 12,
                maxTicksLimit: 10,
                fontColor: '#808080',
                callback(value) {
                  return value.toFixed(2) + '%'
                }
              }
            }
          ]
        }, */
      /* tooltips: {
          displayColors: false,
          callbacks: {
            title(tooltipItems, _) {
              const label = tooltipItems[0].label
              return `期間: ${label}`
            },
            label(tooltipItem, data) {
              const currentData = data.datasets[tooltipItem.datasetIndex]
              const percentage = `${currentData.data[tooltipItem.index]}%`

              return `${metroGraph.base_period}の利用者数との相対値: ${percentage}`
            }
          }
        } */
      //  }
    }
    return data
  },
  created() {
    this.getFromAPI()
  },
  methods: {
    getFromAPI() {
      Promise.all([this.getDataFromAPI(), this.getNewsFromAPI()])
    },
    getDataFromAPI() {
      fetch(
        `https://raw.githubusercontent.com/sakurum/covid19-mie-getdata/gh-pages/data.json`
      )
        .then(response => response.json())
        .then(responseJson => {
          // 感染者数グラフ
          // this.nowpatientsGraph = formatGraph(Data.nowinfectedperson.data)
          this.patientsGraph = formatGraph(responseJson.patients_summary.data)
          this.inspectionsGraph = formatGraph(
            responseJson.inspections_summary.data
          )
          // 感染者数
          this.patientsTable = formatTable(responseJson.patients.data)
          this.date = {
            patientsTable: responseJson.patients.date,
            patientsGraph: responseJson.patients_summary.date,
            inspectionsGraph: responseJson.inspections_summary.date
          }
          this.headerItem.date = responseJson.lastUpdate
          this.sumInfoOfPatients = {
            lText: this.patientsGraph[
              this.patientsGraph.length - 1
            ].cumulative.toLocaleString(),
            sText:
              this.patientsGraph[this.patientsGraph.length - 1].label +
              'までの累計',
            unit: '人'
          }
          this.dataLoaded = true
        })
        .catch(error => {
          this.dataError = true
          this.dataErrorMsg = error.toString()
        })
    },
    getNewsFromAPI() {
      fetch(
        `https://raw.githubusercontent.com/sakurum/covid19-mie-getdata/gh-pages/news.json`
      )
        .then(response => response.json())
        .then(responseJson => {
          this.newsItems = responseJson.newsItems
          this.newsLoaded = true
        })
        .catch(error => {
          this.newsError = true
          this.newsErrorMsg = error.toString()
        })
    }
  },
  head() {
    return {
      title: '三重県内の最新感染動向'
    }
  }
}
</script>

<style lang="scss" scoped>
.MainPage {
  .DataBlock {
    margin: 20px -8px;
    .DataCard {
      @include largerThan($medium) {
        padding: 10px;
      }
      @include lessThan($small) {
        padding: 4px 8px;
      }
    }
  }
}
</style>
