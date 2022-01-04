<template>
  <div class="cover-page container-fluid py-5" id="cover-page">
    <img src="../assets/images/coverpage/bungakiri.png" class="coverbunga" id="bk-1" alt="Bunga">
    <img src="../assets/images/coverpage/bungakanan.png" class="coverbunga" id="bk-2" alt="Bunga">
    <img src="../assets/images/coverpage/bungakiri2.png" class="coverbunga" id="bk-3" alt="Bunga">
    <img src="../assets/images/coverpage/bungakanan2.png" class="coverbunga" id="bk-4" alt="Bunga">
    <div class="cover-page-content container text-center py-5">
      <div class="cover-text">
        <h6>Wedding Invitation</h6>

        <div class="brides-name mb-5 p-5">
          <h1>Isabel Daniels</h1>
          <p class="mx-auto" id="dan">dan</p>
          <h1>Robert Goldman</h1>
        </div>

        <div class="open-button" @click="showContent">
          <h6>open</h6>
          <img src="../assets/images/coverpage/bungatengah.png" alt="BUnga">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CoverPage',

  methods: {
    showContent() {
      const coverPage = document.getElementById('cover-page');
      const roundown = document.querySelector('.roundown');
      const header = document.querySelector('.header');
      
      coverPage.classList.add('closed');
      roundown.style.display = "block";
      header.style.display = "grid";


    }
  },
}
</script>

<style>
  .cover-page {
    max-height: 100vh;
    display: grid;
    place-items: center;
    background: radial-gradient(84.72% 84.72% at 50% 45.17%, #FFFFFF 50.83%, #DDC9DC 86.04%);
    overflow-y: hidden;
    position: fixed;
    top: 0;
    left: 0;
    transition: 3s ease;
    z-index: 1000;
  }

  .cover-page.closed {
    transform: translateY(-100rem);
  }

  .cover-page .coverbunga {
    position: absolute;
    width: 100px;
  }

  #bk-1, #bk-2 {
    top: 0;
  }

  #bk-3, #bk-4 {
    bottom: 0;
  }

  #bk-1, #bk-3 {
    left: 0;
  }

  #bk-2, #bk-4 {
    right: 0;
  }

  @media screen and (min-width: 992px) {
    #bk-1, #bk-2 {
      width: 300px;
    }

    #bk-3, #bk-4 {
      width: 200px;
    }
  }

  .cover-text h6 {
    text-transform: uppercase;
    color: var(--secondary-color);
    font-family: var(--second-font);
    letter-spacing: 5px;
  }

  .brides-name { width: 100%; }

  .brides-name h1 {
    font-family: var(--second-font);
    letter-spacing: 5px;
    text-transform: uppercase;
  }

  #dan {
    width: 130px;
    position: relative;
    font-family: var(--fifth-font);
    font-size: 1.2rem;
  }

  #dan::before, #dan::after {
    content: '';
    position: absolute;
    width: 100%;
    height: 3px;
    top: calc(50% - 1.5px);
    background: var(--secondary-color);
  }

  #dan::before {
    left: -80%;    
  }

  #dan::after {
    right: -80%;
  }

  .open-button { cursor: pointer; }

  .open-button h6 {
    font-family: var(--second-font);
    color: var(--secondary-color);
    font-size: 1.2rem;
  }

  .open-button img {
    transform: translateY(-3rem);
    width: 200px;
    transition: 0.35s ease; 
  }

  .open-button img:hover {
    transform: translateY(-3.5rem);
  }
</style>