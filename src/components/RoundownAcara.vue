<template>
  <div class="roundown container-fluid">
      <div class="roundown-quote container text-center mb-5 pb-md-5">
          <img src="../assets/images/bungaquote.png" alt="Bunga">
          <p>
                “Dan di antara tanda-tanda (kebesaran-Nya) adalah bahwa Dia <br> menciptakan untuk 
                Anda mitra dari jenis Anda sendiri, <br> agar Anda cenderung dan menemukan kedamaian di dalamnya, dan Dia menciptakan  <br>
                di antara Anda cinta dan kasih sayang. <br>
                Ar Ruum : 21
          </p>
      </div>

      <div class="roundown-couple container ">
          <div class="brides container-lg d-flex justify-content-around">
            <div class="bride-men text-center">
                <div class="bride-pic mb-4">
                    <img src="../assets/images/menpic.png" alt="Foto Pria" class="bride-img" id="men-pic">
                    <img src="../assets/images/bungafoto.png" alt="Vector Bunga" class="vec-bunga" id="vector-bunga">
                </div>
                <div class="bride-name mt-lg-3 pt-lg-3" id="men-name">
                    <div class="name my-3">
                        <h1>Robert Goldman</h1> 
                    </div>
                    <div class="sub-name">
                        <p>
                            Anak Kedua dari Keluarga <br>
                            Bapak Robert & Ibu Robert
                        </p>
                    </div>
                </div>
            </div>

            <div class="bride-women text-center">
                <div class="bride-pic mb-4">
                    <img src="../assets/images/wmenpic.png" alt="Foto Wanita" class="bride-img" id="women-pic">
                    <img src="../assets/images/bungafoto.png" alt="Vector Bunga" class="vec-bunga" id="vector-bunga">
                </div>
                <div class="bride-name mt-lg-3 pt-lg-3" id="women-name">
                    <div class="name my-3">
                        <h1>Isabel Daniels</h1> 
                    </div>
                    <div class="sub-name">
                        <p>
                            Anak Pertama dari Keluarga <br>
                            Bapak Isabel & Ibu Isabel
                        </p>
                    </div>
                </div>
            </div>
          </div>
      </div>

      <div class="countdown container my-5 py-lg-5" v-if="loaded">
            <div class="countdown-wrapper row d-flex justify-content-center">
              <div class="box-date col-lg-1 col-6 p-5 mx-lg-3" id="box-hari">
                  <h2>{{ displayDays }}</h2>
                  <h6>Hari</h6>
              </div>
              <div class="box-date col-lg-1 col-6 p-5 mx-lg-3" id="box-jam">
                  <h2>{{ displayHours }}</h2>
                  <h6>Jam</h6>
              </div>
              <div class="box-date col-lg-1 col-6 p-5 mx-lg-3" id="box-menit">
                  <h2>{{ displayMinutes }}</h2>
                  <h6>Menit</h6>
              </div>
              <div class="box-date col-lg-1 col-6 p-5 mx-lg-3" id="box-detik">
                  <h2>{{ displaySeconds }}</h2>
                  <h6>Detik</h6>
              </div>
            </div>
      </div>

      <div class="detail-acara container d-flex justify-content-lg-around justify-content-md-center flex-column flex-lg-row">
          <div class="detail-akad detail text-center">
            <div class="jadwal-akad jadwal">
              <h1>Akad</h1>
              <h6 class="my-3">Sabtu, 12 Desember 2022 <br> Jakarta, Indonesia</h6>
              <h6>Kediaman Mempelai Wanita <br> 08.00 WIB - Selesai</h6>
            </div>

            <button class="detail-btn mt-3">
                <i class='bx-fw bx bxs-map'></i> Lihat lokasi
            </button>
          </div>

          <div class="detail-resepsi detail text-center">
            <div class="jadwal-resepsi jadwal">
                <h1>Resepsi</h1>
                <h6 class="my-3">Minggu, 13 Desember 2022 <br> Jakarta, Indonesia</h6>
                <h6>Priority Sky Ballroom Lt 26, <br> Hotel Aston Priority Simatupang <br> 08.00 WIB - Selesai</h6>
            </div>

            <a href="">
                <button class="detail-btn mt-3">
                    <i class='bx-fw bx bxs-map'></i> Lihat lokasi
                </button>
            </a>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'RoundownAcara',
    props: {
        tanggal: String,
    },
    data: () => ({
        displayDays: 0,
        displayHours: 0,
        displayMinutes: 0,
        displaySeconds: 0,
        loaded: false, // Agar Ketika di Refresh, Countdown Tidak Berubah Jadi 00:00:00:00
        expired: false //Mengatur jika waktu countdown sudah habis
    }),
    computed: {
        _seconds: () => 1000,
        _minutes() {
            return this._seconds * 60
        },
        _hours() {
            return this._minutes * 60
        },
        _days() {
            return this._hours * 24
        },
    },
    mounted() {
        this.showRemaining();
    },
    methods: {
        formatNum: num => (num < 10 ? "0" + num : num), // Format Untuk Mendisplay Date
        showRemaining() {
            const timer = setInterval(() => {
                const date = new Date(); // Mengambil Date 
                const dateEnd = new Date(2022, 11, 12, 10, 10, 10, 10); //Atur Countdown
                const distance = dateEnd.getTime() - date.getTime(); //Mencari jarak detik antara tanggal yang ditentukan dan tanggal sekarang

                if(distance < 0) { // Jika waktu countdown sudah habis, clearInterval Timer
                    clearInterval(timer);
                    this.expired = true;
                    this.loaded = true;
                    return
                }

                const days = Math.floor((distance / this._days));
                const hours = Math.floor((distance % this._days) / this._hours);
                const minutes = Math.floor((distance % this._hours) / this._minutes);
                const seconds = Math.floor((distance % this._minutes) / this._seconds);

                this.displaySeconds = this.formatNum(seconds);
                this.displayMinutes = this.formatNum(minutes);
                this.displayHours = this.formatNum(hours);
                this.displayDays = this.formatNum(days);
                this.loaded = true;
            }, 1000);
        }
    }
}
</script>

