<template>
  <div class="Worker">
    <h2 class="Worker-Heading">
      企業の皆様・はたらく皆様へ
    </h2>
    <div v-for="(item, i) in items" :key="i">
      <TextCard :title="item.title" :link="item.link" :body="item.body" />
    </div>
  </div>
</template>
<script lang="ts">
import TextCard from '@/components/TextCard.vue'
export default {
  components: {
    TextCard
  },
  data() {
    return {
      items: [
        {
          title: '中小企業・サービス産業振興課「中小企業・小規模企業の皆様へ（新型コロナウイルス感染症関連）」',
          link:
            'https://www.pref.mie.lg.jp/SHINSAN/HP/p0016400019.htm',
          body:
            '県では、新型コロナウイルス感染症の流行により影響を受ける、又はその恐れがある中小企業・小規模企業の皆様に対する相談窓口の設置等を行っています。'
        }
      ]
    }
  },
  head() {
    return {
      title: '企業の皆様・はたらく皆様へ'
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
