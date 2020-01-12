<template>
  <div id="app" class="min-h-screen bg-gray-700 p-8">
    <h2 class="text-center text-4xl font-bold text-green-700">Vue Tag Input</h2>
    <div class="max-w-xl mx-auto card mt-8">
      <label class="form-label mb-2">Tag Input</label>
      <TagInput v-model="tags">
        <div
          class="tag-input"
          slot-scope="{ tags, removeTag, inputProps, inputEvents }"
        >
          <span v-for="tag in tags" :key="tag" class="tag-input-tag">
            <span>{{ tag }}</span>
            <button
              type="button"
              class="tag-input-remove"
              @click="removeTag(tag)"
            >
              &times;
            </button>
          </span>
          <input
            class="tag-input-text"
            placeholder="Add tag..."
            v-bind="inputProps"
            v-on="inputEvents"
          />
        </div>
      </TagInput>
    </div>
    <p class="text-white text-center mt-20">Examples will be added soon..</p>
  </div>
</template>

<script>
import TagInput from "./components/TagInput.vue";

export default {
  components: {
    TagInput
  },
  data() {
    return {
      tags: ["vue", "react", "svelte"]
    };
  }
};
</script>

<style lang="scss">
@import "./assets/index.css";

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
