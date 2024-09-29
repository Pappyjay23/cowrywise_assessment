<script setup>
// import ImageModal from '@/components/ImageModal.vue';
import ImageCards from '../components/ImageCards.vue'

const searchLoading = false
const searchResults = false
// <ImageModal />
</script>

<template>
  <main>
    <div class="searchSection">
      <div class="searchForm" v-if="!searchLoading && !searchResults">
        <v-icon class="searchIcon" name="pr-search" />
        <input type="text" placeholder="Search for photo" />
      </div>
      <div class="searchText" v-if="searchLoading">
        <h1>Searching for <span>"Fun"</span></h1>
      </div>
      <div class="searchText" v-if="searchResults">
        <h1>Search Results for <span>"Fun"</span></h1>
      </div>
    </div>
    <ImageCards :searchLoading="searchLoading" />
  </main>
</template>

<style lang="scss">
.searchSection {
  background: #dde2e9;
  height: 30vh;
  display: flex;
  align-items: center;

  .searchForm {
    background: #fff;
    padding: 1rem 2rem;
    border-radius: 8px;
    width: 80%;
    margin: 0 auto;
    display: flex;
    align-items: center;
    gap: 24px;

    .searchIcon {
      color: #2538589b;
      cursor: pointer;
    }

    input {
      border: none;
      outline: none;
      width: 90%;
      color: #253858;
      font-weight: 500;
      &::placeholder {
        color: #253858;
        font-weight: 500;
      }
    }
  }

  .searchText {
    width: 70%;
    margin: 0 auto;
    h1 {
      font-weight: 600;
      color: #253858;
      span {
        font-weight: 600;
        color: #6d7b91;
      }
    }
  }
}
</style>
