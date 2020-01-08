<template>
  <div id="app" class="min-h-screen bg-gray-700 p-8">
    <div class="max-w-md mx-auto card mt-8">
      <label class="form-label mb-2">Tag Input</label>
      <TagInput>
        <div class="tag-input" slot-scope="{}">
          <span class="tag-input-tag">
            <span>sample tag</span>
            <button type="button" class="tag-input-remove">&times;</button>
          </span>
          <input class="tag-input-text" placeholder="Add tag..." />
        </div>
      </TagInput>
    </div>
  </div>
</template>

<script>
import TagInput from "./components/TagInput.vue";

export default {
  name: "app",
  components: {
    TagInput
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
