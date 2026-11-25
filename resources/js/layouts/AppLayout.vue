<script setup>
import AppButton from '../components/AppButton.vue';
import AppLogo from '../components/AppLogo.vue';
import { useRoute } from 'vue-router';

const route = useRoute();

const navigationLinks = [
    { label: 'Vault', path: '/vault' },
    { label: 'Settings', path: '/settings' },
];
</script>

<template>
    <div class="min-h-screen">
        <header class="border-b border-mist/10">
            <div class="mx-auto flex max-w-5xl flex-wrap items-center justify-between gap-4 px-4 py-3">
                <RouterLink to="/vault" class="rounded-xl focus:outline-none focus-visible:ring-2 focus-visible:ring-mint">
                    <AppLogo />
                </RouterLink>
                <nav class="flex items-center gap-1">
                    <RouterLink
                        v-for="link in navigationLinks"
                        :key="link.path"
                        :to="link.path"
                        :class="route.path.startsWith(link.path) ? 'text-mint' : 'text-mist/70 hover:text-mist'"
                        class="rounded-xl px-3 py-2 font-medium transition focus:outline-none focus-visible:ring-2 focus-visible:ring-mint"
                    >
                        {{ link.label }}
                    </RouterLink>
                </nav>
                <div class="flex items-center gap-2">
                    <AppButton variant="ghost">Lock</AppButton>
                    <AppButton variant="ghost">Log out</AppButton>
                </div>
            </div>
        </header>
        <main class="mx-auto max-w-5xl px-4 py-8">
            <slot />
        </main>
    </div>
</template>
