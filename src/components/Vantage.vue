<template>
  <div>
    <div> 測試組件: {{msg}}</div>
    <p>
      <button @click="addData">EMITADD</button>
    </p>
  </div>
</template>
<script>
export default {
  name: 'Vantage',
  props: {
    msg: {
      type: Number
    },
    inemit: {
      type: Number
    }
  },
  methods: {
    addData() {
      console.log(this.msg)
      this.$emit('emitevent', this.msg + this.inemit)
    }
  }
}
</script>