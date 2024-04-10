<template>
  <div>
    <h1>{{ advice }}</h1>
    <button @click="getAdvice">Get advice</button>
    <p>
      You have read <strong>{{ count }}</strong> pieces of advice
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      advice: "",
      count: 0,
    };
  },
  methods: {
    getAdvice() {
      fetch("https://api.adviceslip.com/advice")
        .then((response) => {
          if (!response.ok) {
            throw new Error("Network response was not ok");
          }
          return response.json();
        })
        .then((data) => {
          this.advice = data.slip.advice;
          this.count += 1;
        })
        .catch((error) => {
          console.error("There was an error fetching the advice:", error);
        });
    },
  },
  mounted() {
    this.getAdvice();
  },
};
</script>
