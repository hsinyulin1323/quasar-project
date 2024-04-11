<template>
    <div class="box4" @mouseover="isHovered = true" @mouseleave="isHovered = false">
        <div v-if="isHovered" class="popup">
          <div class="popup-content">
            <div class="upload-field">
              <q-input
                @update:model-value="val => { file = val[0] }"
                filled
                type="file"
                hint="only .wav is accepted"
              />
            </div>
            <div class="right-section">
              <div class="description-fields">
                <q-input
                  v-model="musicTitle"
                  filled
                  label="Music Title"
                />
                <q-input
                  v-model="musicPrompt"
                  filled
                  label="Music Prompt"
                />
              </div>
              <div class="category-field">
                <q-select 
                  v-model="selectedGenre"
                  :options="genreOptions"
                  filled
                  label="Music Genre"
                />
              </div>
              <div class="submit-button">
                <q-btn
                  label="Submit"
                  color="primary"
                  @click="submitMusic"
                />
              </div>
            </div>
          </div>
        </div>
    upload music
  </div>
</template>
<script> //box4
export default {
  data() {
    return {
      isHovered: false,
      file: null,
      selectedGenre: null,
      musicTitle: '',
      musicPrompt: '',
      genreOptions: [
        { label: 'Blues', value: 'Blues' },
        { label: 'Classical', value: 'Classical' },
        { label: 'Country', value: 'Country' },
        { label: 'Disco', value: 'Disco' },
        { label: 'Hip-hop', value: 'Hip-hop' },
        { label: 'Jazz', value: 'Jazz' },
        { label: 'Metal', value: 'Metal' },
        { label: 'Pop', value: 'Pop' },
        { label: 'Reggae', value: 'Reggae' },
        { label: 'Rock', value: 'Rock' },
        { label: 'Custom Genre', value: null }
      ]
    };
  },
  methods: {
    submitMusic() {
      // Implement your submission logic here
    }
  }
};
</script>
<style>

& .popup {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: white;
      border: 1px solid #ccc;
      border-radius: 5px;
      padding: 20px;
      box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
      z-index: 1;
  }

    & .popup-content {
        display: flex;
        justify-content: space-between;
    }

    & .upload-field {
        flex: 1;
    }

    & .right-section {
        flex: 1;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-left: 20px;
    }

    & .description-fields {
        margin-bottom: 20px;
    }

    & .category-field {
        margin-bottom: 20px;
    }

    & .submit-button {
        align-self: flex-end;
    }
</style>