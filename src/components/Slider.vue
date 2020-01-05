<template lang="pug">
    .slider
        .main_box
            .main_box__box_cell
                .box_cell__box_title_main
                    .box_cell__box_title_main--text Wybierz
                .box_cell__box_valor
                    .box_cell__box_valor--text Wartość pożyczki
                        span.valor#amount  1200,00 zł
                .box_cell__box_section
                    .box_cell__box_section--minmax  600
                    .box_cell__box_section--minmax  3000
                .box_cell__box_slider
                        
                .box_cell__box_title 
                    .parameters 
                        span#installment
                .box_cell__box_parcels
                    .box_cell__box_parcels--days
                        
                .box_cell__title_parcela
                    #installment Valor de parcela: 
                        span.valor#rata 
        .main
            .title
                | Hello Ania
            button(@click="click")

    
</template>
<script>
import loan from "@/assets/json/loan.json"

export default {
    data() {
        return {

        }
    },
    methods: {
        click() {
            console.log(loan.data)
        }
    }
    
}
</script>

<style scoped>
.main_box {
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  width: 38%;
  background-color: #da2228;
  color: white;
  border-radius: 10px;
  font-family: "Oswald", sans-serif;
  font-weight: 200;
  font-size: 20px;
}
.main_box__box_cell {
  width: 100%;
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  justify-content: center;
  flex-direction: column;
  padding: 15px;
}
.box_cell__box_title_main {
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  justify-content: center;
  align-items: center;
}
.box_cell__box_section--minmax {
  font-size: 14px;
  line-height: 16px;
  margin: 0 20px 0 20px;
}
.box_cell__box_parcels {
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  justify-content: space-between;
  margin-top: 25px;
}
.box_cell__box_parcels--days {
  cursor: pointer;
}

.box_cell__box_title_main,
.box_cell__box_valor {
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  justify-content: flex-start;
  align-items: center;
  padding-bottom: 5px;
}
.box_cell__box_section {
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}
.box_cell__box_slider {
  padding: 30px 0 30px 0;
}
.box_cell__title_parcela {
  width: 50%;
  margin-top: 30px;
}
.valor {
  border-bottom: solid 1px white;
  font-weight: 500;
}
.textInfo {
  width: 45%;
  text-align: justify;
  font-size: 20px;
  font-weight: 600;
  /* font-family: "Roboto"; */
}
.clear {
  height: 50px;
}

</style>

