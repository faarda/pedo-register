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
          <a target="_blank" href="https://github.com/faarda/pedo-register">
            <img src="@/assets/github.png" alt="">
          </a>
        </div>
      </div>
    </header>
    <div class="design design--top">
      <img src="@/assets/yellow.png" alt="">
    </div>
        <div class="design design--bottom">
      <img src="@/assets/blue.png" alt="">
    </div>
    <div style="min-height: 80vh">

      <router-view/>
    </div>
    <footer class="footer">
      <span class="copy">This platform was funded and developed by a coalition of tech bro’s who are against the sexual exploitation of minors and violence against women, sexual or otherwise.</span>

      <b>Developed by <a href="https://twitter.com/silasadedoyin">Silas</a></b>
    </footer>
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
    position: relative;
  }
  
  .design{
    position: fixed;
    z-index: -1;
    width: 200px;
    height: 200px;
  }

  .design--top{
        top: 20px;
    right: 0;
    transform: translateX(30%);
  }

    .design--bottom{
        bottom: 20px;
    left: 0;
    transform: translateX(-30%);
  }

  .design img{
    width: 100%;
    opacity: 0.4;
    /* display: none; */
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

  .footer{
    margin-top: 50px;
    padding: 25px 35px;
    background: #ddd;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  @media screen and (max-width: 750px){
      .footer{
        flex-direction: column;
      }

      .footer .copy{
        text-align: center;
        margin-bottom: 15px;
        margin-right: 0;
      }
  }

  .footer .copy{
    max-width: 800px;
    margin-right: 30px;
  }
</style>
