<template>
    <q-card class="box3">
        <div class="genre-container">
        <div v-if="selectedGenreIndex > 0" class="arrow-left" @click="scrollLeft">&lt;</div>
        <div
            v-for="(genre, index) in genres"
            :key="index"
            class="genre-item"
            :class="{ 'selected': index === selectedGenreIndex }"
            @click="selectGenre(index)"
            .inset-shadow-down
        >
            {{ genre }}
        </div>
        <div v-if="selectedGenreIndex < genres.length - 1" class="arrow-right" @click="scrollRight">&gt;</div>
        </div>
        <q-btn  class="submit-btn" @click="submitGenres">Submit</q-btn>
    </q-card>
</template>

<script setup>
    import { ref, onMounted } from 'vue'

    const genres = ref([
        'Blues',
        'Classical',
        'County',
        'Disco',
        'Hip-hop',
        'Jazz',
        'Metal',
        'Pop',
        'Reggae',
        'Rock'
    ])

    const genreMap = {
        0: 'Blues',
        1: 'Classical',
        2: 'County',
        3: 'Disco',
        4: 'Hip-hop',
        5: 'Jazz',
        6: 'Metal',
        7: 'Pop',
        8: 'Reggae',
        9: 'Rock'
    }

    const selectedGenreIndex = ref(0)

    const selectGenre = (index) => {
        selectedGenreIndex.value = index
    }   

    const scrollLeft = () => {
    if (selectedGenreIndex.value > 0) {
        selectedGenreIndex.value--
    }
    }

    const scrollRight = () => {
    if (selectedGenreIndex.value < genres.value.length - 1) {
        selectedGenreIndex.value++
    }
    }

    const submitGenres = () => {
    const selectedGenre = genreMap[selectedGenreIndex.value]
    console.log('Selected genre:', selectedGenre)
    // Call a function to submit selected genre to backend
    }

    onMounted(() => {
    // Additional initialization logic can go here
    })

    </script>

    <style scoped lang="scss">
    .genre-container {
        margin:4%;
        display: flex;
        overflow-x: auto;
        align-items: center;
        position: relative;
    }
  
    .genre-item {
        flex: 0 0 100px;
        height: 100px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 10px;
        background-color: rgba(255,255,255,0.75);
        margin-right: 10px;
        cursor: pointer;
        transition: box-shadow 0.3s ease;
    
    }

    .genre-item.selected {
        box-shadow: inset 0 0 60px 5px $q-color-box;
        //box-shadow: 10px 0px 0px rgba(0, 0, 0, 0.75);
    }

    .arrow-left,
    .arrow-right {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    font-size: 24px;
    color: rgba(0, 0, 0, 0.3);
    cursor: pointer;
    z-index: 5;
    }

    .arrow-left {
    left: 5px;
    }

    .arrow-right {
    right: 5px;
    }
    .submit-btn{
        background-color: $q-color-box;
        margin:4%;
        display: flex;
        overflow-x: auto;
        align-items: center;
        position: relative;

    }

    </style>
