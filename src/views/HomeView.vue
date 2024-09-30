<script setup>
import ImageModal from '@/components/ImageModal.vue'
import { onMounted, ref } from 'vue'
import ImageCards from '../components/ImageCards.vue'

const isLoading = ref(false)
const searchLoading = ref(false)
const searchResults = ref(false)
const showModal = ref(false)
const imageData = ref([])
const searchQuery = ref('')

const accessKey = import.meta.env.VITE_UNSPLASH_ACCESS_KEY

const fetchPhotos = async () => {
  isLoading.value = true
  const apiUrl = `https://api.unsplash.com/photos?per_page=8`
  try {
    const response = await fetch(apiUrl, {
      headers: {
        Authorization: `Client-ID ${accessKey}`
      }
    })

    if (!response.ok) {
      throw new Error('Failed to fetch photos')
    }

    const photos = await response.json()
    imageData.value = photos
    setTimeout(() => {
      isLoading.value = false
    }, 700)
  } catch (error) {
    console.error('Error fetching photos:', error)
    isLoading.value = false
  }
}

const fetchSearchPhotos = async (query) => {
  const apiUrl = `https://api.unsplash.com/search/photos?query=${query}&per_page=8`
  searchLoading.value = true
  try {
    const response = await fetch(apiUrl, {
      headers: {
        Authorization: `Client-ID ${accessKey}`
      }
    })

    if (!response.ok) {
      throw new Error('Failed to fetch search results')
    }

    const data = await response.json()
    imageData.value = data.results
    searchLoading.value = false
    searchResults.value = true
  } catch (error) {
    console.error('Error fetching search results:', error)
    searchLoading.value = false
  }
}

const handleSearch = () => {
  searchLoading.value = true
  fetchSearchPhotos(searchQuery.value).then(() => {
    searchLoading.value = false
    searchResults.value = true
  })
}

const handleKeyPress = (event) => {
  if (event.key === 'Enter') {
    event.preventDefault()
    handleSearch()
  }
}

onMounted(() => {
  fetchPhotos()
})

const selectedCard = ref({})

const openModal = (card) => {
  selectedCard.value = card
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
}

</script>

<template>
  <main>
    <div class="searchSection">
      <div class="searchForm" v-if="!searchLoading && !searchResults">
        <v-icon class="searchIcon" name="pr-search" @click="handleSearch" />
        <input
          v-model="searchQuery"
          @keypress="handleKeyPress"
          type="text"
          placeholder="Search for photo"
        />
      </div>
      <div class="searchText" v-if="searchLoading">
        <h1>
          Searching for <span>"{{ searchQuery }}"</span>
        </h1>
      </div>
      <div class="searchText" v-if="searchResults">
        <h1>
          Search Results for <span>"{{ searchQuery }}"</span>
        </h1>
      </div>
    </div>
    <ImageCards
      :openModal="openModal"
      :isLoading="isLoading"
      :imageData="imageData"
      :searchLoading="searchLoading"
    />
  </main>
  <ImageModal :closeModal="closeModal" :showModal="showModal" :selectedCard="selectedCard" />
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
