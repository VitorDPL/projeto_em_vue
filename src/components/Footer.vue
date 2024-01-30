<template>
    <main>
        <!-- Seu conteúdo vai aqui -->
    </main>

    <footer id="footer-id">
        AçaíMaster Distribuidora <span>&copy;</span> 2024
    </footer>
</template>

<script>
export default {
    name: 'Footer',
}
</script>

<style scoped>
main {
    min-height: 3rem; /* Subtrai a altura do footer para garantir que o footer não sobreponha o conteúdo */
}

footer {
    font-size: 2rem;
    display: flex;
    height: 15rem;
    background-color: #771349;
    color: white;
    justify-content: center;
    align-items: center;
}
span {
    margin: 0rem 1rem;
}
</style>
