<template>
    <div class="dialog" v-if="show" @click.stop="hideDialog">        
        <div @click.stop class="dialog__content">
            <div class="close" @click.stop="hideDialog"><i class="ri-close-line"></i></div>
            <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
    name: 'my-dialog',
    props: {
        show: {
            type: Boolean,
            default: false
        }
    },
    methods: {
        hideDialog() {
          this.$emit('update:show', false) 
        }
    }
}
</script>
<style lang="scss">
    .dialog{
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background: rgba(0,0,0, .5);
        position: fixed;
        display: flex;        

        .dialog__content{
            margin: auto;
            background: #fff;
            border-radius: 12px;
            min-height: 50px;
            min-width: 500px;
            padding: 15px;
            position: relative;

            .close{
                position: absolute;
                right: 15px;
                top: 15px;
                cursor: pointer;
            }
        }
    }
</style>