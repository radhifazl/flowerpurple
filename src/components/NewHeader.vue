<template>
  <div class="header text-center container-fluid pt-3">
    <img src="../assets/images/bunga.png" alt="Bunga" id="vector-bunga1">
    <img src="../assets/images/bungs.png" alt="Bunga" id="vector-bunga2">
    <div class="header-content">
      <div class="header-section-title">
        <h1 class="header-title">We Invite You to <br> Celebrate Our Wedding</h1>
        <h2 class="header-subtitle p-3">the wedding of</h2>
      </div>
      <div class="header-couple-name">
        <h1 class="title pb-2">Isabel Daniels</h1>
        <p class="p-lg-3" id="and">and</p>
        <h1 class="title pt-2">Robert Goldman</h1>
      </div>
      <div class="header-date">
        <h5>Sunday</h5>
        <h3 class="date">12 / Desember / 2022</h3>
      </div>
    </div>
    <div class="header-quotes">
      <p>Maha suci Allah SWT yang telah menciptakan makhluk-NYA berpasang-pasangan <br> untuk mengikuti Sunnah Rasul-Mu
       dalam rangka membentuk keluarga yang <br> sakinah, mawaddah, warahmah. Maka ijinkanlah kami menikahkannya.</p>
    </div>
  </div>
</template>

<script>
export default {
    name: 'NewHeader'
}
</script>

<style>
  .header {
    display: none;
    place-items: center;
    height: 100vh;
    position: relative;
    transition: all 0.35s ease;
  }


  .header img {
    position: absolute;
    max-width: 250px;
  }

  #vector-bunga1 {
    top: 1%;
    left: 1%;
  }

  #vector-bunga2 {
    bottom: -20%;
    right: 1%;
  }

  .header-title {
    font-family: var(--second-font);
    font-size: 20px;
    text-transform: uppercase;
  }

  .header-subtitle {
    font-family: var(--fifth-font);
  }

  .header-couple-name h1 {
    font-size: 45px;
    text-transform: uppercase;
    letter-spacing: 4px;
  }

  #and {
    width: 130px;
    position: relative;
    margin: auto;
    font-family: var(--fifth-font);
    font-size: 1.2rem;
  }

  #and::before, #and::after {
    content: '';
    position: absolute;
    width: 100%;
    height: 3px;
    top: calc(50% - 1.5px);
    background: var(--secondary-color);
  }

  #and::before {
    left: -90%;    
  }

  #and::after {
    right: -90%;
  }

  .header-date h5, h3 {
    letter-spacing: 5px;
  }

  .date {
    color: var(--primary-color);
  }

  .header-quotes p {
    font-size: 1.1rem;
    letter-spacing: 3px;
  }

  @media screen and (max-width: 768px) {
    .header img {
      max-width: 50px;
    } 

    #vector-bunga1 {
      top: 1%;
      left: 1%;
    }

    #vector-bunga2 {
      bottom: 0;
      right: 1%;
    }

    .header-title {
      font-size: 18px;
    }

    .header-couple-name h1 {
      font-size: 30px;
      text-transform: uppercase;
      letter-spacing: 4px;
    }

    #and::before, #and::after {
      width: 90%;
    }

    #and::before {
      left: -80%;
    }

    #and::after {
      right: -80%;
    }

    .header-date h5 {
      font-size: 15px;
    }

    .header-date h3 {
      font-size: 18px;
    }

    .header-quotes p {
      font-size: 1rem;
    }
  }
</style>