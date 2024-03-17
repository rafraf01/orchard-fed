<template>
    <div class="card-component">
        <section class="image-wrapper">
            <Image :src="props.image.src" :altText="props.image.alt" :onClick="handleImageClick" :is-bordered="true"
                class="card-image" />
        </section>
        <section class="card-content">
            <Typography tag="label" class="card-label">{{ props.headline }}</Typography>
            <Typography tag="p" class="card-text">{{ props.text }}</Typography>
            <Link :onClick="handleClick" :text="props.link" class="card-link" />
        </section>
    </div>
</template>

<script setup lang="ts">
import Image from "@/components/image/ImageLoader.vue";
import Typography from "@/components/typography/TypographyTag.vue";
import AnchorTag from "@/components/ui/anchor/AnchorTag.vue";
import { ImageInterface } from "@/interface/interfaces";

export interface CardProps {
    headline: string;
    image: ImageInterface;
    text?: string;
    link: string;
}

const props = defineProps<CardProps>();
const emit = defineEmits(['imageClick']);

/**
 * Handle anchor click
 * logs element and text content
 */
const handleClick = () => {
    const element = document.querySelector('.card-link');
    console.log({
        element,
        text: element?.textContent
    });
}

/**
 * Handle image click
 * Used emitter to pass image data to parent
 * logs element
 */
const handleImageClick = () => {
    const element = document.querySelector('.card-image');
    console.log({ element })
    emit('imageClick', props.image);
}

const Link = AnchorTag;

</script>

<style lang="scss" src="./ImageCard.scss" scoped></style>