<template>
    <div class="tableContainer">
        <Message :msg="msg" v-show="msg"/>
        <table class="table">
            <thead>
                <th>#</th>
                <th>Nome:</th>
                <th>Pão:</th>
                <th>Carne:</th>
                <th>Opcionais:</th>
                <th>Ações:</th>
            </thead>
            <tbody v-for="burger in burgers" :key="burger.id">
                <tr >
                    <td data-label="#">{{burger.id}}</td>
                    <td data-label="Nome:">{{burger.nome}}</td>
                    <td data-label="Pão:">{{burger.pao}}</td>
                    <td data-label="Carne:">{{burger.carne}}</td>
                    <td data-label="Opcionais:">
                        <li v-for="(opcional, index) in burger.opcionais" :key="index">
                            <ul>{{ opcional }}</ul>
                        </li>
                    </td>
                    <td data-label="Ações:">
                        <select name="status" class="status" @change="updateBurger($event, burger.id)">
                            <option value="">Selecione:</option>
                            <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo">{{ s.tipo }}</option>
                        </select>
                        <button class="deleteBtn" @click="deleteBurger(burger.id)">Cancelar</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template> 

<script>
import Message from './Message.vue'

    export default
    {
        name: "Dashboard2",
        data()
        {
            return{
                burgers: null,
                burger_id: null,
                status: [],
                msg: null,
            }
        },
        methods:
        {
            async getPedidos()
            {
                const req = await fetch('http://localhost:3000/burgers')
                const data = await req.json()
                this.burgers = data

                this.getStatus()
            } ,
            async getStatus()
            {
                const req = await fetch("http://localhost:3000/status")
                const data = await req.json()
                this.status = data
            },
            async deleteBurger(id)
            {
                const req = await fetch(`http://localhost:3000/burgers/${id}`, { 
                    method: "DELETE"
                    })
                const res = await req.json()    

                this.msg = `Seu pedido acaba de ser removido!`

                setTimeout(()=> this.msg = "", 3000)

                this.getPedidos()

            },
            async updateBurger(event, id)
            {
                const option = event.target.value
                const dataJson = JSON.stringify({status: option})
                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                    method: "PATCH",
                    headers: { "Content-Type" : "application/json" },
                    body: dataJson
                });

                const res = await req.json()

                this.msg = `O status do pedido Nº${res.id} foi alterado para ${res.status}! `

                setTimeout(()=> this.msg = "", 3000)
            }

        },
        mounted()
        {
            this.getPedidos()
        },
        components:
        {
            Message, 
        }
    }
</script>

<style scoped>
    .tableContainer
    {
        max-width: 1200px;
        min-height: 800px;
        margin: 0 auto;
    }
    .table
    {
        width: 100%;
        border-collapse: collapse;
    }
    .table thead
    {

        border-bottom: 3px solid #121212;

    }
    .table thead th
    {
        font-size: 1.1rem;
        font-weight: 600;
        letter-spacing: 0.35px;
        padding: 12px;
        border-right: 1px solid #12121227;
        border-left: 1px solid #12121227;
    }
    .table tbody
    {
        border-bottom: 1px solid #12121227;
    }
    .table tbody tr td
    {
        font-size: 0.875rem;
        letter-spacing: 0.35px;
        padding: 8px;
        text-align: center;
    }
    .table tbody tr td li
    {
        list-style-type:none;
    }
    select
    {
        margin-right: 12px;
        padding: 5px 10px;
        border:2px solid #121212;
        border-radius: 10px;
        background-color: #12121219;
    }
    select:hover, 
    select:focus
    {
        border:2px solid #FCBA03;

    }
    .deleteBtn
    {
        background-color: #121212;
        color: #FCBA03;
        font-weight: 600;
        border: 2px solid #121212;
        border-radius: 10px;
        padding: 8px 8px;
        font-size: 14px;
        margin: 0 auto;
        cursor: pointer;
        transition: 0.5s;
    }
    .deleteBtn:hover
    {
        background-color: transparent;
        color: #121212;
        box-shadow: 10px 10px 8px rgba(0, 0, 0, 0.2),
                    inset -5px -5px 8px rgba(0, 0, 0, 0.15) ;
    }
    @media (max-width: 725px)
    {
        .table thead
        {
            display: none;
        }
        .table,
        .table tbody,
        .table tr,
        .table td
        {
            display: block;
            width: 100%;
        }
        .table tr
        {
            margin-bottom: 15px;
        }
        .table tbody tr td
        {
            text-align: end;
            padding-left: 50%;
            position: relative;
            border-bottom: 1px solid #12121227;
            border-left: 3px solid #FCBA03;
        }
        .table td::before
        {
            content: attr(data-label);
            position: absolute;
            left: 0;
            width: 50%;
            padding-left: 15px;
            font-size: 1.1rem;
            font-weight: 600;
            letter-spacing: 0.35px;
            text-align: left;
        }
    }
    @media (max-width: 463.20px)
    {
        select
        {
            margin-right: 0px;
            margin-bottom: 5px;
        }
    }
</style>



