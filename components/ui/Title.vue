<template>
  <h1 v-if="tag === '1'" :class="$style.title">{{ title }}</h1>
  <h2 v-else :class="$style.title_second">
    Нужна помощь? <br />
    Мы поможем! Просто свяжитесь с нами.
  </h2>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: "",
    },
    tag: {
      type: String,
      default: "",
    },
  },
  data: () => ({}),
};
</script>

<style lang="scss" module>
.title {
  font-weight: 500;
  font-size: 34px;
  line-height: 40px;
  color: #0f4471;
  margin-bottom: 40px;
  margin-top: 30px;

  @media screen and (max-width: 1599px) {
    font-size: 26px;
    line-height: 30px;
    margin-bottom: 30px;
  }

  @media screen and (max-width: 1279px) {
    margin-bottom: 20px;
    margin-top: 20px;
  }

  @media screen and (max-width: 767px) {
    font-weight: 700;
    font-size: 20px;
    line-height: 140%;
  }

  &_second {
    font-size: 36px;
    line-height: 46px;
    color: #093078;

    @media screen and (max-width: 1599px) {
      font-size: 29px;
      line-height: 36px;
    }

    @media screen and (max-width: 1279px) {
      font-size: 18px;
      line-height: 24px;
    }

    @media screen and (max-width: 767px) {
      font-weight: 700;
      font-size: 16px;
    }
  }
}
</style>
