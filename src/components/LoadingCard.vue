<script setup></script>

<template>
  <div class="imageCard">
    <div class="imageTextContainer">
      <p class="imageTextAuthor"></p>
      <p class="imageTextLocation"></p>
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
  background: #f5f5f5;
  overflow: hidden;
  cursor: pointer;

  .imageTextContainer {
    width: 100%;
    z-index: 2;
    display: flex;
    flex-direction: column;
    gap: 10px;

    .imageTextAuthor {
      background: #e6e6e6;
      width: 50%;
      height: 15px;
      border-radius: 2px;
      animation: pulse 1.5s infinite;
    }
    .imageTextLocation {
      background: #e6e6e6;
      width: 30%;
      height: 15px;
      border-radius: 2px;
      animation: pulse 1.5s infinite;
    }
  }
}

@keyframes pulse {
  0% {
    opacity: 0.6;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0.6;
  }
}
</style>
