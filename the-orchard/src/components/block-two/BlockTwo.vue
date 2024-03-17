<template>
    <ContentBlock>
        <div class="component">
            <Typography tag="h1" class="title">{{ cardData.title }}</Typography>
            <div class="block-content">
                <template v-for="data of cardData.data" :key="data.content.title">
                    <ImageCard 
                        :headline="data.content.title"
                        :image="data.image"
                        :text="data.content.text"
                        :link="data.content.link"
                        @imageClick="handleListener"
                    ></ImageCard>
                </template>
                <div v-if="isModalOpen">
                    <ModalImage :src="source.modalImage" :alt="source.alt" @closeModal="handleCloseModal" />
                </div>
            </div>
        </div>
    </ContentBlock>
</template>

<script setup lang="ts">
import { ref } from "vue";
import ImageCard from "@/components/image-card/ImageCard.vue";
import Typography from "@/components/typography/TypographyTag.vue";
import ContentBlock from "@/components/shared/content-block/ContentBlock.vue";
import Image01 from "@/assets/static-two/image01.jpg";
import Image02 from "@/assets/static-two/image02.jpg";
import Image03 from "@/assets/static-two/image03.jpg";
import ImageModal01 from "@/assets/static-two/Image-01@2x.jpg";
import ImageModal02 from "@/assets/static-two/Image-02@2x.jpg";
import ImageModal03 from "@/assets/static-two/Image-03@2x.jpg";
import ModalImage from "@/components/shared/modal/ModalImage.vue";

/**
 * Card Data 
 * Assuming that this data comes from CMS
 */
const cardData = ref({
  title: 'ALL THE LATEST FROM AEG',
  data: [
    {
      image: {
        alt: 'image01',
        src: Image01,
        modalImage:ImageModal01
      },
      content: {
        title: 'Summer Lunch Menu By Mark Best',
        text: `AEG ambassador Mark Best's summer easts are guaranteed to help you make the most of the warmer weather and entertaining at home.`,
        link: 'READ MORE'
      }
    },
    {
      image: {
        alt: 'image02',
        src: Image02,
        modalImage:ImageModal02
      },
      content: {
        title: 'A Traditional Christmas Eve, Mark Best Style',
        text: `One of Australia's best chefs and AEG ambassador. Mark Best, shares his favourite Christmas Eve menu which is sure to impress your guests.`,
        link: 'READ MORE'
      }
    },
    {
      image: {
        alt: 'image03',
        src: Image03,
        modalImage: ImageModal03
      },
      content: {
        title: 'Taking Taste Further',
        text: `This executive cookbook gives you all the know-how you need. We've designed it to make sure you get the most out of our products - and the best out of your food.`,
        link: 'READ MORE'
      }
    }
  ]
});

const isModalOpen = ref(false);
const source = ref({
  modalImage: '',
  alt: ''
});

const handleListener = (event: {modalImage: string; alt: string}) => {
    if (event) {
        isModalOpen.value = !isModalOpen.value;
    }
    source.value = event;
};

const handleCloseModal = () => {
    isModalOpen.value = false;
}

</script>

<style lang="scss" src="./BlockTwo.scss" scoped>

</style>