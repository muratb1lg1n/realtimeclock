<template>
  <div class="hello" v-if="yuk">
    <h1>{{ msg }}</h1>
    <h2>{{gostergun}} {{gostertar}} {{gosteray}} {{gosteryil}}</h2>
    <div id="app">
      <div class="container">
        <span id="saatler">{{gostersaat}}</span>
      </div>
      <div class="container">
        <span id="ciftnokta">:</span>
      </div>
      <div class="container">
        <span id="dakikalar">{{gosterdak}}</span>
      </div>
      <div class="container">
        <span id="ciftnokta">:</span>
      </div>
      <div class="container">
        <span id="saniyeler">{{gostersan}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String

  },
  data: ()=> ({
    gosteryil: 0,
    gosteray: "",
    gostertar: 0,
    gostergun: "",
    gostersaat: 0,
    gosterdak: 0,
    gostersan: 0,
    yuk: false,
  }),
  methods: {
    sifirli: girdi => (girdi < 10 ? "0" + girdi : girdi),
    hesap(){
      setInterval(()=>{
         const date = new Date();

         const ayarrray = ["Ocak","Subat","Mart","Nisan","Mayis","Haziran","Temmuz","Agustos","Eylul","Ekim","Kasim","Aralik"];
         const gunarray =["Pazar","Pazartesi","Sali","Carsamba","Persembe","Cuma","Cumartesi"]
         
         const yil = date.getFullYear();
         const ay = date.getMonth();
         const tar = date.getDate();
         const gun = date.getDay();
         const saat = date.getHours();
         const dakika = date.getMinutes();
         const saniye = date.getSeconds();
         
         this.gosteryil = yil;
         this.gosteray = ayarrray[ay];
         this.gostertar = tar;
         this.gostergun = gunarray[gun]
         this.gostersaat = this.sifirli(saat);
         this.gosterdak = this.sifirli(dakika);
         this.gostersan = this.sifirli(saniye);

         this.yuk = true;
      },1000)
    }
  },
  mounted() {
    this.hesap();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body{
  
  text-align: center;
  display: flex;
  flex-direction: column;
}
#app{
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  margin-top:  5%;
  
}
p {
  font-family: "Lucida Console", Monaco, monospace;
  padding: 10px;
  font-size: 45px;
  
}
span {
 
  font-size: 95px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
