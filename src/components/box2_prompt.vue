<template>
    <div class="box2" @mouseover="isHovered = true" @mouseleave="isHovered = false" >
      Enter Prompt
      <div v-if="isHovered" class="hover-border"></div>
      <textarea v-model="prompt" rows="4" placeholder="请输入或选择标签"></textarea>
      <div class="tag-container">Selected Tag(s)
        <span v-for="tag in selectedTags" :key="tag" class="selected-tag" @click="removeTag(tag)">{{ tag }}</span>
      </div>
      <div class="messy-tags">
        <span v-for="tag in unselectedTags" :key="tag" class="tag" @click="addTag(tag)">{{ tag }}</span>
      </div>
      <button color="q-color-box" @click="submitPrompt">SUBMIT</button>
    </div>
</template>
  
<script>
  export default {
    data() {
      return {
        isHovered: false,
        prompt: '',
        tags: ['adjective1', 'adjective2', 'adjective3', 'adjective4', 'adjective5'],
        selectedTags: [],
      }
    },
    computed: {
      unselectedTags() {
        return this.tags.filter(tag => !this.selectedTags.includes(tag));
      }
    },
    methods: {
      addTag(tag) {
        this.selectedTags.push(tag);
        this.prompt += ` ${tag}`;
      },
      removeTag(tag) {
        this.selectedTags = this.selectedTags.filter(t => t !== tag);
        this.prompt = this.prompt.replace(` ${tag}`, '');
      },
      submitPrompt() {
        // Handle submit logic here
        console.log('Submitted prompt:', this.prompt);
      }
    }
  }
</script>