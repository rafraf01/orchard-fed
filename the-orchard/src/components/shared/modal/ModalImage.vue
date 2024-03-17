<template>
    <Teleport to="body">
        <div class="overlay"></div>
        <div class="modal-wrapper">
            <div class="modal">
                <XCircleIcon  @click="close" class="close"/>
                <ImageLoader :src="props.src" :altText="props.alt" class="image"/>
            </div>
        </div>
    </Teleport>
    
</template>

<script setup lang="ts">
import ImageLoader from '@/components/image/ImageLoader.vue';
import { XCircleIcon  } from "@heroicons/vue/24/solid";

interface ModalProps {
    src: string;
    alt: string;
}
const props = defineProps<ModalProps>();
const emit = defineEmits(['closeModal']);

/**
 * Close modal handler
 * Emit closeModal event
 */
const close = () => {
    const element = document.querySelector('.close');
    emit('closeModal');
    console.log({ element });
};

</script>

<style src="./ModalImage.scss" lang="scss" scoped>

</style>