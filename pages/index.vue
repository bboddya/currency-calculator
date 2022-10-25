<template>
  <div :class="$style.main">
    <div class="container">
      <Title tag="1" title="Валютный калькулятор" />

      <div :class="$style.main__wrap">
        <div :class="$style.main__data">
          <Input
            v-for="item in inputs"
            :key="item.id"
            :title="item.title"
            :placeholder="item.placeholder"
            :input-name="item.name"
            :value="item.value"
            :type="item.type"
            @updateForm="updateForm"
          />

          <TotalBlock :icon-obj="iconObj" :totalCount="totalCount" />
        </div>

        <InfoBlock :info="info" />
      </div>

      <Footer />
    </div>
  </div>
</template>

<script>
import Title from "@/components/ui/Title.vue";
import Input from "@/components/ui/Input.vue";
import InfoBlock from "@/components/blocks/InfoBlock.vue";
import CustomIcon from "@/components/ui/CustomIcon.vue";
import Footer from "@/components/blocks/Footer.vue";
import TotalBlock from "@/components/blocks/TotalBlock.vue";

export default {
  components: {
    Title,
    Input,
    InfoBlock,
    CustomIcon,
    Footer,
    TotalBlock,
  },
  data() {
    return {
      inputs: [
        {
          title: "Валюта 1",
          placeholder: "Введите название или код",
          value: "",
          name: "first",
          id: 1,
          type: "text",
        },
        {
          title: "Валюта 2",
          placeholder: "Введите название или код",
          value: "",
          name: "second",
          id: 2,
          type: "text",
        },
        {
          title: "Количество",
          placeholder: "Введите число",
          value: "",
          name: "amount",
          id: 3,
          type: "number",
        },
      ],
      info: {
        title:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor:",
        list: [
          "incididunt ut labore et dolore magna aliqua",
          "incididunt ut labore et",
          "incididunt ut labore et dolore",
          "labore et dolore",
          "incididunt ut",
          "incididunt ut labore et dolore",
          "incididunt ut labore",
        ],
        images: ["img-1.jpg", "img-2.jpg", "img-3.jpg", "img-4.png"],
      },
      iconObj: {
        name: "info",
        color: "red",
      },
      form: {
        first: "",
        second: "",
        amount: "",
      },
      totalCount: "",
      _timerId: null,
    };
  },
  methods: {
    updateForm({ name, value }) {
      this.form[name] = value;

      clearTimeout(this._timerId);
      this._timerId = setTimeout(async () => {
        let first = this.form.first.toLowerCase().trim();
        let second = this.form.second.toLowerCase().trim();
        let amount = +this.form.amount.toLowerCase().trim();

        if (first !== "" && second !== "" && amount !== 0) {
          const { data } = await this.$axios.get("/api");

          let newFirst = 0;
          let newSecond = 0;

          for (var key in data.Valute) {
            let code = data.Valute[key].CharCode.toLowerCase();
            let name = data.Valute[key].Name.toLowerCase();

            if (code === first || name === first) {
              if (data.Valute[key].Nominal > 0) {
                newFirst = data.Valute[key].Value / data.Valute[key].Nominal;
              } else {
                newFirst = data.Valute[key].Value;
              }
            }

            if (code === second || name === second) {
              if (data.Valute[key].Nominal > 0) {
                newSecond = data.Valute[key].Value / data.Valute[key].Nominal;
              } else {
                newSecond = data.Valute[key].Value;
              }
            }
          }

          if (!newFirst || !newSecond) {
            return (this.totalCount = "Некорректная валюта");
          }

          if (newFirst === newSecond) {
            this.totalCount = amount;
          } else {
            let sum = amount * newFirst;
            this.totalCount = Math.ceil(sum / newSecond);
          }
        }
      }, 1000);
    },
  },
};
</script>

<style lang="scss" module>
.main {
  &__wrap {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 35px;

    @media screen and (max-width: 767px) {
      flex-direction: column;
      gap: 20px;
    }
  }

  &__data {
    width: 100%;
    max-width: 699px;

    @media screen and (max-width: 767px) {
      max-width: 100%;
    }
  }
}
</style>
