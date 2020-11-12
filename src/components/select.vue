<template>
  <div class="select">
    <div
      @click="onSelect=!onSelect"
      class="select__input"
      :class="{'on-select': onSelect}"
    >{{ model ? model.name : placeholder }}</div>
    <div v-show="onSelect" class="select__options">
      <div
        @click="change(value)"
        class="option"
        v-for="value in select"
        :key="value.id"
      >
        {{ value.name }}
      </div>
    </div>
    <div v-show="onSelect" @contextmenu.prevent="onSelect=false" @click="onSelect=false" class="close"></div>
  </div>
</template>

<script>
export default {
  props: {
    select: {
      type: Array,
      default: () => []
    },
    model: {
      type: Object,
      default: () => {}
    },
    placeholder: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      onSelect: false
    }
  },
  methods: {
    change(value) {
      this.onSelect = false
      this.$emit('change', value)
    }
  },
}
</script>

<style scoped>
  .select {
    width: 100%;
    position: relative;
  }
  .select__input {
    border: 1px solid #ced4da;
    height: 24px;
    padding: 6px 10px;
    line-height: 24px;
    border-radius: 5px;
    cursor: pointer;
  }
  .select__input.on-select {
    box-shadow: 0 0 5px cornflowerblue;
  }
  .select__options {
    position: absolute;
    top: 100%;
    width: 100%;
    left: 0;
    background: #FFF;
    border: 1px solid #ced4da;
    z-index: 4;
    max-height: 98px;
    overflow-y: auto;
  }
  .option {
    cursor: pointer;
    height: 24px;
    line-height: 24px;
    padding-left: 10px;
  }
  .option:hover {
    color: #FFFFFF;
    background-color: cornflowerblue;
  }
  .close {
    position: fixed;
    width: 100%;
    height: 100vh;
    z-index: 3;
    top: 0;
    left: 0;
  }
</style>
