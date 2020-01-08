<template>
  <div>
    <slot
      :tags="tags"
      :removeTag="removeTag"
      :inputProps="{
        value: input
      }"
      :inputEvents="{
        input: onInput,
        keydown: keydown
      }"
    >
      <p>Default</p>
    </slot>
  </div>
</template>

<script>
export default {
  model: {
    prop: "tags",
    event: "update"
  },
  props: ["tags"],
  data() {
    return {
      input: ""
    };
  },
  computed: {
    newTag() {
      return this.input.trim();
    }
  },
  methods: {
    onInput(e) {
      this.input = e.target.value;
    },
    addTag() {
      if (this.newTag.length === 0 || this.tags.includes(this.newTag)) {
        return;
      }
      this.$emit("update", [...this.tags, this.newTag]);
      this.clearInput();
    },
    clearInput() {
      this.input = "";
    },
    handleBackspace() {
      if (this.newTag.length === 0) {
        this.$emit("update", this.tags.slice(0, -1));
      }
    },
    keydown(e) {
      if (e.key === "Backspace") {
        this.handleBackspace();
      }
      if (e.key === "Enter") {
        e.preventDefault();
        this.addTag();
      }
    },
    removeTag(tag) {
      this.$emit(
        "update",
        this.tags.filter(t => t !== tag)
      );
    }
  }
};
</script>
