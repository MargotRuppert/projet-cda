<template>
    <nav>
        <div class="navbar bg-orange shadow-sm text-color-header font-titan">
            <div class="navbar-start">
                <div class="dropdown">
                    <div tabindex="0" role="button" class="btn btn-ghost lg:hidden">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24"
                            stroke="black">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M4 6h16M4 12h8m-8 6h16" />
                        </svg>
                    </div>
                    <ul tabindex="0" class="menu menu-sm dropdown-content bg-orange rounded-box z-1 mt-3 w-52 shadow text-lg">
                        <NuxtLink to="/" class="link link-hover"> Accueil</NuxtLink>
                        <NuxtLink to="/calendar" class="link link-hover"> Agenda</NuxtLink>
                        <NuxtLink to="/map" class="link link-hover"> Carte</NuxtLink>
                        <NuxtLink to="/search" class="link link-hover"> Rechercher</NuxtLink>
                        <NuxtLink to="/dashboard" class="link link-hover"> Dashboard</NuxtLink>
                        <NuxtLink to="/profile" class="link link-hover"> Profil</NuxtLink>
                    </ul>
                </div>
                <a href="/"><img src="../assets/logo-transparent-png.png" alt="logo site accueil"
                        class="h-25 w-30"></a>

            </div>
            <div class="navbar hidden lg:flex ml-[100px]">
                <ul class="menu menu-horizontal text-lg">
                        <NuxtLink to="/" class="link link-hover mr-3"> Accueil</NuxtLink>
                        <NuxtLink to="/calendar" class="link link-hover mr-3"> Agenda</NuxtLink>
                        <NuxtLink to="/map" class="link link-hover mr-3"> Carte</NuxtLink>
                        <NuxtLink to="/search" class="link link-hover mr-3"> Rechercher</NuxtLink>
                        <NuxtLink to="/dashboard" class="link link-hover mr-3"> Dashboard</NuxtLink>
                        <NuxtLink to="/profile" class="link link-hover mr-3"> Profil</NuxtLink>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script setup>

</script>