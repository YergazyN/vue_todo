<template>
    <input :value="modelValue" @input="updateInput" class="form-item" type="text">
</template>
<script>
export default {
    name: 'my-input',
    props: {
        modelValue: [String, Text]
    },
    methods: {
        updateInput(event) {
          this.$emit('update:modelValue', event.target.value)  
        }
    }
}
</script>
<style lang="scss">
    .form-item{
        margin-bottom: 10px;
        min-height: 30px;
        padding-left: 10px;
        outline: none;
      } 
</style>