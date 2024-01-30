<template>

    <div id="div_pai">
        <div class="div_background"></div>
        <div class="div_sec">
        
            <div class="banner-secunda">
                <img src="img/banner-secundario.png" alt="aaaaa">
            </div>
        
            <div class="textos">
                <h1>Obrigado pelo pedido !</h1>
                <h2>Em breve o açaí chegará em sua residência.</h2>
            </div>
        
        </div>
    </div>
</template>

<script>
export default {
    name : 'Confirmacao',
}
</script>

<style scoped>
#div_pai {
    justify-content: center;
    position: absolute;
}

.div_background {
    background-color: #fcd8fc;
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: 0;
    opacity: 0.4;
}

.div_sec {
    display: inline-block;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 1rem;
    position: relative;
    z-index: 999;
    padding: 3rem;
    border-radius: 6rem;
    background-color: #771349;
}

.div_sec img {
    border-radius: 10rem;
    z-index: 1;
    opacity: 1;
}

.textos {
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    margin: 2rem;
}


</style>