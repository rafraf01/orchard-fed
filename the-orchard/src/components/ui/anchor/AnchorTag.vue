<template>
    <a class='link' @click="onClick">
        {{  props.text }}
    </a>
</template>

<script setup lang="ts">
interface LinkProps {
    onClick: () => void;
    text: string;
}

const props = defineProps<LinkProps>();

</script>

<style lang="scss" src="./AnchorTag.scss" scoped>

</style>