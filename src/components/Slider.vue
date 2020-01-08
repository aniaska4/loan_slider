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
                    .box_cell__box_section--minmax  min: 400
                    .box_cell__box_section--minmax  max: 2000
                .box_cell__box_slider
                    VueSlideBar(
                          v-model="slider.value"
                          :data="slider.data"
                          :range="slider.range"
                          :processStyle="{ backgroundColor: '#ffffff6e' }"
                          :lineHeight="slider.lineHeight"
                          class="demo-demo" id="slider-1")
                          template(slot="tooltip" style="background-color: #031d4c; border: black;" slot-scope="tooltip")
                            img(src="@/public/image/handle.png" style="background-color: white; margin-top: 10px; border-radius: 7px;")
                .box_cell__box_title Ilość rat w miesiącach:
                .box_cell__box_parcels
                    .box_cell__box_parcels--days(
                          v-for="count in monthCounts"
                          :key="count"
                          @click="currentMonthCount = count"
                          :class="currentMonthCount === count ? 'active' : 'available'"
                        ) {{ count }}
                .box_cell__title_parcela
                    #installment Wartość raty: 
                        span.valor#rata {{finalInstallment}}
                .box_cell__button
                    button weź pożyczkę

    
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
            loan: {},
            slider: {
                lineHeight: 8,
                value: 600,
                data: [],
                },
            days: 150,
            monthCounts: [1,2,3,4,5],
            currentMonthCount: 2,
        }
    },

    computed: {
        finalInstallment(){
            if (!this.loan.prices || this.monthCounts === []) {
            return "";
      }
            return this.showPeriod();
        }
         
    },

    created(){
        this.loan = loan.data
        this.slider.data = this.loan.amounts
        console.log(this.loan)

    },

    methods: {
        showPeriod() {
        const index = this.monthCounts.indexOf(this.currentMonthCount); //index klikanego miesiąca
        this.days = Object.keys(this.loan.prices)[index];
        const payment = this.loan.prices[this.days][this.slider.value].schedule[0].amount;
        return payment + "  zł";
        },
        currentMounths(){
             this.currentMounth = this.loan.periods.map(month => month / 30)
             return this.currentMounth
        }
    }
    
}
</script>

<style scoped>
.slider {
  display: flex;
  justify-content: center;
  height: 500px;
  color: #d7d8da;
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
.box_cell__box_title,
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
.box_cell__box_title{
    margin-top: 25px;
}
.box_cell__box_valor{
    text-align: start;
    margin-bottom: 30px;
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
  margin: 30px 0 30px 0;
  text-align: start;
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
.available {
  width: 100%;
  border: solid 1px #fff;
  border-radius: 5px;
  padding: 5px 0;
  color: #fff;
  text-align: center;
  margin: 2px;
}
.active {
  width: 100%;
  background-color: #fff;
  border: solid 1px #fff;
  border-radius: 5px;
  padding: 5px 0;
  margin: 2px;
  color: #000;
  text-align: center;
}

</style>

