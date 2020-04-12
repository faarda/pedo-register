<template>
  <div id="app">
    <header class="header">
      <div class="logo">
         <!-- <img src="@/assets/senate.png" alt=""> -->
         Twitter Pedophiles
      </div>
      <div class="header__end">
        <a href="" class="btn">Donate</a>
        <div class="github">
          <a target="_blank" href="https://github.com/faarda/Nigerian-senators-contacts">
            <img src="@/assets/github.png" alt="">
          </a>
        </div>
      </div>
    </header>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: "app",
  mounted(){
    window.addEventListener('scroll', () => {
      let top = window.scrollY;
      const header = document.querySelector('.header');

      if(top >= 55){
        header.classList.add('active');
      }else{
        header.classList.remove('active');
      }
    });
  }
}
</script>

<style>

  *{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  body{
    font-family: 'Lato', sans-serif;
    color: #001F3F;
  }

  .header{
    background: #fff;
    height: 70px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    border-bottom: solid 1px #ddd;
    box-shadow: none;
    transition: box-shadow 1s ease;
    z-index: 1000;
  }

  .header.active{
        box-shadow: 0 2px 10px rgba(0, 0, 0, .07);
        border-bottom: 0;
  }

  .header__end{
    display: flex;
    align-items: center;
  }

  .logo{
    display: inline-block;
    font-weight: bold;
  }

  .logo img{
    width: 100%;
  }

  .btn{
    text-decoration: none !important;
    background: #FF851B;
    color: #fff;
    padding: 10px 15px;
    border-radius: 5px;
    margin: 10px 20px;
  }

  .btn:hover{
    box-shadow: 0 2px 10px rgba(0, 0, 0, .07);
  }

  .github{
    display: inline-block;
    width: 30px;
    cursor: pointer;
  }

  .github img{
    width: 100%;
  }
</style>
