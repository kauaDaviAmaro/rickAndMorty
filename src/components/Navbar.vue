<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <nav class="navbar navbar-expand-lg bg-dark" data-bs-theme="dark">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Rick & Morty</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <RouterLink class="nav-link" aria-current="page" to="/">Inicio</RouterLink>
                    </li>
                    <li class="nav-item">
                        <RouterLink class="nav-link" aria-current="page" to="/about">Sobre</RouterLink>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>