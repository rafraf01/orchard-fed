<template>
    <Tag class="typography">
        <slot></slot>
    </Tag>
</template>

<script setup lang="ts">
export type TypographyTag = | 'a'
    | 'div'
    | 'span'
    | 'h1'
    | 'h2'
    | 'h3'
    | 'h4'
    | 'h5'
    | 'h6'
    | 'p'
    | 'small'
    | 'label';

export interface TypographyProps {
    tag?: TypographyTag;
}

const props = withDefaults(defineProps<TypographyProps>(), {
    tag: 'span',
});

const Tag = props.tag;

</script>

<style src="./TypographyTag.scss" lang="scss" scoped></style>