<template>
    <BannerAdm/>


    <h1>Gerenciamento de Pedidos: </h1>
    <div class="container-principal">

        <div class="pedidos" v-for="acai in acais" :key="acai.id">

            <div class="id">
                <p>Id: {{ acai.id }}</p>
            </div>

            <div class="nome">
                <p>Nome: {{ acai.nome }}</p>
            </div>

            <div class="tamanho">
                <p>Tamanho:</p>
                <p>{{ acai.tamanho_escolhido }}</p>
            </div>

            <div class="listas">
                <div class="frutas">
                    <label
                    >Frutas: </label>
                    <ul>
                        <li v-for="(fruta, index) in acai.frutas_escolhidas" :key="index"> {{ fruta }}  </li>
                    </ul>
                </div>
                <div class="caldas">
                    <label
                    >Caldas</label>
                    <ul>
                        <li v-for="(calda, index ) in acai.caldas_escolhidas" :key="index"> {{ calda }} </li>
                    </ul>
                </div>
                <div class="adicionais">
                    <label
                    >Adicionais</label>
                    <ul>
                        <li v-for="(adicional, index) in acai.adicionais_escolhidos" :key="index" > {{ adicional }}</li>
                    </ul>
                </div>
            </div>

            <div class="adm">

                <select name="" id="">
                    <option value="">Solicitado</option>
                    <option value="">Em Preparação</option>
                    <option value="">Finalizado</option>
                </select>

                <button class="remocao" @click="deletarPedido(acai.id)">
                    <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor" class="bi bi-x-octagon" viewBox="0 0 16 16">
                        <path d="M4.54.146A.5.5 0 0 1 4.893 0h6.214a.5.5 0 0 1 .353.146l4.394 4.394a.5.5 0 0 1 .146.353v6.214a.5.5 0 0 1-.146.353l-4.394 4.394a.5.5 0 0 1-.353.146H4.893a.5.5 0 0 1-.353-.146L.146 11.46A.5.5 0 0 1 0 11.107V4.893a.5.5 0 0 1 .146-.353zM5.1 1 1 5.1v5.8L5.1 15h5.8l4.1-4.1V5.1L10.9 1z"/>
                        <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708"/>
                      </svg>
                      <p>Remover Pedido</p>
                </button>

            </div>

        </div>
    </div>
  </template>
  
  <script>
  import BannerAdm from '@/components/BannerAdm.vue';
 
  
  export default {
    name: 'Pedidos',
    components: {
      BannerAdm,
    },
    data () {
        return {
            acais : null,
            acai_id : null,
            status : null,
        }
    },

    methods: {
        async resgatarPedidos() {
            const req = await fetch("http://localhost:3000/açais");
            const data = await req.json();

            this.acais = data;

            console.log(data);
        },

        async deletarPedido(id) {
            // console.log(id);

            const req = await fetch(`http://localhost:3000/açais/${id}`, {
                method : "DELETE"
            });
            
            const res = await req.json();

            this.resgatarPedidos();

        }
        
    },

    mounted() {
        this.resgatarPedidos();
    },
  }
  </script>

  <style scoped>

  .id, .nome, .tamanho {
    display: flex;
  }

  h1{
    text-align: center;
    padding: 1rem;
  }

  .container-principal {
    display: flex;
    justify-content: center;
    text-align: center;
    align-items: center;
    flex-wrap: wrap;
  }

  .pedidos {
    display: inline-block;
    text-align: center;
    align-items: center;
    border: 0.2rem solid #771349;
    padding: 1rem;
    width: 60rem;
    border-radius: 5rem;
    padding: 2rem;
    margin: 2rem;
    height: 16rem;
    min-width: 50rem;
  }


  .frutas, .caldas, .adicionais {
    display: flex;
    align-items: center;
    margin: 1rem;
    border: 0.2rem solid #771349;
    padding: 1rem;
    border-radius: 1rem;
  }

  .listas {
    display: flex;
    margin: 1rem;
    justify-content: center;
  }

  ul, li {
    margin-left: 2rem;
  }

  select {
    height: 3rem;
    width: 9rem;
    border-radius: 1rem;
  }

  option {
    padding: 2rem;
    text-align: center;
  }

  label {
    font-size: 1.2rem;
    font-weight: 700;
  }

  .adm {
    display: flex;
    justify-content: space-between;
  }

 .adm, .remocao {
    display: flex;
  }

  .remocao {
    text-align: center;
    align-items: center;
    max-height: 3rem;
  }

  button {
    padding: 0.5rem;
    border-radius: 1rem;
    cursor: pointer;
    transition: 1s;
    align-items: center;
    
  }

  button p {
    margin-left: 0.5rem;
  }

  button:hover {
    background-color: rgb(255, 158, 158);
    color: red;
  }

  </style>