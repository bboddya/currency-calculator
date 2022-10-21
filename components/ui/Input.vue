<template>
  <div :class="$style.input__wrap">
    <div :class="$style.input__title">{{ title }}</div>

    <input
      :type="type"
      v-model="inputValue"
      :class="$style.input"
      :placeholder="placeholder"
    />
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: "",
    },
    type: {
      type: String,
      default: "",
    },
    valueInput: {
      type: String,
      default: "",
    },
    inputName: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
  },
  data: () => ({
    inputValue: "",
  }),
  watch: {
    inputValue() {
      let obj = {
        name: this.inputName,
        value: this.inputValue,
      };

      this.$emit("updateForm", obj);
    },
  },
};
</script>

<style lang="scss" module>
.input {
  font-weight: 400;
  font-size: 14px;
  line-height: 28px;
  color: #a0a3bd;
  background: #ffffff;
  border: 1px solid #dfdfdf;
  border-radius: 5px;
  padding: 10px 20px;
  display: block;
  width: 100%;
  margin-bottom: 30px;
  outline: none;

  &::-webkit-outer-spin-button,
  &::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  @media screen and (max-width: 1599px) {
    font-size: 12px;
  }

  @media screen and (max-width: 1279px) {
    padding: 8px 20px;
  }

  @media screen and (max-width: 767px) {
    margin-bottom: 20px;
  }

  &__title {
    font-weight: 500;
    font-size: 16px;
    line-height: 19px;
    color: #2c3a4b;
    margin-bottom: 10px;

    @media screen and (max-width: 1599px) {
      font-size: 14px;
      line-height: 16px;
    }
  }
}
</style>
