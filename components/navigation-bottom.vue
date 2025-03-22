<template>
  <div class="navigation-bottom">
    <div
      v-for="(item, index) in navigation"
      :key="index"
      :class="{ 'opacity-30': isActive(item.path) }"
      @click="$router.push(item.path)"
    >
      <img :src="getImagePath(item.icon)" :alt="item.title" />
      <span>{{ item.title }}</span>
    </div>
  </div>
</template>

<script >
export default {
  data() {
    return {
      navigation: [
        { icon: 'main', title: 'Main', path: '/' },
        { icon: 'basket', title: 'Payments', path: '' },
        { icon: 'escrow', title: 'Escrow', path: '' },
        { icon: 'list', title: 'WhiteList', path: '' },
        { icon: 'shops', title: 'Shops', path: '' },
        { icon: 'more', title: 'More', path: '' },
      ],
    }
  },
  methods: {
    getImagePath(icon) {
      return require(`@/assets/svg/${icon}.svg`)
    },
    isActive(path) {
      return !(this.$route.path === path)
    },
  },
}
</script>

<style scoped lang="scss">
.navigation-bottom {
  width: 100%;
  height: 70px;
  background: #111016;
  border-top: 1px solid #21212d;
  position: fixed;
  bottom: 0;
  left: 0;
  display: grid;
  grid-template-columns: repeat(6, minmax(0, 1fr));
  color: white;
  font-family: 'Reza Zulmi Alfaizi Sans';
  font-size: 10px;
  div {
    display: flex;
    flex-direction: column;
    gap: 6px;
    justify-content: center;
    align-items: center;

    &:hover {
      cursor: pointer;
    }
    img {
      height: 29px;
      width: auto;
      object-fit: contain;
    }
  }
}
.opacity-30 {
  opacity: 0.3;
}
</style>
