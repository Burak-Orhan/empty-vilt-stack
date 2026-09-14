<script setup>
import { ref } from 'vue';

const showGuide = ref(false);
</script>

<template>
    <div class="relative flex items-center justify-center min-h-screen bg-zinc-950 font-sans selection:bg-zinc-800 selection:text-white">

        <div class="w-full max-w-3xl p-8 mx-4">
            <div class="flex flex-wrap items-center gap-3 mb-10">
                <span class="px-3 py-1.5 text-xs font-medium text-zinc-400 bg-zinc-900/50 border border-zinc-800 rounded-md">Laravel</span>
                <span class="px-3 py-1.5 text-xs font-medium text-zinc-400 bg-zinc-900/50 border border-zinc-800 rounded-md">Inertia.js</span>
                <span class="px-3 py-1.5 text-xs font-medium text-zinc-400 bg-zinc-900/50 border border-zinc-800 rounded-md">Vue 3</span>
                <span class="px-3 py-1.5 text-xs font-medium text-zinc-400 bg-zinc-900/50 border border-zinc-800 rounded-md">Tailwind CSS</span>
            </div>

            <div>
                <h1 class="text-4xl md:text-5xl font-bold tracking-tight text-zinc-100 mb-6">
                    The VILT Stack is Ready.
                </h1>

                <p class="text-base md:text-lg text-zinc-500 mb-12 leading-relaxed max-w-2xl">
                    A clean, robust, and scalable foundation for your next project. Perfectly configured without the bloat, ready for you to build high-performance modern web applications.
                </p>

                <div class="flex flex-col sm:flex-row items-center gap-4">
                    <button
                        @click="showGuide = true"
                        class="w-full sm:w-auto px-6 py-3 text-sm font-medium text-zinc-900 bg-zinc-100 rounded-md hover:bg-white transition-colors text-center"
                    >
                        Pro Tips & Setup
                    </button>

                    <a href="https://github.com/Burak-Orhan" target="_blank" class="w-full sm:w-auto px-6 py-3 text-sm font-medium text-zinc-300 bg-transparent border border-zinc-700 rounded-md hover:bg-zinc-900 transition-colors text-center">
                        View on GitHub
                    </a>
                </div>
            </div>
        </div>

        <transition
            enter-active-class="transition ease-out duration-300"
            enter-from-class="opacity-0 scale-95"
            enter-to-class="opacity-100 scale-100"
            leave-active-class="transition ease-in duration-200"
            leave-from-class="opacity-100 scale-100"
            leave-to-class="opacity-0 scale-95"
        >
            <div
                v-if="showGuide"
                class="fixed inset-0 z-50 flex items-center justify-center px-4 bg-zinc-950/80 backdrop-blur-sm"
                @click.self="showGuide = false"
            >
                <div class="w-full max-w-2xl p-8 bg-zinc-900 border border-zinc-800 rounded-xl shadow-2xl">

                    <div class="flex items-center justify-between mb-6">
                        <h2 class="text-xl font-semibold text-zinc-100">VILT Pro Tips</h2>
                        <button @click="showGuide = false" class="text-zinc-500 hover:text-zinc-300 transition-colors">
                            <svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                            </svg>
                        </button>
                    </div>

                    <div class="space-y-4">

                        <div class="p-4 rounded-lg bg-zinc-950/50 border border-zinc-800/50">
                            <h3 class="flex items-center gap-2 text-sm font-semibold text-zinc-200 mb-2">
                                <svg class="w-4 h-4 text-emerald-500" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M11.3 1.046A120.1 120.1 0 0010 1C5.58 1 2 4.58 2 9s3.58 8 8 8 8-3.58 8-8-3.58-8-8-8zm-2.03 11.234a.75.75 0 01-1.04-.04l-2.5-2.5a.75.75 0 111.04-1.08l1.94 1.94 4.48-5.38a.75.75 0 111.16.96l-5.08 6.1z" clip-rule="evenodd" /></svg>
                                Persistent Layouts
                            </h3>
                            <p class="text-sm text-zinc-400 mb-3">
                                Prevent sidebars and navbars from re-rendering on page navigation. Avoid wrapping your template with layout components.
                            </p>
                            <code class="block w-full p-3 text-xs text-emerald-400 bg-zinc-950 rounded border border-zinc-800 font-mono">
                                &lt;script setup&gt;<br>
                                import AppLayout from '@/Layouts/AppLayout.vue';<br>
                                defineOptions({ layout: AppLayout });<br>
                                &lt;/script&gt;
                            </code>
                        </div>

                        <div class="p-4 rounded-lg bg-zinc-950/50 border border-zinc-800/50">
                            <h3 class="flex items-center gap-2 text-sm font-semibold text-zinc-200 mb-2">
                                <svg class="w-4 h-4 text-cyan-500" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M11.3 1.046A120.1 120.1 0 0010 1C5.58 1 2 4.58 2 9s3.58 8 8 8 8-3.58 8-8-3.58-8-8-8zm-2.03 11.234a.75.75 0 01-1.04-.04l-2.5-2.5a.75.75 0 111.04-1.08l1.94 1.94 4.48-5.38a.75.75 0 111.16.96l-5.08 6.1z" clip-rule="evenodd" /></svg>
                                Global Shared Data
                            </h3>
                            <p class="text-sm text-zinc-400 mb-3">
                                Share the authenticated user or flash messages globally without prop drilling. Update <code class="text-xs text-zinc-300 bg-zinc-800 px-1 py-0.5 rounded">HandleInertiaRequests.php</code> and access it anywhere via <code class="text-xs text-zinc-300 bg-zinc-800 px-1 py-0.5 rounded">usePage()</code>.
                            </p>
                            <code class="block w-full p-3 text-xs text-cyan-400 bg-zinc-950 rounded border border-zinc-800 font-mono">
                                const user = usePage().props.auth.user;<br>
                                const flash = usePage().props.flash.message;
                            </code>
                        </div>

                        <div class="p-4 rounded-lg bg-zinc-950/50 border border-zinc-800/50">
                            <h3 class="flex items-center gap-2 text-sm font-semibold text-zinc-200 mb-2">
                                <svg class="w-4 h-4 text-purple-500" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M11.3 1.046A120.1 120.1 0 0010 1C5.58 1 2 4.58 2 9s3.58 8 8 8 8-3.58-8-8-3.58-8-8-8zm-2.03 11.234a.75.75 0 01-1.04-.04l-2.5-2.5a.75.75 0 111.04-1.08l1.94 1.94 4.48-5.38a.75.75 0 111.16.96l-5.08 6.1z" clip-rule="evenodd" /></svg>
                                Optimize Inertia Payloads
                            </h3>
                            <p class="text-sm text-zinc-400">
                                Inertia sends JSON responses. Always use Laravel's <code class="text-xs text-zinc-300 bg-zinc-800 px-1 py-0.5 rounded">->select()</code> or API Resources to prevent exposing sensitive database columns and to keep the initial page load blazing fast.
                            </p>
                        </div>

                    </div>

                </div>
            </div>
        </transition>

    </div>
</template>
