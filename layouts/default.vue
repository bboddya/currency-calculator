<template>
  <div>
    <header class="header">
      <div class="container">
        <nuxt-link
          v-for="(item, index) in pages"
          :key="index"
          :to="item.link"
          class="header__link text-[12px] text-[#666666]"
          :class="item.checked ? 'text-[#343434]' : ''"
        >
          <span @click="clickLink(index)">{{ item.title }}</span>
        </nuxt-link>
      </div>
    </header>

    <Nuxt />
  </div>
</template>

<script>
export default {
  created() {
    const pages = [
      {
        title: "Калькулятор",
        link: "/",
        checked: false,
      },
      {
        title: "Курс рубля",
        link: "/currency",
        checked: false,
      },
    ];

    pages.forEach((item) => {
      if (item.link === this.$route.path) {
        item.checked = true;
      }
    });

    this.pages = pages;
  },
  data: () => ({
    pages: [],
  }),
  methods: {
    clickLink(index) {
      this.pages.forEach((item, idx) => {
        if (idx === index) {
          item.checked = true;
        } else {
          item.checked = false;
        }
      });
    },
  },
};
</script>

<style lang="scss">
button,
input,
optgroup,
select,
textarea {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html {
  font-size: 12px;
}

body {
  @apply font-roboto text-text-main;
  font-size: 1.4rem;
  overflow-x: hidden;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  -webkit-tap-highlight-color: transparent;
}

.header {
  background: #f8f8f8;
  padding-top: 15px;
  padding-bottom: 15px;

  &__link {
    font-weight: 500;
    line-height: 14px;
    transition: all 0.3s;

    &:not(:last-child) {
      margin-right: 30px;
    }

    &:hover {
      color: #343434;
      transition: all 0.3s;
    }
  }
}
</style>
