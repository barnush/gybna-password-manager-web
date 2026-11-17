<script setup>
import { useId } from 'vue';

defineOptions({ inheritAttrs: false });

defineProps({
    label: { type: String, required: true },
    error: { type: String, default: '' },
    type: { type: String, default: 'text' },
});

const model = defineModel({ type: String, default: '' });

const inputId = useId();
const errorId = useId();
</script>

<template>
    <div class="flex flex-col gap-1.5">
        <label :for="inputId" class="text-sm font-medium text-mist/80">{{ label }}</label>
        <input
            :id="inputId"
            v-model="model"
            v-bind="$attrs"
            :type="type"
            :aria-invalid="error ? 'true' : 'false'"
            :aria-describedby="error ? errorId : undefined"
            :class="error ? 'border-red-400' : 'border-mist/15'"
            class="w-full rounded-xl border bg-mist/5 px-4 py-2.5 text-mist placeholder:text-mist/40 transition focus:border-mint focus:outline-none focus:ring-2 focus:ring-mint/40"
        />
        <p v-if="error" :id="errorId" class="text-sm text-red-400">{{ error }}</p>
    </div>
</template>
