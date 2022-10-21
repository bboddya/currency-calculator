<template>
  <div :class="$style.info">
    <div :class="$style.info__title">{{ info.title }}</div>

    <div :class="$style.info__wrap">
      <ul :class="$style.info__list">
        <li
          v-for="(item, index) in info.list"
          :key="index"
          :class="$style.info__item"
        >
          {{ item }}
        </li>
      </ul>

      <div :class="$style.info__images">
        <div v-for="item in info.images" :key="item" :class="$style.info__img">
          <img :src="require(`@/assets/images/${item}`)" alt="img" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
      default: () => {},
    },
  },
  data: () => ({}),
};
</script>

<style lang="scss" module>
.info {
  width: 100%;
  background: #eef5ff;
  border: 1px solid #dfe1f0;
  box-shadow: 0px 0px 20px rgba(239, 239, 239, 0.5);
  border-radius: 16px;
  padding: 40px 25px;

  @media screen and (max-width: 1599px) {
    padding: 30px 25px;
  }

  @media screen and (max-width: 1279px) {
    padding: 20px 15px;
  }

  &__title {
    font-weight: 500;
    font-size: 18px;
    line-height: 24px;
    display: flex;
    align-items: center;
    text-transform: uppercase;
    color: #0f4471;

    @media screen and (max-width: 1599px) {
      font-size: 15px;
      line-height: 20px;
    }

    @media screen and (max-width: 1279px) {
      font-size: 13px;
      line-height: 18px;
    }
  }

  &__wrap {
    margin-top: 50px;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 20px;

    @media screen and (max-width: 1599px) {
      margin-top: 40px;
    }

    @media screen and (max-width: 1279px) {
      margin-top: 30px;
    }

    @media screen and (max-width: 767px) {
      flex-direction: column;
      gap: 30px;
    }
  }

  &__list {
    padding-left: 17px;
  }

  &__item {
    font-weight: 400;
    font-size: 18px;
    line-height: 20px;
    color: #404456;
    position: relative;

    &:not(:last-child) {
      margin-bottom: 20px;
    }

    &::before {
      content: "";
      position: absolute;
      width: 10px;
      height: 10px;
      border: 2px solid #e02025;
      border-radius: 50%;
      left: -17px;
      top: 50%;
      transform: translateY(-50%);
    }

    @media screen and (max-width: 1599px) {
      font-size: 14px;
      line-height: 18px;

      &:not(:last-child) {
        margin-bottom: 15px;
      }

      &::before {
        width: 8px;
        height: 8px;
      }
    }

    @media screen and (max-width: 1279px) {
      font-size: 13px;
      line-height: 15px;
    }
  }

  &__images {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr;
    gap: 15px;
    height: fit-content;

    @media screen and (max-width: 1279px) {
      grid-template-columns: auto;
      grid-template-rows: auto;
      gap: 5px;
    }

    @media screen and (max-width: 767px) {
      grid-template-columns: 1fr 1fr 1fr 1fr;
      gap: 5px;
    }
  }

  &__img {
    width: 100%;
    max-width: 146px;
    height: 146px;

    img {
      object-fit: cover;
      height: 100%;
    }

    &:nth-child(2) img {
      border-radius: 0 50px 0 0;
    }

    &:nth-child(3) img {
      border-radius: 0 0 0 50px;
    }

    @media screen and (max-width: 1599px) {
      max-width: 116px;
      height: 116px;
    }

    @media screen and (max-width: 1279px) {
      max-width: 86px;
      height: 56px;

      img,
      &:nth-child(3) img,
      &:nth-child(2) img {
        border-radius: 15px 0;
      }

      &:nth-child(1) img {
        border-radius: 0 15px;
      }
    }

    @media screen and (max-width: 767px) {
      max-width: 100%;
      height: 47px;

      &:nth-child(3) img {
        border-radius: 0 15px;
      }
    }
  }
}
</style>
