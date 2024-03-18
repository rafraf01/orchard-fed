<template>
    <section class="image-with-text-component">
        <div class="image-wrapper">
            <template v-for="data of props.images" :key="data.alt">
                <Image :src="data.src" :altText="data.alt"  @click="handleImageClick(data)" class="image" :hasCustomHeight="true"/>
            </template>
        </div>
        <div class="text-content">
            <Typography tag="h1" class="heading">{{ props.heading }}</Typography>
            <Typography tag="p" class="paragraph">{{ props.content.text }}</Typography>
            <Typography tag="span" class="sub-title">{{ props.content.subTitle }}</Typography>
            <Typography tag="p" class="sub-text">{{ props.content.subText }}</Typography>
        </div>
    </section>
</template>

<script setup lang="ts">
import { type ImageInterface, type ImageWithTextContent } from '@/interface/interface';
import Typography from '@/components/typography/TypographyTag.vue';
import Image from '@/components/image/ImageLoader.vue';

type Images = ImageInterface[];
export interface ImageWithTextProps {
    images: Images;
    heading: string;
    content: ImageWithTextContent;
}

const props = defineProps<ImageWithTextProps>();
const emit = defineEmits(['image']);

/**
 * Handle image click
 * Used emitter to pass image data to parent
 * logs element
 * @param {ImageInterface} image - image object to be passed
 */
const handleImageClick = (image: ImageInterface) => {
    const element = document.querySelector('.image');
    console.log({ element });
    emit('image', image);
}

</script>

<style lang="scss" src="./ImageWithText.scss" scoped>

</style>