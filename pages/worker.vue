<template>
  <div class="Worker">
    <h2 class="Worker-Heading">
      {{ $t('企業の皆様・はたらく皆様へ') }}
    </h2>
    <div v-for="(item, i) in items" :key="i">
      <TextCard :title="item.title" :link="item.link" :body="item.body" />
    </div>
  </div>
</template>
<script lang="ts">
import TextCard from '@/components/TextCard.vue'
import { MetaInfo } from 'vue-meta'
export default {
  components: {
    TextCard
  },
  data() {
    return {
      items: [
        {
          title: this.$t('中小企業・サービス産業振興課「中小企業・小規模企業の皆様へ（新型コロナウイルス感染症関連）」'),
          link:
            'https://www.pref.mie.lg.jp/SHINSAN/HP/p0016400019.htm',
          body:
            this.$t(
              '県では、新型コロナウイルス感染症の流行により影響を受ける、又はその恐れがある中小企業・小規模企業の皆様に対する相談窓口の設置等を行っています。'
            )
        },
        {
          title: this.$t('新型コロナウイルスに関するQ&A（労働者の方向け）'),
          link:
            'https://www.mhlw.go.jp/stf/seisakunitsuite/bunya/kenkou_iryou/dengue_fever_qa_00018.html',
          body:
            this.$t(
              '厚生労働省が公開している、労働者向けの新型コロナウイルスに関するQ&Aがまとめられたページです。'
            )
        }
      ]
    }
  },
  head() : MetaInfo {
    return {
      title: this.$t('企業の皆様・はたらく皆様へ') as string
    }
  }
}
</script>
<style lang="scss">
.Worker {
  &-Heading {
    @include font-size(30);
    font-weight: normal;
    color: $gray-2;
    margin-bottom: 12px;
  }
}
a {
  @include text-link();
}
</style>
