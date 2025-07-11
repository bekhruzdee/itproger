<template>
  <h3>{{ info }}</h3>
  <p>{{ someInfo }}</p>

  <button type="button" @click="userData()">Send</button>
</template>

<script>
export default {
  data() {
    return {
      info: "Title!",
      someInfo: "Anons of message",
    };
  },
  methods: {
    userData() {
      this.someInfo = 'Some new'
    }
  }
};
</script>

<style scoped>
h3 {
  font-weight: lighter;
}
p {
  color: rgb(204, 28, 28);
}
</style>
