<template>
    <div class="box6">
      <div class="player">
        <q-btn round color="q-color-box" icon="play_arrow" @click="playSong" />
        <q-linear-progress class="q-mt-sm" :value="songProgress" color="q-color-box" />
      </div>
      <p>{{ songDescription }}</p>
      <div class="down">
        <div class="rating">
          <q-btn round color="q-color-box" icon="thumb_up" @click="rateSong(true)" /> 
          <q-btn round color="q-color-box" icon="thumb_down" @click="rateSong(false)" />
        </div>
        <q-btn color="q-color-box" @click="downloadSong" >Download</q-btn>
      </div>
    </div>
</template>

    <script>
    export default {
      props: {
        song: {
          ype: Object,
          required: true
        },
        songDescription: {
          type: String,
          required: true
        }
      },
      data() {
        return {
          songProgress: 0
        }
      },
        methods: {
            playSong() {
                // Play song and update songProgress
            },
            rateSong(liked) {
                // Send rating to backend
            },
            downloadSong() {
                // Download song
            }
        }
    }
   </script>

<style>
.player {
      display:flex;
      align-items: center;
    }
    .down{
      display: flex;
      justify-content: space-between; 
      gap: 1rem;
      margin: 0.5rem 0;
      .rating {
        display: flex;
        justify-content: space-between; 
        gap: 1rem;
        margin: 1rem 0;
      }
    }

</style>