<style>
    .roundown {
        height: 100%;
        background: url("../assets/images/baground.png");
        background-size: 100vw 100%;
        background-repeat: no-repeat;
        padding-top: 5rem;
        padding-bottom: 10rem;
        transition: all 0.35s ease linear;
        display: none;
    }

    .roundown-quote {
        background: #F4F2F5;
        box-shadow: 0px 1px 26px 4px rgba(0, 0, 0, 0.25);
        border-radius: 27px;
        padding: 5px 0;
        padding-top: 1.5rem;
        position: relative;
    }

    .roundown-quote img {
        position: absolute;
        width: 200px;
        top: -100px;
        left: -50px;
    }

    @media screen and (max-width: 768px) {
        .roundown-quote img {
            width: 100px;
            top: -50px;
        }
    }

    .roundown-couple {
        background: #F4F2F5;
        box-shadow: 0px 1px 26px 4px rgba(0, 0, 0, 0.25);
        border-radius: 27px;
        height: 350px;
        display: grid;
        place-items: center;
    }


    .bride-pic {
        /* transform: translateY(2rem); */
        position: relative;
    }

    .bride-pic .bride-img {
        width: 100px;
    }

    .bride-pic .vec-bunga {
        width: 100px;
        /* transform: translateY(-3rem); */
        position: absolute;
        left: calc(50% - 50px);
        bottom: -20%;
    }

    .bride-name .name h1 {
        font-size: 1.5rem;
        text-transform: uppercase;
        letter-spacing: 2px;
        color: var(--primary-color);
    }

    .bride-name .sub-name p {
        font-size: 1rem;
    }


    /* === Countdown === */
    .box-date {
        height: 90px;
        border-radius: 11px;
        display: flex;
        gap: 5px;
        justify-content: center;
        align-items: end;
    }

    .box-date h2, h6 {
        color: var(--primary-color);
    }

    @media screen and (min-width: 992px) {
        .roundown-quote {
            margin: 8rem 0;
        }
        .roundown-quote p {
            font-size: 1.2rem;
        }
        .roundown-couple {
            height: 450px;
        }

        .bride-pic .bride-img {
            width: 200px;
        }

        .bride-pic .vec-bunga {
            width: 200px;
            /* transform: translateY(-3rem); */
            position: absolute;
            left: calc(50% - 95px);
            bottom: -20%;
        }

        .bride-name .name h1 {
            font-size: 2rem;
            letter-spacing: 5px;
        }

        .bride-name .sub-name p {
            letter-spacing: 5px;
        }

        .box-date h2 {
            font-size: 2.5rem;
        }
    }

    /* === Detail Acara === */
    .detail {
        display: grid;
        place-items: center;
    }

    .detail .jadwal h1 {
        color: var(--primary-color);
    }

    .detail .jadwal h6 {
        font-style: italic;
    }

    .detail-btn {
        border: none;
        outline: none;
        width: 10rem;
        height: 2.5rem;
        padding: 1rem;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1rem;
        background: var(--secondary-color);
        border-radius: 10px;
        color: #FFFFFF;
    }

    .detail-btn:hover {
        background: var(--tertiary-color);
    }

    .detail-btn i {
        color: #FFFFFF;
    }

    @media screen and (max-width: 768px) {
        .detail {
            margin-bottom: 3rem;
        }
    }
</style>