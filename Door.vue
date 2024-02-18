<script type='text/javascript'>
export default {
  props: ['imgLeft', 'imgRight', 'imgIn', 'imgBg', 'url'],
  data() {
    return {}
  },
  methods: {
    touchInsideImgBg() {
      this.$router.push({path: this.url})
    }
  },
  mounted() {

  }
}
</script>

<template>
  <div class="door">

    <img class="left" :src="imgLeft" alt="Front Image"/>
    <img class="left" :src="imgIn" alt="Back Image"/>

    <img class="right" :src="imgRight" alt="Front Image"/>
    <img class="right" :src="imgIn" alt="Back Image"/>

    <img class="bgimg" :src=imgBg alt="" @click="touchInsideImgBg"/>

  </div>
</template>

<style scoped lang="scss">
.door {
  width: 300px;
  height: 300px;
  border: 1px solid gray;
  perspective: 500px;
  background-repeat: no-repeat;
  background-size: 100% auto;
  position: relative;

  .bgimg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    cursor: pointer;
  }
}

.door > img {
  box-sizing: border-box;
  border: 1px solid black;
}

.left {
  float: left;
  width: 50%;
  height: 100%;
  position: relative;
}

.right {
  margin-left: 50%;
  width: 50%;
  height: 100%;
  position: relative;
}

.door .left {
  width: 50%;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  transform-origin: left center;
  transition: 1s;
}

.door .right {
  width: 50%;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  transform-origin: right center;
  transition: 1s;
}

.door img:first-child {
  z-index: 2;
  backface-visibility: hidden;
}

.door img:nth-child(3) {
  z-index: 2;
  backface-visibility: hidden;
}

.left::before,
.right::before {
  content: "";
  position: absolute;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  top: 50%;
  transform: translateY(-10px);
  border: 1px solid whitesmoke;
}

.left::before {
  right: 0;
}

.right::before {
  left: 0;
}

.door:hover .left {
  transform: rotateY(-130deg);
}

.door:hover .right {
  transform: rotateY(130deg);
}
</style>
