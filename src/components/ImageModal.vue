<script setup>
import CardBg from '@/assets/images/card-bg.png'
</script>

<template>
  <div class="imageModal" @click="$emit('close')">
    <div class="modalContainer">
      <div class="modalButtonContainer">
        <p class="modalCloseBtn"><v-icon name="io-close-sharp"></v-icon></p>
      </div>
      <div class="modalCard">
        <div class="modalImageContainer">
          <img :src="CardBg" alt="Modal Card Image" />
        </div>
        <div class="modalTextContainer">
          <p class="modalTextAuthor">Fredrick Apata</p>
          <p class="modalTextLocation">Lagos, Nigeria</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.imageModal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.8);
  z-index: 7;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;

  .modalContainer {
    width: 80%;
    height: 80%;
    margin: auto;

    .modalButtonContainer {
      color: white;
      width: 100%;
      display: flex;
      justify-content: flex-end;
      padding: 1rem;

      .modalCloseBtn{
        cursor: pointer;
      }
    }

    .modalCard {
      width: 90%;
      height: 90%;
      background: red;
      margin: auto;
      border-radius: 8px;
      overflow: hidden;
      display: flex;
      flex-direction: column;

      .modalImageContainer {
        height: 80%;
        width: 100%;

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
        }
      }

      .modalTextContainer {
        height: 20%;
        width: 100%;
        background: white;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 0 2rem;

        .modalTextAuthor {
          font-weight: 600;
          font-size: 1.2rem;
          color: #253858;
          letter-spacing: -0.5px;
        }
        .modalTextLocation {
          font-weight: 600;
          font-size: 90%;
          color: #6d7b91;
          letter-spacing: -0.5px;
        }
      }
    }
  }
}
</style>
