<script setup>
import { computed } from 'vue';

const props = defineProps({
    variant: { type: String, default: 'primary' },
    loading: { type: Boolean, default: false },
    type: { type: String, default: 'button' },
});

const variantClasses = {
    primary: 'bg-mint text-night hover:bg-mint/85',
    ghost: 'border border-mist/20 text-mist hover:bg-mist/10',
    danger: 'bg-red-400 text-night hover:bg-red-400/85',
};

const buttonClasses = computed(() => variantClasses[props.variant] ?? variantClasses.primary);
</script>

<template>
    <button
        :type="type"
        :disabled="loading"
        :class="buttonClasses"
        class="inline-flex items-center justify-center gap-2 rounded-xl px-4 py-2.5 font-medium transition focus:outline-none focus-visible:ring-2 focus-visible:ring-mint focus-visible:ring-offset-2 focus-visible:ring-offset-night disabled:cursor-not-allowed disabled:opacity-60"
    >
        <span
            v-if="loading"
            class="size-4 animate-spin rounded-full border-2 border-current border-t-transparent"
        ></span>
        <slot />
    </button>
</template>
