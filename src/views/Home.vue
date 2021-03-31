<template>
  <div
    :class="isCard ? '' : 'lg:h-screen'"
    class="container mx-auto p-2 grid grid-cols-1 row-gap-12 lg:grid-cols-10 lg:col-gap-10 lg:pt-12"
  >
    <Summary :items="items"></Summary>
  </div>
</template>

<script>
import Summary from "../components/Summary";

export default {
  name: "CheckoutPage",
  components: {
    Summary
  },
  data() {
    return {
      items: [
        {
          title: "Title 1",
          description: "lorem impsu liwe",
          price: 550
        },
        {
          title: "Title 2",
          description: "lorem impsu liwe",
          price: 250
        },
        {
          title: "Title 3",
          description: "lorem impsu liwe",
          price: 150
        }
      ],
      alertVisible: true,
      total: 0,
      isCard: false
    };
  },
  mounted() {
    this.getTotal(this.items);
  },
  methods: {
    getTotal(items) {
      items.forEach(item => {
        this.total += item.price;
      });
    },
    handleAlert() {
      this.alertVisible = true;
      setTimeout(() => {
        this.alertVisible = false;
      }, 4000);
    },
    handleCard() {
      this.isCard = true;
    }
  }
};
</script>
