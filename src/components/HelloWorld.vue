<template>
  <div class="hello">
    <h1 v-if="show">{{ msg }}</h1>
    <h1 v-else>Judul Disembunyikan</h1>

    <p>{{ nama }}</p>
    <p>{{ 'Poin Anda '+poin}}</p>
    <input type="text" v-model="nama">

    <button type="button" v-on:click="hideTitle">Click Me</button>
    <div v-for="(item,index) in items" :key="item.pertanyaan" :options="item.pertanyaan">
      <p>{{ item.pertanyaan}}</p>
      <div  v-for="pilih in item.pilihan" :key="pilih.pilihan" :options="pilih.pilihan">
        <input type="radio"  name="data['+index+']" 
         v-on:click="checkJawaban(index,pilih.pilihan)" 
        :value="pilih.pilihan" v-model="jawab">{{ pilih.pilihan }} 
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
  data: function(){
    return {
      nama: 'Rasyad',
      show: true,
      poin:0,
      jawab:String,
      items:[
      {
        name:'soal1',
        pertanyaan: '1. 2+1-1+5= ?',
        answer:String,
        check:true,
        pilihan:[
        { pilihan:'10' },
        { pilihan:'5' },
        { pilihan:'7'},
        { pilihan:'3' } ],
        jawaban:'7'
      },
      {
        pertanyaan: 'apa makanan yang berkuah?',
        name:'soal2',
        check:true,
        answer:String,
        pilihan:[
        {
          pilihan:'bakso'
        },
        {
          pilihan:'nasi goreng'
        },
        {
          pilihan:'siomay'
        },
        {
          pilihan:'ayam goreng'
        }
        ],
        jawaban:'bakso'
      },
      {
        pertanyaan: '3. apa bahan bakar truk? ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        {
          pilihan:'air'
        },
        {
          pilihan:'premium'
        },
        {
          pilihan:'pertamax'
        },
        {
          pilihan:'solar'
        }
        ],
        jawaban:'solar'
      }
      ]
    }
  },
  methods: {
    hideTitle () {
      this.show = !this.show
    },
    checkJawaban(i,jawab){
         if(this.items[i].jawaban === jawab){
          this.poin++;
        }
        this.items[i].check = false;
         
        
    }
  },
  mounted: function () {
    this.nama = 'Suwita'
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
    