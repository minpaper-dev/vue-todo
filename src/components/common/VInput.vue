<template>
  <div class="v-input">
    <input
      class="v-input__text"
      :value="value"
      @input="change"
      :type="type"
      :placeholder="placeholder"
      @keypress.enter="$emit('enter')"
    />
  </div>
</template>

<script>
export default {
  name: "VInput",
  props: {
    value: {
      type: String,
    },
    type: {
      type: String,
      default: "text",
    },
    placeholder: {
      type: String,
    },
  },
  methods: {
    change(event) {
      this.$emit("input", event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.v-input {
  display: inline;
  width: 120px;
  height: 30px;
}
.v-input__text {
  width: 100%;
  height: 100%;
  outline: none;
  border: 1px solid rgba(0, 0, 0, 0.15);
  padding-left: 8px;
  box-sizing: border-box;

  &:hover {
    border: 1px solid rgba(0, 0, 0, 0.54);
  }
  &:focus {
    border: 1px solid #00c4c4;
  }
}
</style>
