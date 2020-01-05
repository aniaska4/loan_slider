<template lang="pug">
    .slider
        .main_box
            .main_box__box_cell
                .box_cell__box_title_main
                    .box_cell__box_title_main--text Kalkulator raty pożyczki
                .box_cell__box_valor
                    .box_cell__box_valor--text Twoja kwota pożyczki:
                        span.valor#amount  {{slider.value}} zł
                .box_cell__box_section
                    .box_cell__box_section--minmax  600
                    .box_cell__box_section--minmax  3000
                .box_cell__box_slider
                    VueSlideBar(
                          v-model="slider.value"
                          :data="slider.data"
                          :range="slider.range"
                          :processStyle="{ backgroundColor: '#ffffff6e' }"
                          :lineHeight="slider.lineHeight"
                          class="demo-demo" id="slider-1")
                          template(slot="tooltip" style="background-color: #031d4c; border: black;" slot-scope="tooltip")
                            img(src="/image/handle.png" style="background-color: white; margin-top: 10px; border-radius: 7px;")
                .box_cell__box_title 
                    .parameters 
                        span#installment
                .box_cell__box_parcels
                    .box_cell__box_parcels--days
                        
                .box_cell__title_parcela
                    #installment Valor de parcela: 
                        span.valor#rata 
                .box_cell__button
                    button weź pożyczkę
        .main
            .title
                | Hello Ania
            button(@click="click")

    
</template>
<script>
import loan from "@/assets/json/loan.json";
import VueSlideBar from "vue-slide-bar";

export default {
    name: "Slider",
    components: {
        VueSlideBar
    },
    data() {
        return {
        slider: {
            lineHeight: 8,
            value: 300,
            data: [100, 200, 300, 400, 500]
            },
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
.slider {
  display: flex;
  justify-content: center;
  height: 450px;
}
.main_box {
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  width: 40%;
  height: 100%;
  background-color: #5e5e5f;
  border: 2px solid rgb(0, 0, 27);
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
  font-size: 18px;
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
.box_cell__box_title_main{
  margin-bottom: 20px;
  font-size: 30px;
  color: rgb(0, 0, 27);
  font-weight: 600;
  border-bottom: 1px solid rgb(0, 0, 27);
  text-align: center;  
  justify-content: center;
  margin-bottom: 40px;
}
.box_cell__box_valor{
    text-align: start;
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
/* .box_cell__box_slider {
  padding: 30px 0 30px 0;
} */
.box_cell__title_parcela {
  width: 50%;
  margin-top: 30px;
}
.box_cell__button button{
	box-shadow: 0px 0px 0px 2px #9fb4f2;
	background:linear-gradient(to bottom, #032257 5%, #476e9e 100%);
	background-color:#032257;
	border-radius:10px;
	border:2px solid #4e6096;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:19px;
	padding:12px 37px;
	text-decoration:none;
	text-shadow:0px 1px 0px #060f24;
    width: 150px;
    height: 60px;
};
.box_cell__button:hover{
	background:linear-gradient(to bottom, #476e9e 5%, #032257 100%);
	background-color:#476e9e;
};
.box_cell__button:active {
	position:relative;
	top:1px;
};
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
.vue-slide-bar-tooltip{

}

</style>

