<script setup>
import AppLogo from '../components/AppLogo.vue';

defineProps({
    title: { type: String, required: true },
});
</script>

<template>
    <main class="flex min-h-screen flex-col items-center justify-center gap-8 px-4 py-12">
        <AppLogo />
        <section class="w-full max-w-md rounded-xl border border-mist/10 bg-mist/5 p-6 sm:p-8">
            <h1 class="mb-6 text-2xl font-bold text-mist">{{ title }}</h1>
            <slot />
        </section>
    </main>
</template>
