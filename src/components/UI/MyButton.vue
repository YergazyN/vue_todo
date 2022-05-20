<template>
    <button class="form-button">
        <slot></slot>
    </button>
</template>
<script>
export default {
    name: 'my-button'
}
</script>
<style lang="scss">
    .form-button{        
        display: inline-block;        
        padding: 8px 12px;
        border: 1px solid teal;
        color: teal;
        background: #fff;
        cursor: pointer;
        
      }
</style>