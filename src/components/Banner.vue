<template>
    <div class="banner-container">
        <div class="banner-text-container">
            <div class="banner-text">
                Monte o seu açaí !
            </div>!
        </div>
    </div>
</template>

<script>
export default {
    name: 'Banner'
}
</script>


<style scoped>


.banner-container{
    width: 100vw;
    height: 86dvh;
    background-image: url('/public/img/banner3.jpg');
    background-position: 500px -150px;
    display: flex;
    align-items: center;
}

.banner-text{
    font-size: 8rem;
    color: white;
}

</style>