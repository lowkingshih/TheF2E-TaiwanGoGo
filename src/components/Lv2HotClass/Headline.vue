<script>
  export default {
    props: {
      title: {
        type: String,
        default: "標題",
      },
    },
    setup(props) {
      return { props };
    },
  };
</script>
<template>
  <h1>
    {{ props.title }}
  </h1>
</template>

<style lang="scss" scoped>
  h1 {
    font-size: 24px;
    font-weight: 300;
    color: #1e1e1e;
    @media (min-width: 1200px) {
      font-size: 36px;
    }
  }
</style>
