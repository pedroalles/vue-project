<template>

    <div class="conversor">

        <h3>{{moedaA}} to {{moedaB}}</h3>

        <input class="inputclass" type="text" v-model="moedaA_value" v-bind:placeholder="moedaA">
        
        <div class="btcenter">
            <input type="button" value="Converter" v-on:click="converter">
        </div>

        <h2 >{{moedaB_value}}</h2>

    </div>

</template>


<script>

export default {
    name: "Conversor",
    props: ["moedaA","moedaB"],
    data(){
        return{
            moedaA_value : "",
            moedaB_value : 0
        };
    },
    methods: {
        converter()
        {
            let de_para = this.moedaA +"_"+ this.moedaB;
            let apikey = "1feee5522525b5536695"
            let url = "https://free.currconv.com/api/v7/convert?q=" + de_para + "&compact=ultra&apiKey=" + apikey

            fetch(url).then(res=>{return res.json();})
                      .then(json=>{

                          let cotacao = json[de_para];
                          this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2);
                      })
        }
    }
};

</script>

<style scoped>

.conversor{
    padding: 10px;
    max-width: 160px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.4);
    border-radius:20px;
    text-align: center;
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