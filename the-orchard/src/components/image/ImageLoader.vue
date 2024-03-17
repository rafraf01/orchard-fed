<template>
    <div class="image-container">
        <img loading="lazy" 
        :src="props.src" 
        :alt="props.altText" 
        :class="{
           'isBordered': isBordered,
           'widthAuto': isAuto,
           'customHeight': hasCustomHeight
        }"
        class="image" 
        @click="onClick" />
    </div>
</template>

<script setup lang="ts">

interface ImageProps {
    onClick?: () => void;
    src: string;
    altText: string;
    isBordered?: boolean;
    isAuto?: boolean;
    hasCustomHeight?: boolean;
}

const props = withDefaults(defineProps<ImageProps>(), {
    isBordered: false
});

</script>

<style lang="scss" src="./ImageLoader.scss" scoped></style>