<template>
  <div>
    <button @click="getMessage()">APIテスト</button>
    <div>{{ message }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
    }
  },
  methods: {
    async getMessage() {
      try {
        this.message = '通信中...'
        const res = await this.$axios.get('/api/test')
        this.message = 'success!! ' + res.data
      } catch(e) {
        this.message = 'failed... ' + e.message
      }
    }
  }
}
</script>
