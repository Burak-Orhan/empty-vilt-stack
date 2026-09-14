<script setup>
import { Head, Link } from '@inertiajs/vue3';

const stats = [
    { name: 'Total Revenue', value: '$45,231.89', change: '+20.1%', trend: 'up' },
    { name: 'Active Users', value: '2,314', change: '+15.2%', trend: 'up' },
    { name: 'New Signups', value: '142', change: '-3.1%', trend: 'down' },
    { name: 'System Uptime', value: '99.9%', change: '0.0%', trend: 'neutral' },
];

const recentUsers = [
    { id: 1, name: 'Burak Orhan', email: 'burak@example.com', role: 'Superadmin', status: 'Active' },
    { id: 2, name: 'John Doe', email: 'john@example.com', role: 'Editor', status: 'Offline' },
    { id: 3, name: 'Jane Smith', email: 'jane@example.com', role: 'User', status: 'Active' },
];
</script>

<template>
    <Head title="Dashboard" />

    <div class="flex h-screen bg-zinc-950 text-zinc-100 font-sans selection:bg-zinc-800 selection:text-white">

        <aside class="w-64 flex flex-col border-r border-zinc-800 bg-zinc-900/30">
            <div class="flex items-center h-16 px-6 border-b border-zinc-800">
                <span class="text-lg font-bold tracking-tight text-white">VILT<span class="text-zinc-500">Panel</span></span>
            </div>

            <nav class="flex-1 px-4 py-6 space-y-2">
                <a href="#" class="flex items-center gap-3 px-3 py-2 text-sm font-medium text-white bg-zinc-800/50 rounded-lg">
                    <svg class="w-5 h-5 text-zinc-400" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" /></svg>
                    Dashboard
                </a>

                <a href="#" class="flex items-center gap-3 px-3 py-2 text-sm font-medium text-zinc-400 rounded-lg hover:text-white hover:bg-zinc-800/50 transition-colors">
                    <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" /></svg>
                    Users
                </a>
            </nav>

            <div class="p-4 border-t border-zinc-800">
                <Link :href="route('welcome')" class="flex items-center justify-center w-full gap-2 px-4 py-2 text-sm font-medium text-zinc-300 bg-zinc-800 rounded-lg hover:bg-zinc-700 transition-colors">
                    <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18" /></svg>
                    Back to Website
                </Link>
            </div>
        </aside>

        <main class="flex-1 flex flex-col overflow-hidden">

            <header class="flex items-center justify-between h-16 px-8 border-b border-zinc-800 bg-zinc-950">
                <h1 class="text-xl font-semibold text-zinc-100">Overview</h1>
                <div class="flex items-center gap-4">
                    <button class="w-8 h-8 rounded-full bg-zinc-800 border border-zinc-700 flex items-center justify-center text-sm font-bold text-zinc-300">
                        B
                    </button>
                </div>
            </header>

            <div class="flex-1 overflow-y-auto p-8">

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                    <div v-for="stat in stats" :key="stat.name" class="p-6 rounded-xl bg-zinc-900/50 border border-zinc-800">
                        <p class="text-sm font-medium text-zinc-500 mb-1">{{ stat.name }}</p>
                        <div class="flex items-baseline gap-3">
                            <h3 class="text-2xl font-bold text-zinc-100">{{ stat.value }}</h3>
                            <span
                                :class="[
                                    'text-xs font-semibold px-2 py-0.5 rounded-full',
                                    stat.trend === 'up' ? 'text-emerald-400 bg-emerald-400/10' :
                                    stat.trend === 'down' ? 'text-rose-400 bg-rose-400/10' :
                                    'text-zinc-400 bg-zinc-400/10'
                                ]"
                            >
                                {{ stat.change }}
                            </span>
                        </div>
                    </div>
                </div>

                <div class="rounded-xl bg-zinc-900/50 border border-zinc-800 overflow-hidden">
                    <div class="px-6 py-5 border-b border-zinc-800">
                        <h3 class="text-base font-semibold text-zinc-100">Recent Users</h3>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="border-b border-zinc-800 bg-zinc-900/30">
                                    <th class="px-6 py-3 text-xs font-medium text-zinc-500 uppercase">Name</th>
                                    <th class="px-6 py-3 text-xs font-medium text-zinc-500 uppercase">Role</th>
                                    <th class="px-6 py-3 text-xs font-medium text-zinc-500 uppercase">Status</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-zinc-800">
                                <tr v-for="user in recentUsers" :key="user.id" class="hover:bg-zinc-800/20 transition-colors">
                                    <td class="px-6 py-4">
                                        <div class="text-sm font-medium text-zinc-200">{{ user.name }}</div>
                                        <div class="text-xs text-zinc-500">{{ user.email }}</div>
                                    </td>
                                    <td class="px-6 py-4 text-sm text-zinc-400">{{ user.role }}</td>
                                    <td class="px-6 py-4">
                                        <span class="inline-flex items-center gap-1.5 px-2 py-1 text-xs font-medium rounded-md"
                                            :class="user.status === 'Active' ? 'text-emerald-400 bg-emerald-400/10' : 'text-zinc-400 bg-zinc-500/10'">
                                            <span class="w-1.5 h-1.5 rounded-full" :class="user.status === 'Active' ? 'bg-emerald-400' : 'bg-zinc-500'"></span>
                                            {{ user.status }}
                                        </span>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>

            </div>
        </main>

    </div>
</template>
