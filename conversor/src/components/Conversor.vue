<template>

    <div class="conversor">

        <h3>{{moedaA}} to {{moedaB}}</h3>

        <select v-model="moedaA">
            <option v-for="item in currencys" v-bind:key="item">{{ item }}</option>
        </select>

        <input class="inputclass" @click="trigger" type="text" v-model="moedaA_value" v-bind:placeholder="moedaA" ref="fileInput" >

        <select v-model="moedaB">
            <option v-for="item in currencys" v-bind:key="item">{{ item }}</option>
        </select>
        
        <div class="btcenter">
            <input type="button" value="Convert" v-on:click="converter">
        </div>

        <h2 >{{result}}</h2>

    </div>

</template>


<script>

export default {
    name: "Conversor",
    props: ["moedaA","moedaB"],
    data(){
        return{
            moedaA_value : "",
            moedaB_value : "",
            result : 0,
            valA : 0,
            currencys: ['BRL', 'CAD','CHF', 'EUR','GBP', 'JPY','NZD', 'USD', 'UYU']
        };
    },
    methods: {
        trigger(){
            this.moedaA_value = "";
        },
        converter()
        {
            let de_para = this.moedaA +"_"+ this.moedaB;
            let apikey = "1feee5522525b5536695"
            let url = "https://free.currconv.com/api/v7/convert?q=" + de_para + "&compact=ultra&apiKey=" + apikey
            

            fetch(url).then(res=>{return res.json();})
                      .then(json=>{
                          console.log(json);
                          let cotacao = json[de_para];
                          this.result = (cotacao * parseFloat(this.moedaA_value)).toFixed(2);
                      })
        
            
            this.resertInput();
        }
    }
};

</script>

<style scoped>

.conversor{
    padding: 10px;
    max-width: 300px;
    box-shadow: 10px 10px 20px 0px rgba(0, 0, 0, 0.4);
    border-radius:30px 10px 30px 10px;
    text-align: center;
    background-color: #b6d40ba9;
    border: 5px solid;
}
.btcenter{
    /* text-align: center; */
    padding-top: 5px;
}
.inputclass{
    text-align: center;
    width: 60%;
}

</style>