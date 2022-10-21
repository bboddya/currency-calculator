<template>
  <div :class="$style.card">
    <CustomIcon :color="getColor" />

    <div :class="$style.card__code">
      {{ charCode }}
    </div>

    <div :class="$style.card__title">
      {{ title }}
    </div>

    <div :class="$style.card__value">
      {{ nominal }}
    </div>

    <div :class="$style.card__value">
      {{ value }}
    </div>
  </div>
</template>

<script>
import CustomIcon from "../ui/CustomIcon.vue";
export default {
  components: { CustomIcon },
  props: {
    title: {
      type: String,
      default: "",
    },
    value: {
      type: Number,
      default: 0,
    },
    index: {
      type: Number,
      default: 0,
    },
    charCode: {
      type: String,
      default: "",
    },
    nominal: {
      type: Number,
      default: 0,
    },
  },
  data: () => ({
    inputValue: "",
  }),

  computed: {
    getColor() {
      const res = this.index % 2;
      if (res) {
        return "red";
      }

      return "blue";
    },
  },
};
</script>

<style lang="scss" module>
.card {
  background: #f8f8f8;
  border-radius: 16px;
  padding: 38px 30px;
  cursor: pointer;
  transition: all 0.3s;

  @media screen and (max-width: 1599px) {
    padding-left: 25px;
    padding-right: 25px;
  }

  @media screen and (max-width: 767px) {
    padding: 25px;
  }

  @media screen and (min-width: 1280px) {
    &:hover {
      filter: drop-shadow(0px 2px 10px rgba(0, 0, 0, 0.15));
      transition: all 0.3s;
    }
  }

  &__code {
    font-weight: 700;
    font-size: 20px;
    line-height: 140%;
    color: #0f4471;
    margin-top: 30px;

    @media screen and (min-width: 1280px) {
      font-size: 18px;
    }

    @media screen and (max-width: 767px) {
      font-size: 17px;
      margin-top: 20px;
    }
  }

  &__title {
    font-weight: 400;
    font-size: 16px;
    line-height: 140%;
    color: #111111;
    margin-top: 20px;
    margin-bottom: 30px;

    @media screen and (max-width: 1599px) {
      font-size: 15px;
    }

    @media screen and (min-width: 1280px) {
      font-size: 14px;
    }

    @media screen and (max-width: 767px) {
      margin-top: 20px;
      margin-bottom: 20px;
    }
  }

  &__value {
    font-weight: 500;
    font-size: 16px;
    line-height: 20px;
    color: #1c1c1c;
    position: relative;
    margin-left: 20px;

    &:not(:last-child) {
      margin-bottom: 15px;
    }

    &::before {
      content: "";
      position: absolute;
      width: 10px;
      height: 10px;
      border: 2px solid #e02025;
      border-radius: 50%;
      left: -20px;
      top: 50%;
      transform: translateY(-50%);
    }

    @media screen and (max-width: 1599px) {
      font-size: 15px;

      &::before {
        width: 8px;
        height: 8px;
      }
    }

    @media screen and (max-width: 767px) {
      &:not(:last-child) {
        margin-bottom: 10px;
      }
    }
  }
}
</style>
