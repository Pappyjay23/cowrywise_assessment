<script setup>
import CardBg from '@/assets/images/card-bg.jpeg'
</script>

<template>
  <div class="imageCard" :style="{ backgroundImage: `url(${CardBg})` }">
    <div class="imageOverlay"></div>
    <div class="imageTextContainer">
      <p class="imageTextAuthor">Jordan Okeke</p>
      <p class="imageTextLocation">Pretoria, South Africa</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.imageCard {
  height: 100%;
  width: 100%;
  background-size: cover;
  background-position: center;
  border-radius: 8px;
  padding: 2rem 1.5rem;
  display: flex;
  align-items: flex-end;
  color: #fff;
  position: relative;
  overflow: hidden;
  cursor: pointer;

  .imageOverlay {
    position: absolute;
    top: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.4);
    z-index: 1;
    height: 100%;
    width: 100%;
  }

  .imageTextContainer {
    width: 100%;
    z-index: 2;

    .imageTextAuthor {
      font-size: 1.2rem;
      font-weight: 300;
    }
    .imageTextLocation {
      font-size: 80%;
    }
  }
}
</style>
