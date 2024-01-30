<template>
    <div class="banner-container">
        <div class="banner-text-container">

            <div class="banner-text">
                Página Administrativa 
            </div>

            <div class="banner-text">
                AçaíMaster Distribuidora
            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'BannerAdm'
}
</script>


<style scoped>


.banner-container{
    width: 100vw;
    height: 86dvh;
    background-image: url('/public/img/banner3.jpg');
    background-position: 700px -150px;
    display: flex;
    align-items: center;
}

.banner-text{
    font-size: 8rem;
    color: white;
}

</style>