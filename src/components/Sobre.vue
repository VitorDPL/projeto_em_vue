<template>

    <div id="container-principal">

        <div>
            <img src="/img/eu.png" alt="">
        </div>

        
        <article>

            <div id="div-h1">
                <h1>Sobre mim: </h1>
            </div>
            
            <li>
                Eu me chamo Vitor, tenho 23 anos, nascido na data 18/07/2000.
            </li>

            <li>
                Atualmente, curso Análise e Desenvolvimento de Sistemas no Vianna JR, em Juiz de Fora.
            </li>
            
            <li>
                Tenho como experiência na programação alguns projetos pessoais que fiz para a loja de meus pais, como uma contagem completa de estoque, com inteligência de vendas e trocas integradas.
            </li>
            
            <li>
                É importante deixar fixado que este projeto específico não foi o meu primeiro envolvendo o Vue.JS, mas sim o que eu escolhi para postar.
            </li>

            <li>
                Desde pequeno, sempre tive muita afinidade com a computação em geral.
            </li>

            <li>
                "Fora das telas", tenho experiência com o público. Já trabalhei em comércio e telemarketing.
            </li>

            <h2>
                Formas de contato:
            </h2>
            <ul>
                <li>
                    Telefone (Prefencialmente WhatsApp) : (032) 99947-7844
                </li>
                <li>
                    E-mail: vitorlippi8@hotmail.com
                </li>
                <li>
                    Linkedin: 
                   <a href="https://www.linkedin.com/in/vitor-lippi-4279a0294/" target="__blank">https://www.linkedin.com/in/vitor-lippi-4279a0294/</a>
                </li>
            </ul>

            <h2>
                Qualificações Importantes:
            </h2>

            <ul>
                <li>Tenho EXTREMA facilidade em memorizar detalhes importantes.</li>
                <li>Sempre fui muito focado em alcançar melhorias.</li>
                <li>Atento à críticas.</li>
                <li>Detalhista.</li>
            </ul>

            <h2>Inspiração para o projeto: </h2>

            <p>
                Esse projeto tem como inspiração o canal "Hora de Codar", do YouTube.
            </p>
            
            <p>
                Sempre que posso, tento reproduzir projetos interessantes de outras formas com o intuito de melhorar ainda mais o meu desempenho.
            </p>

        </article>
    </div>

</template>

<script>
export default {
    name: 'Sobre',
    data () {
        return {
            linguagens : ['Python', 'JavaScript', 'C#', 'HTML / CSS'],
        }
    }
}
</script>

<style scoped>

#container-principal {
    display: flex;
    margin: 1rem 0rem 0.9rem 0rem;
    border: 0.2rem solid #771349;
    padding: 1rem;
}

article {
    margin-left: 2rem;
}

h1, h2 {
    text-align: center;
    margin: 1rem 0rem;
}

p, li {
    margin:00.7rem 0rem;
}

</style>