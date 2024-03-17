<template>
    <ContentBlock>
        <ImageWithText :images="data.images" :heading="data.heading" :content="data.content" @image="handleListener" />
        <div v-if="isModalOpen">
            <ModalImage class="modal-image" :src="source.modalImage" :alt="source.alt" @closeModal="handleCloseModal" />
        </div>
    </ContentBlock>
</template>

<script lang="ts" setup>
import ContentBlock from '@/components/shared/content-block/ContentBlock.vue';
import ImageWithText from '@/components/image-with-text/ImageWithText.vue';
import ModalImage from '@/components/shared/modal/ModalImage.vue';
import Image1 from "@/assets/static-one/image01.jpg";
import Image2 from "@/assets/static-one/image02.jpg";
import Image3 from "@/assets/static-one/image03.jpg";
import ImageModal1 from "@/assets/static-one/Image-01@2x.jpg";
import ImageModal2 from "@/assets/static-one/Image-02@2x.jpg";
import ImageModal3 from "@/assets/static-one/Image-03@2x.jpg";

import { ref } from 'vue';

/**
 * Image with text data
 * Assuming that this comes from CMS 
 */
const data = ref({
    heading: `ANSWER YOUR BODY'S NEEDS`,
    content: {
        text: `The way ingredients are sourced affects the way we nourish our bodies. Author Mark Schatzer believes pur body naturally develops an appetite for the foods and nutrients it needs to be healthy, but that artificial flavourings are getting in the way. This can be reversed by focusing on high-quality ingredients and being mindful as your appetite guides you to consume according to your body's needs.`,
        subTitle: 'BE MINDFUL',
        subText: `Sourcing local or organic food is a good way to start being more mindful about what you're cooking and eating.`
    },
    images: [
        {
            src: Image1,
            alt: 'image1',
            modalImage: ImageModal1
        },
        {
            src: Image2,
            alt: 'image2',
            modalImage: ImageModal2
        },
        {
            src: Image3,
            alt: 'image3',
            modalImage: ImageModal3
        }
    ]
});

const isModalOpen = ref(false);
const source = ref({
    modalImage: '',
    alt: ''
})

const handleCloseModal = () => {
    isModalOpen.value = false;
}
const handleListener = (event: {modalImage: string; alt: string}) => {
    if (event) {
        isModalOpen.value = !isModalOpen.value;
    }
    source.value = event;
}

</script>

<style lang="scss" scoped src="./BlockOne.scss"></style>