<template>
  <div class="home">
    <!-- <h2>Search for persons by names</h2> -->
    <div class="search">
      <input type="text" v-model="query" @input="searchPedos"  placeholder="Search persons by name" class="form-input">
      <button class="search__btn">
        <span data-feather="search"></span>
      </button>
    </div>
    <div class="">
      <h4 class="lead-text">This page shows a list of people who have displayed gross pedophilic tendencies on the Twitter microblogging platform, and is an attempt to help curb Pedophila.</h4>

      <div class="pedos">

      <pedo v-for="pedo in pedos" :key="pedo"></pedo>
      </div>
    </div>
  </div>
</template>

<script>
require('../../public/feather');
import Pedo from '../components/Pedo';
export default {
  name: 'home',
  data(){
    return {
      pedos: [1, 2, 3, 4, 5, 6],
      results: [],
      query: ""
    }
  },
  components: {
    Pedo
  },
  mounted(){
    feather.replace();
  },
  computed: {
    list(){
      if(this.results.length == 0 || this.query == ""){
        return this.pedos;
      }else{
        return this.results;
      }
    }
  },
  methods:{
    searchPedos(){
      this.results = [...this.pedos].filter((val) => {
        // console.log(val);
        return val.name.toLowerCase().indexOf(this.query.toLowerCase());
      });


    }
  }
}
</script>

<style>
  .home{
    display: grid;
    grid-template-columns: minmax(500px, 80%);
    align-items: center;
    justify-content: center;
    margin: 100px 50px auto;
  }

  h2{
    text-align: center;
  }

  .lead-text{
    text-align: center;
    max-width: 700px;
    margin: 0 auto;
    color: #777;
  }


  .search{
    width: 70%;
    margin: 30px auto;
    border: solid 1px rgba(0,31, 63, 0.70);
    display: flex;
    align-items: center;
    height: 50px;
    border-radius: 10px;
    overflow: hidden;
  }

  .search .form-input{
    height: 100%;
    flex: 1;
    border: 0;
    outline: 0;
    padding: 5px 15px;
  }

  .search__btn{
    outline: none;
    border: none;
    background: transparent;
    padding: 8px 10px;
    margin-right: 8px;
    border-radius: 5px;
    cursor: pointer;
    transition: .5s all;
  }

  .search__btn .feather{
    width: 16px;
    height: 16px;
    color: #FF851B;
    transition: .5s all;
  }

  .search__btn:hover{
    background: #FF851B;
  }

  .search__btn:hover > .feather{
    color: #f2f2f2;
  }

  .pedos{
    margin: 30px auto;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    /* grid-auto-rows: 85%; */
    grid-column-gap: 50px;
    flex-direction: column;
    align-items: top;
  }

  
  a{
    color: #008751;
    text-decoration: none;
    transition: .5s all;
  }

  a:hover{
    text-decoration: underline;
  }

  @media screen and (max-width: 600px){
    .home{
      grid-template-columns: 95%;
      margin: 100px 20px auto;
    }

    h1{
      font-size: 22px;
    }

    .search{
      width: 90%;
      margin-bottom: 10px;
    }

    .pedos{
      width: 95%;
      grid-template-columns: 100%;
      grid-column-gap: 0;
    }

    
  }

</style>
