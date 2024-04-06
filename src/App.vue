<script setup>
  import { ref } from "vue";
  const dolares = ref(null)

  function loadData() {
    fetch('https://dolarapi.com/v1/dolares')
    .then(res => res.json())
    .then(data => dolares.value = data)
  }
    
  loadData()

</script>

<template>
  <div class="dolares">
        <div v-for="dolar in dolares" class="dolar">
            <p class="dolar_nombre">Dolar {{dolar.nombre}}</p>
            <div class="compraventa">
                <div class="compra">
                    <p>Compra</p>
                    <p class="moneda">${{dolar.compra}}</p>
                </div>
                <div class="compra">
                    <p>Venta</p>
                    <p class="moneda">${{dolar.venta}}</p>
                </div>
            </div>
        </div>
    </div>
</template>


<style >
    .dolares {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
    .dolar {
        width: 45%;
        display: flex;
        flex-wrap: wrap;
        border-style: solid;
        border-width: 1px;
        border-radius: 10px;
        margin: 5px;
        
    }
    .dolar_nombre{
        width: 100%;
        text-align: center;
        font-weight: bold;
    }
    .compraventa{
        width: 100%;
        display: flex;
        justify-content: center;
        
    }

    .compra{
        margin: 15px;
        margin-top: 0;
    }
    .moneda {
        color: #85BB65;
    }
</style>
