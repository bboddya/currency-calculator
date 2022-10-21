<template>
  <footer :class="$style.footer">
    <div :class="$style.footer__descr">
      <Title tag="2" />

      <div :class="$style.footer__text">
        Наши специалисты с радостью ответят на все ваши вопросы и дадут
        профессиональную консультацию по товарам.
      </div>
    </div>

    <div :class="$style.footer__links">
      <a href="tel:+78008889028" :class="$style.footer__number"
        >8 (800) 888-90-28</a
      >

      <span :class="$style.footer__text_big">или</span>

      <a href="mailto:info@example.ru" :class="$style.footer__mail"
        >info@example.ru</a
      >
    </div>
  </footer>
</template>

<script>
import Title from "../ui/Title.vue";
export default {
  data: () => ({}),
  components: { Title },
};
</script>

<style lang="scss" module>
.footer {
  background: #eef5ff;
  border-radius: 16px;
  padding: 65px 130px 54px 50px;
  margin-top: 40px;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 140px;

  @media screen and (max-width: 1599px) {
    padding: 40px 100px 34px 33px;
    margin-top: 24px;
    margin-bottom: 90px;
  }

  @media screen and (max-width: 1279px) {
    padding: 30px 68px 18px 20px;
    margin-top: 20px;
  }

  @media screen and (max-width: 767px) {
    margin-bottom: 70px;
    padding: 20px 15px;
    flex-direction: column;
    gap: 20px;
    align-items: center;
  }

  &__descr {
    width: 100%;
    max-width: 775px;

    @media screen and (max-width: 1599px) {
      max-width: 607px;
    }

    @media screen and (max-width: 1279px) {
      max-width: 352px;
    }

    @media screen and (max-width: 767px) {
      text-align: center;
    }
  }

  &__text {
    margin-top: 15px;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    color: #404456;

    @media screen and (max-width: 1599px) {
      font-size: 13px;
      line-height: 18px;
    }

    @media screen and (max-width: 1279px) {
      font-size: 10px;
      line-height: 12px;
    }
  }

  &__text_big {
    margin: 20px 0;
    font-weight: 400;
    font-size: 24px;
    line-height: 28px;
    text-transform: uppercase;

    @media screen and (max-width: 1599px) {
      font-size: 18px;
      line-height: 21px;
    }

    @media screen and (max-width: 1279px) {
      font-size: 12px;
      line-height: 14px;
      margin: 10px 0;
    }
  }

  &__links {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    @media screen and (max-width: 1599px) {
      font-size: 24px;
      line-height: 28px;
    }
  }

  &__number {
    font-weight: 500;
    font-size: 50px;
    line-height: 46px;
    color: #093078;

    @media screen and (max-width: 1599px) {
      font-size: 40px;
    }

    @media screen and (max-width: 1279px) {
      font-size: 24px;
      line-height: 28px;
    }
  }

  &__mail {
    font-weight: 400;
    font-size: 34px;
    line-height: 40px;
    text-align: right;
    letter-spacing: 1px;
    color: #093078;

    @media screen and (max-width: 1599px) {
      font-size: 24px;
      line-height: 28px;
    }

    @media screen and (max-width: 1279px) {
      font-size: 20px;
      line-height: 23px;
    }
  }
}
</style>
