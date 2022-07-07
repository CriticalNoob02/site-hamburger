<template>
    <div id="burgerTable">
        <div>
            <div id="burgerTableHeader">
                <div class="orderId">#</div>
                <div>Nome:</div>
                <div>Pão:</div>
                <div>Carne:</div>
                <div>Opcionais:</div>
                <div>Ações:</div>
            </div>
        </div>
        <div>
            <div id="burgerTableRows">
                <div class="burgerTableRow">
                    <div class="orderNumber">1</div>
                    <div>Jonas</div>
                    <div>3 Queijos</div>
                    <div>Picanha</div>
                    <div>
                        <ul>
                            <li>Tomate</li>
                            <li>Cheddart</li>
                        </ul>
                    </div>
                    <div>
                        <select name="status" class="status">
                            <option value="">Selecione o Status do Lanche:</option>
                        </select>
                        <button class="deleteBtn">Cancelar</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default
    {
        name: "Dashboard"
    }
</script>

<style scoped>

</style>