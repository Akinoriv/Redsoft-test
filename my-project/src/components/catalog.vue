<template>

  <div class="page">
    <div class="page__title">
      <h1> Картины эпохи Возрождения </h1>
    </div>

    <div class="wrap">
      <div class="paintings">

        <div class="painting__item">
          <img class="painting__item-img" 
            src="https://github.com/Akinoriv/Redsoft-test/blob/master/my-project/src/assets/painting-63186_1280%201.png?raw=true" 
            alt="«Рождение Венеры»"
          >
          <h2 class="painting__item-name"> «Рождение Венеры» <br> Сандро Боттичелли </h2>
          <div class="painting__item-block">
            <div class="painting__price-box">
              <h6 class="painting__price-discount"> 2 000 000 $ </h6>
              <h3 class="painting__price--new"> 1 000 000 $ </h3>
            </div>
            <div class="painting__button-box">
              <button  v-if="picture[0].status" class="painting__button"  v-on:click="putInBacskets0"> {{ picture[0].state }} </button>
              <button  v-else id="hide-seen" class="painting__button painting__button--basket" v-on:click="putInBacskets0"> 
                <img class="foter__contacts-img" 
                src="https://raw.githubusercontent.com/Akinoriv/Redsoft-test/216b544ec28482b1801ed7ef5c97ec9a1b2ceb7f/my-project/src/assets/Vector.svg"> 
                {{ picture[0].state }} 
              </button>
            </div>
          </div>
        </div>

        <div class="painting__item">
          <img class="painting__item-img"
            src="https://github.com/Akinoriv/Redsoft-test/blob/master/my-project/src/assets/ae973f6678e037cd297053384aa7dca0%201.png?raw=true"
            alt="«Тайная вечеря»"
          >
          <h2 class="painting__item-name"> «Тайная вечеря» <br> Леонардо да Винчи </h2>
          <div class="painting__item-block">
            <div class="painting__price-box">
              <h3 class="painting__price"> 3 000 000 $ </h3>
            </div>
            <div class="painting__button-box">
              <button  v-if="picture[1].status" class="painting__button"  v-on:click="putInBacskets1"> {{ picture[1].state }} </button>
              <button  v-else id="hide-seen" class="painting__button painting__button--basket" v-on:click="putInBacskets1"> 
                <img class="foter__contacts-img" 
                src="https://raw.githubusercontent.com/Akinoriv/Redsoft-test/216b544ec28482b1801ed7ef5c97ec9a1b2ceb7f/my-project/src/assets/Vector.svg"> 
                {{ picture[1].state }} 
              </button>
            </div>
        </div>
        </div>

        <div class="painting__item">
          <img class="painting__item-img" 
            src="https://github.com/Akinoriv/Redsoft-test/blob/master/my-project/src/assets/image-19%201.png?raw=trues" 
            alt="«Сотворение Адама»"
          >
          <h2 class="painting__item-name"> «Сотворение Адама» <br> Микеланджело </h2>
          <div class="painting__item-block">
            <div class="painting__price-box">
              <h6 class="painting__price-discount"> 6 000 000 $ </h6>
              <h3 class="painting__price--new"> 5 000 000 $ </h3>
            </div>

            <div class="painting__button-box">
              <button  v-if="picture[2].status" class="painting__button" v-on:click="ajaxRequest"> {{ picture[2].state }} </button>
              <button  v-else  class="painting__button painting__button--basket" v-on:click="ajaxRequest"> 
                <img class="foter__contacts-img" 
                src="https://raw.githubusercontent.com/Akinoriv/Redsoft-test/216b544ec28482b1801ed7ef5c97ec9a1b2ceb7f/my-project/src/assets/Vector.svg"> 
                {{ picture[2].state }} 
              </button>
            </div>

          </div>
        </div>

        <div class="painting__item painting__item--sold">
          <img class="painting__item-img" 
            src="https://github.com/Akinoriv/Redsoft-test/blob/master/my-project/src/assets/20152310142330%201.png?raw=true" 
            alt="«Урок анатомии»"
          >
          <h2 class="painting__item-name"> «Урок анатомии» <br> Рембрандт </h2>
          <div class="painting__item-block--sold">
            <h3 class="painting__price"> Продана на аукционе </h3>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
// import axios from "axios";

