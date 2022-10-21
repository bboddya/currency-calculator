<template>
  <div
    :class="$style.total"
    :style="
      iconObj.color === 'red' ? 'background: #eef5ff;' : 'background: #F8F8F8;'
    "
  >
    <CustomIcon :name="iconObj.name" :color="iconObj.color" />

    <div v-if="iconObj.color === 'red'" :class="$style.total__sum">
      <span>Итого:</span>
      <span>{{ totalCount }}</span>
    </div>

    <div v-else :class="$style.total__text">
      <div>Телефон: <a href="tel:+78008889028">8 (800) 888-90-28</a>,</div>
      <div>email: <a href="mailto:info@example.ru">info@example.ru.</a></div>
    </div>
  </div>
</template>

<script>
import CustomIcon from "@/components/ui/CustomIcon.vue";

export default {
  components: {
    CustomIcon,
  },
  props: {
    iconObj: {
      type: Object,
      default: () => {},
    },
    totalCount: {
      default: "...",
    },
  },
  data: () => ({}),
};
</script>

<style lang="scss" module>
.total {
  display: flex;
  align-items: center;
  border-radius: 16px;
  padding: 37px 30px;

  @media screen and (max-width: 1599px) {
    padding: 30px;
  }

  @media screen and (max-width: 1279px) {
    padding: 34px 27px;
  }

  @media screen and (max-width: 767px) {
    padding: 20px 26px;
    flex-wrap: wrap;
  }

  &__sum {
    margin-left: 30px;
    font-weight: 700;
    font-size: 24px;
    line-height: 140%;
    color: #0f4471;

    @media screen and (max-width: 1599px) {
      font-size: 20px;
    }

    @media screen and (max-width: 1279px) {
      font-size: 16px;
      margin-left: 20px;
    }
  }

  &__text {
    font-weight: 700;
    font-size: 20px;
    line-height: 140%;
    color: #0f4471;
    margin-left: 30px;
    display: flex;
    justify-content: flex-start;
    align-items: center;

    @media screen and (max-width: 1279px) {
      font-size: 18px;
    }

    @media screen and (max-width: 767px) {
      flex-direction: column;
      align-items: flex-start;
      width: 100%;
      margin-left: 0;
      margin-top: 20px;
    }
  }
}
</style>
