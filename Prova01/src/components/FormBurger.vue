<template>
    <div>
        <Message :msg="msg" v-show="msg"/>
        <form class="burgerForm" @submit="createBurger">
            <div class="inputContainer">
                <label for="nome">Nome do Cliente:</label>
                <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite seu nome aqui...">
            </div>
            <div class="inputContainer">
                <label for="pao">Escolha o Pão:</label>
                <select name="pao" id="pao" v-model="pao">
                <option value="">Selecione seu Pão!</option>
                <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
                </select>
            </div>
            <div class="inputContainer">
                <label for="carne">Escolha a Carne:</label>
                <select name="carne" id="carne" v-model="carne">
                <option value="">Selecione sua Carne!</option>
                <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                </select>
            </div>
            <div class="inputContainer" id="optionsContainer" >
                <label for="opcionais">Selecione os opcionais:</label>
                    <div class="checkBoxContainer" v-for="opcional in opcionaisdata" :key="opcional.id" >
                        <input type="checkbox" id="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                        <span>{{ opcional.tipo }}</span>
                    </div>    
            </div>
            <div class="inputContainer">
                <input type="submit" class="submitBtn" value="Criar meu Burguer">
            </div>

        </form>
    </div>
</template>

<script>
import { stringify } from 'postcss';
import Message from './Message.vue'

    export default
    {
    name: "FormBurger",
    data() {
        return {
            paes: null,
            carnes: null,
            opcionaisdata: null,
            nome: null,
            pao: null,
            carne: null,
            opcionais: [],
            msg: null,
        };
    },
    methods: {
        async getIngredients()
        {
            const req = await fetch("http://localhost:3000/ingredientes");
            const data = await req.json();
            this.paes = data.paes;
            this.carnes = data.carnes;
            this.opcionaisdata = data.opcionais;
        },
        async createBurger(e)
        {
            e.preventDefault()

           const data =
           {
             nome: this.nome,
             pao: this.pao,
             carne: this.carne,
             opcionais: Array.from(this.opcionais),
             status: "Solicitado"
           }

            const dataJson = JSON.stringify(data)

            const req = await fetch("http://localhost:3000/burgers", 
            {
                method: "POST",
                headers: { "Content-Type" : "application/json" },
                body: dataJson,
            })

            const res = await req.json()

            this.msg = `Pedido Nº${res.id} realizado com Sucesso!`

            setTimeout(()=> this.msg = "", 5000)

            this.nome = ""
            this.pao = ""
            this.carne = ""
            this.opcionais = []
        }
    },
    mounted() {
        this.getIngredients();
    },
    components:
    { 
        Message, 
    }
}
</script>

<style scoped>
    .burgerForm
    {
        width: 45vw;
        margin: 15px auto;
    }
    .inputContainer
    {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }
    label
    {
        font-weight: bold;   
        margin-bottom: 15px;
        color: #333;
        padding: 5px 10px;
        border-left: 4px solid #FCBA03;
        font-size: 1.25rem;
    }
    input, 
    select
    {
        padding: 5px 10px;
        border:2px solid #121212;
        border-radius: 10px;
        background-color: #12121219;
    }
    input:hover, 
    select:hover, 
    select:focus
    {
        border:2px solid #FCBA03;

    }
    #checkbox
    {
        cursor: pointer;
        min-width: 20px;
        min-height: 20px;
    }
    #optionsContainer
    {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;

    }
    #optionsContainer label
    {
        width: 100%;
        font-size: 1.25rem;

    }
    .checkBoxContainer
    {
        display: flex;
        align-items: flex-start;
        width: 30%;
        margin-bottom: 20px;
        margin-left: auto;
        margin-right: auto;
    }
    .checkBoxContainer span
    {
        margin-left: 6px;
        font-weight: 500;
        font-size: 1.2rem;
    }
    .submitBtn
    {
        background-color: #121212;
        color: #FCBA03;
        font-weight: bold;
        border: 2px solid #121212;
        border-radius: 10px;
        padding: 15px 30px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: 0.5s;
    }
    .submitBtn:hover
    {
        background-color: transparent;
        color: #121212;
        box-shadow: 10px 10px 8px rgba(0, 0, 0, 0.2),
                    inset -5px -5px 8px rgba(0, 0, 0, 0.15) ;
    }
    @media (max-width: 560px)
    {
        .checkBoxContainer
        {
            margin-left: 15px;
            margin-right: 15px;
        }
        .burgerForm
        {
            width: 90%;
            margin: 40px auto;
        }
        #optionsContainer label, label
        {
            font-size: 1.25rem;
        }
        .checkBoxContainer span
        {
            font-weight: 500;
            font-size: 1.2rem;
        }
    }

</style>