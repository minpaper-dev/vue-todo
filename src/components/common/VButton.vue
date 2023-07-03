<template>
    <button class="v-button" :class="[variant]" :type="type" @click="clickEvent">
        <slot />
    </button>
</template>

<script>

export default {
    name : 'VButton',
    props : {
        type : {
            type : String,
            default : 'button'
        },
        variant : {
            type : String,
            default : 'outlined'
        }
    },
    methods : {
        clickEvent(){
            this.$emit('click')
        }
    }
}
</script>

<style lang="scss" scoped>
.v-button {
        width : 80px;
        height: 30px;
        background-color: #00C4C4;
        border: 1px solid #00C4C4;
        color : #fff;
        cursor: pointer;
        margin : 16px 0px;

        &:hover{
            border-color : #00b2b2;
            background-color : #00b2b2;
        }
    }
    
    .contained {
        background-color: #00C4C4;
        border: 1px solid #00C4C4;

        &:hover{
            border-color : #00b2b2;
            background-color : #00b2b2;
        }
    }

    .outlined {
        background-color: #fff;
        color: #00C4C4;
        border: 1px solid #00C4C4;

        &:hover{
            border-color : #00b2b2;
            background-color : #00b2b2;
            color : #fff
        }
    }
</style>
