<script setup>
    import { onMounted, reactive, ref } from 'vue';

    defineProps([
        "personagem"
    ])

</script>

<template>
    <div class="col">
        <div class="card mb-3 border-0 shadow">
            <div class="row g-0">
                <div class="col-md-5">
                    <img :src="personagem.image" class="img-fluid rounded w-100 h-100" :alt="personagem.name" style="object-fit: cover;">
                </div>
                <div class="col-md-7">
                    <div class="card-body">
                        <div class="card-title fw-bold">
                            <h5 class="fs-2">{{ personagem.name }}</h5>
                            <span
                                :class="{ 'text-bg-success': personagem.status == 'Alive', 'text-bg-danger': personagem.status == 'Dead', 'text-bg-secondary': personagem.status == 'unknown' }"
                                class="badge rounded-pill">{{ personagem.status }}</span>
                        </div>
                        <div class="card-text mt-4">
                            <div class="row">
                                <div class="col">
                                    <div class="specie mb-1">
                                        <strong>Espécie:</strong>
                                        <div>{{ personagem.species }}</div>
                                    </div>
                                    <div class="gender mb-1">
                                        <strong>Gênero:</strong>
                                        <div>{{ personagem.gender }}</div>
                                    </div>
                                    <div class="location mb-1">
                                        <strong>Localização:</strong>
                                        <div>{{ personagem.location.name }}</div>
                                    </div>
                                </div>
                                <div class="col">
                                    <div class="origin mb-1">
                                        <strong>Origem:</strong>
                                        <div>{{ personagem.origin.name }}</div>
                                    </div>
                                    <div class="totalEp mb-1">
                                        <strong>Total episódios:</strong>
                                        <div>{{ personagem.episode.length }} episódio(s)</div>
                                    </div>
                                </div>
                            </div>

                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>