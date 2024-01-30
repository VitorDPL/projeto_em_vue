<template>
  <Banner/>

  
  
  <div id="div-pai-de-todas">

      <div class="quem-somos-container">
        <div>
          <article>
            <h2>Quem Somos?</h2>

            <p>
              Somos a AçaíMaster Distribuidora, uma empresa comprometida em levar o melhor do açaí diretamente para você! <br>  Nosso objetivo é proporcionar momentos de sabor e energia, promovendo um estilo de vida saudável e delicioso.
            </p>


            <h2>Compromisso com a Qualidade</h2>
            <p>
              Nossos produtos passam por rigorosos controles de qualidade, desde a colheita até a embalagem. <br>  Trabalhamos em parceria com fornecedores confiáveis para garantir a frescura e a autenticidade de cada lote de açaí.
            </p>

            <h2>Por que Escolher a AçaíMaster?</h2>
            <ul>
              <li>Excelência em Qualidade: Comprometidos em fornecer açaí da mais alta qualidade.</li>
              <li>Atendimento Personalizado: Nossa equipe está sempre pronta para atender às suas necessidades.</li>
              <li>Entrega Rápida e Eficiente: Garantimos que seu pedido chegue fresco e pontualmente.</li>
            </ul>

            <h2>Contato</h2>
            <p>Quer experimentar o melhor do açaí? Entre em contato conosco para fazer seu pedido ou agendar uma visita ao nosso showroom.  <br> Estamos ansiosos para colaborar com você na promoção de um estilo de vida mais saudável e delicioso!</p>

            <h2>AçaíMaster Distribuidora</h2>
            <p>
              <ul>
                <li>Telefone: (32) 99947-7844</li>
                <li>Email: vitorlippi8@hotmail.com</li>
              </ul>
              
            </p>

            <h2>Transforme seus dias com AçaíMaster - Sabor e Saúde em um Único Pote!</h2>
          </article>
        </div>
      </div>

      <Confirmacao v-show="confirmacao"/>

      <form action="" @submit="solicitarPedido">
        <div class="container">
          <div class="separador">
      
            <div class="texto">
              <h1>Veja as opções:</h1>
            </div>
      
            <div class="info">
              <label for="">Insira o seu nome:</label>
              <input type="text" id="info-input" placeholder="Digite o seu nome aqui" v-model="nome" required="true">
            </div>
            <div class="container-inputs">
              <label for="ml">Escolha o tamanho do copo:</label>
              <select name="ml" class="container-select" id="#select-ml" v-model="tamanho_escolhido" required="true"> 
                <option v-for="tamanho in tamanhos" :key="tamanho.id" :value="tamanho.tipo"> {{ tamanho.tipo }}</option>
              </select>
            </div>
            <div class="container-opcionais">
             <div class="label-border">
               <div class="label">
                 <label for="frutas">Frutas</label>
               </div>
             </div>
              <div class="frutas-opcionais-inputs">
      
                <div class="opcionais-itens" v-for="fruta in frutas" :key="fruta.id" :value="fruta.tipo">
                  <label :for="fruta.tipo" > {{ fruta.tipo }} </label>
                  <input v-model="frutas_escolhidas" :value="fruta.tipo" type="checkbox" class="input">
                </div>
                
              </div>
            </div>
            <div class="container-opcionais">
              <div class="label-border">
                <div class="label">
                  Caldas
                </div>
              </div>
              <div class="frutas-opcionais-inputs">
      
      
                <div class="opcionais-itens" v-for="calda in caldas" :key="calda.id" :value="calda.tipo">
                  <label> {{ calda.tipo }} </label>
                  <input v-model="caldas_escolhidas" :value="calda.tipo" type="checkbox" class="input">
                </div>
      
              </div>
            </div>
      
            <div class="container-opcionais">
              <div class="label-border">
                <div class="label">
                  Adicionais
                </div>
              </div>
              <div class="frutas-opcionais-inputs">
      
                <div class="opcionais-itens" v-for="adicional in adicionais" :key="adicional.id">
                  <label>{{ adicional.tipo }}</label>
                  <input v-model="adicionais_escolhidos" :value="adicional.tipo" name="adicionais" type="checkbox" class="input">
                </div>

              </div>
            </div>

            <div class="button-div">
              <div id="valor">
                <label> Valor Único: </label>
                <p>R$ 25,00</p>
              </div>
              <button type="submit" @click="ativar">Solicitar Pedido</button>
            </div>
      
          </div>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  import Banner from '@/components/Banner.vue';
  import Confirmacao from './Confirmacao.vue';

  export default {
    name: 'FormAçai',
    components: {
      Banner,
      Confirmacao,
    },
    data () {
      return {
        tamanhos : null,
        frutas : null,
        caldas : null,
        adicionais : null,
        
        nome : null,
        tamanho_escolhido : null,
        frutas_escolhidas : [],
        caldas_escolhidas : [],
        adicionais_escolhidos : [],

        confirmacao : false,

        status : "Solicitado",
      }
    },
  
    methods: {
      
      async getOptions() {
        const req = await fetch('http://localhost:3000/ingredientes');
        const data = await req.json();
  
        this.tamanhos = data.tamanhos;
        this.frutas = data.frutas;
        this.caldas = data.caldas;
        this.adicionais = data.adicionais;
  
        console.log(data);
      },

      async solicitarPedido(e) {
        e.preventDefault();
        
        const data= { 
          nome: this.nome,
          tamanho_escolhido : this.tamanho_escolhido,
          frutas_escolhidas : Array.from(this.frutas_escolhidas),
          caldas_escolhidas : Array.from(this.caldas_escolhidas),
          adicionais_escolhidos : Array.from(this.adicionais_escolhidos),
        }

        const dataJson = JSON.stringify(data);

        const req = await fetch("http://localhost:3000/açais", {
          method: "POST",
          headers : {"Content-Type" : "application/json"},
          body: dataJson
        });

        const res = await req.json();

        this.confirmacao = true;


        const tempoDuracao = 5000;

        setTimeout(() => {
        this.confirmacao = false;}, tempoDuracao);

        this.nome = "",
        this.tamanho_escolhido = "",
        this.frutas_escolhidas = "",
        this.caldas_escolhidas = "",
        this.adicionais_escolhidos = ""
      },

    },
  
    mounted() {
      this.getOptions();
    }
  
    
  }
  </script>


  
  <style scoped>

  #div-pai-de-todas{
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .container {
    text-align: center;
    color: #771349;
  }

  .quem-somos-container {
    margin: 2rem;
    display: flex;
  }

  form {
    width: 50%;
  }

  .quem-somos-container p, ul, li{
    margin: 1rem;
    font-size: 1.2rem;
  }
  
  h1 {
    display: inline-block;
    text-align: center;
    padding: 2rem;
    border-bottom: 0.2rem solid #771349;
  }

  h2 {
    font-size: 1.2rem;
    color: #771349;
  }


  .info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    font-weight: 700;
    margin-bottom: 1rem;
    padding: 1rem;
  }
  
  
  
  .separador{
    margin: 2%;
    display: inline-block;
    border: 0.3rem solid #771349;
    border-radius: 2rem;
  }
  
  .container-inputs {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    font-weight: 700;
    margin: 0rem 2.5rem;
  }
  
  #info-input {
    width: 30.5rem;
    margin: 1rem 1rem 1rem 2.5rem;
  }
  
  .container-select {
    margin: 1rem;
  }
  
  .label {
    font-weight: 700;
    margin: 1rem;
  }
  
  .label-border {
    border-top: 0.2rem solid #771349;
    margin-bottom: 1rem;
  }
  
  .frutas-opcionais-inputs {
    display: flex;
    margin: 1rem;
    
  }
  
  .opcionais-itens {
    display: flex;
    margin: 0.5rem;
    width: 8rem;
    text-align: center;
    align-items: center;
  }
  
  .input {
    margin: 0rem 0.2rem;
  }
  
  input, select, label, button {
    padding: 0.4rem;
    font-weight: 700;
    border-radius: 0.5rem;
    text-align: center;
    min-height: 1.2rem;
    min-width: 1.2rem;
  }
  
  label, input {
    font-size: 1rem;
  }
  
  .button-div {
    border-top: 0.2rem solid black;
    margin-bottom: 1rem;
    justify-content: space-between;
    align-items: center;
  }
  
  button {
    font-size: 1.5rem;
    font-weight: 700;
    margin-top: 1rem;
    padding: 1rem 2rem;
    border-radius: 0.5rem;
    cursor: pointer;
    transition: 1s;
    background-color: #fcd8fc;

  }
  
  button:hover {
    background-color: #771349;
    color: white;
  }

  #valor {
    display: inline-block;
    align-items: center;
    margin-right: 5rem;
  }

  #valor label, p {
    display: inline;
    font-weight: 700;
    font-size: 1.3rem;
  
  }

  </style>
