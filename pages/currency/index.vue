<template>
  <div :class="$style.currency">
    <div class="container">
      <Title tag="1" title="Курс рубля" />

      <Loader v-if="!currency.length" />

      <div v-else :class="$style.currency__wrap">
        <CurrencyCard
          v-for="(cur, index) in currency"
          :key="cur.ID"
          :index="index"
          :char-code="cur.CharCode"
          :title="cur.Name"
          :nominal="cur.Nominal"
          :value="cur.Value"
        />
      </div>

      <TotalBlock :icon-obj="iconObj" />
    </div>
  </div>
</template>

<script>
import CurrencyCard from "@/components/blocks/CurrencyCard.vue";
import Title from "@/components/ui/Title.vue";
import Loader from "@/components/ui/Loader.vue";
import TotalBlock from "@/components/blocks/TotalBlock.vue";

export default {
  components: { CurrencyCard, Title, Loader, TotalBlock },
  async asyncData({ $axios }) {
    const { data } = await $axios.get("/api");

    const currency = [];

    for (var key in data.Valute) {
      currency.push(data.Valute[key]);
    }

    return { currency };
  },
  data() {
    return {
      currency: [],
      iconObj: {
        name: "info",
        color: "blue",
      },
    };
  },
  computed: {},
};
</script>

<style lang="scss" module>
.currency {
  padding-bottom: 90px;

  @media screen and (max-width: 1279px) {
    padding-bottom: 45px;
  }

  &__wrap {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 30px;
    margin-bottom: 30px;

    @media screen and (max-width: 1279px) {
      gap: 20px;
      grid-template-columns: 1fr 1fr;
    }

    @media screen and (max-width: 767px) {
      grid-template-columns: 1fr;
    }
  }
}
</style>
