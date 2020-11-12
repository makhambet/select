<template>
  <div id="app">
    <div class="content">
      <app-select
        :select="select"
        :model="resultArr"
        :placeholder="'Выберите нужное'"
        @change="changeValue"
      ></app-select>
    </div>
  </div>
</template>

<script>
import AppSelect from './components/select'

export default {
  name: 'App',
  data() {
    return {
      select: [
        {
          id: 1,
          name: '1111111'
        },
        {
          id: 2,
          name: '2222222'
        },
        {
          id: 3,
          name: '3333333'
        },
        {
          id: 4,
          name: '3333333'
        },
        {
          id:54,
          name: '3333333'
        }
      ],
      resultArr: null
    }
  },
  methods: {
    changeValue(value) {
      this.resultArr = value
    }
  },
  components: {
    AppSelect
  }
}
</script>

<style>
  .content {
    margin: 200px auto 0;
    width: 500px;
  }
</style>
