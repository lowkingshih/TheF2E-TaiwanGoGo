<script>
  import { ref } from "vue";
  export default {
    props: {
      hotClass: {
        type: Array,
        default: () => [
          {
            className: "",
            imgUrl: "",
          },
        ],
      },
      HandHotClassSearch: {
        type: Function,
        default: () => {},
      },
    },
    setup(props) {
      const img = ref(null);
      return { props, img };
    },
  };
</script>
<template>
  <div class="cards">
    <!-- 透過v-for渲染卡片 -->
    <div class="card" v-for="item in props.hotClass" :key="item.imgUrl">
      <a
        class="imgWrap"
        :data-class="item.className"
        @click.prevent="HandHotClassSearch(item.className)"
      >
        <img :src="item.imgUrl" :alt="item.className" />
      </a>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  a {
    cursor: pointer;
  }
  .cards {
    display: flex;
    flex-flow: wrap;
    .card {
      width: 48%;
      margin-bottom: 10px;
      @media (min-width: 1200px) {
        width: 23%;
        margin-bottom: 12px;
      }
    }
    .card:nth-child(2n) {
      margin-left: 2%;
      @media (min-width: 1200px) {
        margin-left: unset;
      }
    }
    .card:not(:nth-child(4n + 1)) {
      @media (min-width: 1200px) {
        margin-left: 2.5%;
      }
    }
    .imgWrap {
      display: block;
      border-radius: 24px;
      overflow: hidden;
      position: relative;
      &:hover img {
        transform: scale(1.1);
      }
      &::before {
        content: attr(data-class);
        color: white;
        white-space: nowrap;
        position: absolute;
        z-index: 200;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        @media (min-width: 1200px) {
          font-size: 24px;
        }
      }
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: all 0.4s;
      }
    }
  }
</style>