export default {
  data() {
    return {
      test: "",
      picture: [
        {
          id: 0,
          name: "Рождение Венеры",
          state: "Купить",
          status: true
        },
         {
          id: 1,
          name: "Тайная вечеря",
          state: "Купить",
          status: true
        },
        {
          id: 2,
          name: "Сотворение Адама",
          state: "Купить",
          status: true
        },
      ],

    }
  },

  methods: {  
  
    // changes the state of the button on clicked
    putInBacskets0: function () {
      this.picture[0].status = !this.picture[0].status;
      this.picture[0].state = this.picture[0].status ? 'Купить' : 'В корзине';
    },
    // TO DO
    putInBacskets1: function () {
      this.picture[1].status = !this.picture[1].status;
      this.picture[1].state = this.picture[1].status ? 'Купить' : 'В корзине';
    },  
     
    putInBacskets2: function() {
      var then = this;
      // then.picture[2].status = !then.picture[2].status;
      then.picture[2].state = then.picture[2].status ? 'Купить' : 'Обработка';
    },
  
    ajaxRequest: function() {
      this.putInBacskets2();
      var then = this;
      let XMLH = new XMLHttpRequest();

      XMLH.open('GET', "https://jsonplaceholder.typicode.com/posts/1");
      
      XMLH.onreadystatechange = function() {
        if (XMLH.readyState === 4 && XMLH.status === 200) {
          test(XMLH.responseText);
          putInBacsketsOk(XMLH.responseText);
        }
        else {
          putInBacsketsEror()
        }
      }
      function putInBacsketsOk() {
        then.picture[2].status = !then.picture[2].status;
        then.picture[2].state = then.picture[2].status ? 'Купить' : 'В корзине';
      }
      function putInBacsketsEror() {
        then.picture[2].status = !then.picture[2].status;
        then.picture[2].state = then.picture[2].status ? 'Купить' : 'Eror';
      // then.picture[2].state =  'обработка' ;
    }
      function test(data) {
        console.log(data) 
      }

      XMLH.send();
    
    },
  },

  // mounted() {
  //   var then = this
  //   if(localStorage.getItem()){
  //     then.picture = localStorage.test;
  //   }
  // },

    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">

.page {
  /* min-height: calc(100vh - 80px); */
  padding-top: 102px;
  padding-bottom: 96px;
  // box-sizing: border-box;
	// min-height: 100%; 
}

.page__title {

  /* max-width: 1400px; */
  /* padding-left: 7%; */
  justify-content: start;
  padding: 24px;
  padding-bottom: 14px;
  /* position: fixed; */
}

.wrap {
  /* padding:24px; */
  margin: 0 auto;
  width: 100%;
  max-width: 1400px;
  display: flex;
  justify-content: space-around;

  /* justify-content: space-between; */
}

/* .paintings {
} */

.painting__item {
  height: 328px;
  width: 282px;
  float:left; 
  text-align:center;
  margin: 14px;
  /* position: absolute; */
  /* left: 0%;
  right: 0%;
  top: 0%;
  bottom: 0%; */
  border: 1px solid #E1E1E1;
  box-sizing: border-box;
}

.painting__item-name {
  padding-left: 24px;
  text-align: left;
  line-height: 1.5;
}

.painting__item-img  {
  height: 158px;
  width: 280px;
}

.painting__item-block {
  margin:  24px;
  /* padding-top: ; */
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
}

.painting__price-box {
  align-self: center;
}

.painting__price {
  margin: 0;
  text-align: start;
} 

.painting__price--new {
  margin: 0;
  text-align: start;
}

.painting__price-discount {
  color: #A0A0A0;
  text-decoration: line-through;
  margin: 0;
  text-align: start;
}

.painting__item--sold {
  background :rgb(246, 243, 243);
  opacity:.4; 
}

.painting__item-block--sold {
  margin: 24px;
  text-align: left;
  display: flex;
  align-items: flex-end;
}

.painting__button {
   /* padding-left: 24px; */
  border: none;
  height: 48px;
  width: 120px;
  background-color: #382E2B;
  color: #F4F6F9;
  Font-Family: Merriweather;
  Font-Style: Bold;
  Font-Size: 14px;
  Line-Height: 21px;
  Line-Height: 150%;
  /* justify-content: space-evenly; */
  justify-content:right;
}

.painting__button--basket {
  background-color: #5B3A32
  
}


</style>
