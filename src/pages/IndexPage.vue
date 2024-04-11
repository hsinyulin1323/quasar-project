<template>
  <q-page class="layout">
    <q-card class="box1">profile</q-card>
    <Box2_prompt @submit="generateSong"></Box2_prompt>
    <Box3_Genres @submit="generateSong"></Box3_Genres>
    <Box4_upload @submit="generateSong"></Box4_upload>
    <q-card class="box5">progress bar</q-card>
    <Box5_progress :isGenerating="isGenerating"></Box5_progress>
    <Box6_output :song="song" :songDescription="songDescription"></Box6_output>
    <q-card class="box7">history</q-card>
  </q-page>
</template>



<script setup>
import { ref } from 'vue'
import Box2_prompt from 'src/components/box2_prompt.vue'
import Box3_Genres from 'src/components/box3_genre.vue'
import Box4_upload from 'src/components/box4_upload.vue'
import Box5_progress from 'src/components/box5_progress.vue'
import Box6_output from 'src/components/box6_output.vue'


const song = ref(null)
const songDescription = ref('A song...')
const isGenerating = ref(false)

const generateSong = () => {
  isGenerating.value = true
  // Call backend API to generate song
  // Update song and songDescription data properties
  // After API call completes, set isGenerating.value to false
}
</script>

<!--

<script setup>
  defineOptions({
    name: 'IndexPage'
  });
</script>
<script>

import Box2_prompt from 'pages/box2_prompt.vue';
import Box4_upload from 'pages/box4_upload.vue'; 
import Box6_output from 'pages/box6_output.vue';
export default {
  components: {
    Box2_prompt,
    Box4_upload,
    Box6_output,
  },
  data() {
    return {
      song: null,
      songDescription: 'A song...'
    }
  },
  methods: {
    generateSong() {
      // Call backend API to generate song
      // Update song and songDescription data properties
    }
  }
};
</script>



<script> //box2
export default {
  data() {
    return {
      isHovered: false,
      prompt: '',
      tags: ['adjective1', 'adjective2', 'adjective3', 'adjective4', 'adjective5']
    }
  },
  methods: {
    addToPrompt(tag) {
      this.prompt += ` ${tag}`;
    },
    submitPrompt() {
      // Handle submit logic here
      console.log('Submitted prompt:', this.prompt);
    }
  }
}
</script>
-->
