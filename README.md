<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />

  <meta
    name="viewport"
    content="width=device-width, initial-scale=1.0, viewport-fit=cover"
  />

  <meta name="theme-color" content="#1565c0" />

  <title>Şehir Rehberi</title>

  <style>
    :root {
      --ana-renk: #1565c0;
      --koyu-renk: #0d47a1;
      --arka-plan: #f4f7fb;
      --beyaz: #ffffff;
      --yazi: #202124;
      --gri: #68717d;
      --kenarlik: #e1e7ef;
      --yesil: #188038;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      background: var(--arka-plan);
      color: var(--yazi);
      font-family: Arial, Helvetica, sans-serif;
      -webkit-tap-highlight-color: transparent;
    }

    header {
      background: linear-gradient(135deg, var(--ana-renk), var(--koyu-renk));
      color: var(--beyaz);
      padding: calc(24px + env(safe-area-inset-top)) 18px 26px;
      text-align: center;
      border-radius: 0 0 28px 28px;
      box-shadow: 0 7px 20px rgba(13, 71, 161, 0.22);
    }

    header h1 {
      margin: 0 0 8px;
      font-size: 27px;
    }

    header p {
      margin: 0;
      opacity: 0.9;
      font-size: 15px;
    }

    main {
      width: min(100%, 900px);
      margin: auto;
      padding: 18px 14px 45px;
    }

    .arama-alani {
      position: sticky;
      top: 0;
      z-index: 10;
      padding: 10px 0;
      background: rgba(244, 247, 251, 0.95);
      backdrop-filter: blur(8px);
    }

    #arama {
      width: 100%;
      border: 1px solid var(--kenarlik);
      border-radius: 15px;
      background: var(--beyaz);
      padding: 15px 16px;
      font-size: 16px;
      outline: none;
      box-shadow: 0 4px 14px rgba(0, 0, 0, 0.05);
    }

    #arama:focus {
      border-color: var(--ana-renk);
      box-shadow: 0 0 0 3px rgba(21, 101, 192, 0.12);
    }

    .kategoriler {
      display: grid;
      grid-template-columns: repeat(5, minmax(105px, 1fr));
      gap: 9px;
      overflow-x: auto;
      padding: 8px 0 16px;
    }

    .kategori {
      border: 1px solid var(--kenarlik);
      background: var(--beyaz);
      color: var(--yazi);
      border-radius: 14px;
      min-height: 67px;
      padding: 10px 8px;
      cursor: pointer;
      font-weight: bold;
      font-size: 13px;
    }

    .kategori span {
      display: block;
      font-size: 23px;
      margin-bottom: 4px;
    }

    .kategori.aktif {
      background: var(--ana-renk);
      border-color: var(--ana-renk);
      color: var(--beyaz);
    }

    .bolum-basligi {
      margin: 15px 2px 12px;
      font-size: 21px;
    }

    .liste {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 13px;
    }

    .kart {
      background: var(--beyaz);
      border: 1px solid var(--kenarlik);
      border-radius: 18px;
      padding: 17px;
      box-shadow: 0 5px 18px rgba(29, 43, 76, 0.06);
    }

    .kart-ust {
      display: flex;
      align-items: flex-start;
      gap: 12px;
    }

    .simge {
      min-width: 48px;
      height: 48px;
      border-radius: 14px;
      display: grid;
      place-items: center;
      background: #e8f0fe;
      font-size: 25px;
    }

    .kart h3 {
      margin: 2px 0 7px;
      font-size: 18px;
      line-height: 1.3;
    }

    .tur {
      display: inline-block;
      background: #e8f0fe;
      color: var(--koyu-renk);
      padding: 5px 9px;
      border-radius: 20px;
      font-size: 12px;
      font-weight: bold;
    }

    .bilgi {
      color: var(--gri);
      margin: 13px 0;
      line-height: 1.55;
      font-size: 14px;
    }

    .butonlar {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
    }

    .buton {
      text-decoration: none;
      text-align: center;
      border-radius: 11px;
      padding: 11px 8px;
      font-size: 14px;
      font-weight: bold;
    }

    .harita {
      background: var(--ana-renk);
      color: var(--beyaz);
    }

    .telefon {
      background: #e6f4ea;
      color: var(--yesil);
    }

    .bos {
      grid-column: 1 / -1;
      text-align: center;
      background: var(--beyaz);
      padding: 35px 15px;
      border-radius: 18px;
      color: var(--gri);
    }

    footer {
      text-align: center;
      color: var(--gri);
      padding: 15px;
      font-size: 13px;
    }

    @media (max-width: 650px) {
      .liste {
        grid-template-columns: 1fr;
      }

      .kategoriler {
        grid-template-columns: repeat(5, 108px);
      }
    }
  </style>
</head>

<body>
  <header>
    <h1>📍 Şehir Rehberi</h1>
    <p>Okullar, yurtlar ve camiler tek uygulamada</p>
  </header>

  <main>
    <div class="arama-alani">
      <input
        id="arama"
        type="search"
        placeholder="Kurum adı veya adres ara..."
        autocomplete="off"
      />
    </div>

    <div class="kategoriler">
      <button class="kategori aktif" data-kategori="ilkokul">
        <span>🎒</span>İlkokullar
      </button>

      <button class="kategori" data-kategori="ortaokul">
        <span>📘</span>Ortaokullar
      </button>

      <button class="kategori" data-kategori="lise">
        <span>🎓</span>Liseler
      </button>

      <button class="kategori" data-kategori="yurt">
        <span>🏠</span>Yurtlar
      </button>

      <button class="kategori" data-kategori="cami">
        <span>🕌</span>Camiler
      </button>
    </div>

    <h2 class="bolum-basligi" id="bolumBasligi">İlkokullar</h2>

    <section class="liste" id="kurumListesi"></section>
  </main>

  <footer>
    © 2026 Şehir Rehberi
  </footer>

  <script>
    /*
      KENDİ BİLGİLERİNİ BURADAN DEĞİŞTİREBİLİRSİN.

      kategori seçenekleri:
      ilkokul, ortaokul, lise, yurt, cami
    */

    const kurumlar = [
      {
        ad: "Örnek İlkokulu",
        kategori: "ilkokul",
        adres: "Merkez Mahallesi, Cizre",
        telefon: "04860000001"
      },
      {
        ad: "Cumhuriyet İlkokulu",
        kategori: "ilkokul",
        adres: "Örnek Mahallesi, Cizre",
        telefon: "04860000002"
      },
      {
        ad: "Örnek Ortaokulu",
        kategori: "ortaokul",
        adres: "Dicle Mahallesi, Cizre",
        telefon: "04860000003"
      },
      {
        ad: "Merkez Ortaokulu",
        kategori: "ortaokul",
        adres: "Merkez, Cizre",
        telefon: "04860000004"
      },
      {
        ad: "Örnek Anadolu Lisesi",
        kategori: "lise",
        adres: "Yeni Mahalle, Cizre",
        telefon: "04860000005"
      },
      {
        ad: "Örnek Mesleki ve Teknik Anadolu Lisesi",
        kategori: "lise",
        adres: "Merkez, Cizre",
        telefon: "04860000006"
      },
      {
        ad: "Örnek Öğrenci Yurdu",
        kategori: "yurt",
        adres: "Üniversite Caddesi, Cizre",
        telefon: "04860000007"
      },
      {
        ad: "Merkez Öğrenci Yurdu",
        kategori: "yurt",
        adres: "Merkez Mahallesi, Cizre",
        telefon: "04860000008"
      },
      {
        ad: "Örnek Merkez Camii",
        kategori: "cami",
        adres: "Merkez Mahallesi, Cizre",
        telefon: ""
      },
      {
        ad: "Örnek Ulu Camii",
        kategori: "cami",
        adres: "Eski Çarşı, Cizre",
        telefon: ""
      }
    ];

    const kategoriBilgileri = {
      ilkokul: {
        baslik: "İlkokullar",
        tur: "İlkokul",
        simge: "🎒"
      },
      ortaokul: {
        baslik: "Ortaokullar",
        tur: "Ortaokul",
        simge: "📘"
      },
      lise: {
        baslik: "Liseler",
        tur: "Lise",
        simge: "🎓"
      },
      yurt: {
        baslik: "Yurtlar",
        tur: "Öğrenci Yurdu",
        simge: "🏠"
      },
      cami: {
        baslik: "Camiler",
        tur: "Cami",
        simge: "🕌"
      }
    };

    let seciliKategori = "ilkokul";

    const listeAlani = document.getElementById("kurumListesi");
    const aramaAlani = document.getElementById("arama");
    const baslikAlani = document.getElementById("bolumBasligi");
    const kategoriButonlari = document.querySelectorAll(".kategori");

    function guvenliMetin(metin) {
      const alan = document.createElement("div");
      alan.textContent = metin;
      return alan.innerHTML;
    }

    function kurumlariGoster() {
      const aranan = aramaAlani.value.trim().toLocaleLowerCase("tr-TR");

      const sonuclar = kurumlar.filter((kurum) => {
        const kategoriUygun = kurum.kategori === seciliKategori;

        const metin =
          `${kurum.ad} ${kurum.adres}`.toLocaleLowerCase("tr-TR");

        const aramaUygun = metin.includes(aranan);

        return kategoriUygun && aramaUygun;
      });

      baslikAlani.textContent =
        `${kategoriBilgileri[seciliKategori].baslik} (${sonuclar.length})`;

      if (sonuclar.length === 0) {
        listeAlani.innerHTML = `
          <div class="bos">
            <div style="font-size: 38px; margin-bottom: 10px;">🔎</div>
            Aramanıza uygun bir yer bulunamadı.
          </div>
        `;
        return;
      }

      listeAlani.innerHTML = sonuclar.map((kurum) => {
        const bilgi = kategoriBilgileri[kurum.kategori];

        const haritaAdresi = encodeURIComponent(
          `${kurum.ad}, ${kurum.adres}`
        );

        const temizTelefon = kurum.telefon.replace(/[^0-9+]/g, "");

        const telefonButonu = temizTelefon
          ? `
            tel:${temizTelefon}
              ☎️ Ara
            </a>
          `
          : "";

        return `
          <article class="kart">
            <div class="kart-ust">
              <div class="simge">${bilgi.simge}</div>

              <div>
                <h3>${guvenliMetin(kurum.ad)}</h3>
                <span class="tur">${bilgi.tur}</span>
              </div>
            </div>

            <p class="bilgi">
              📌 ${guvenliMetin(kurum.adres)}
            </p>

            <div class="butonlar"
              style="${temizTelefon ? "" : "grid-template-columns: 1fr;"}"
            >
              https://www.google.com/maps/search/?api=1&query=${haritaAdresi}
                🗺️ Haritada Aç
              </a>

              ${telefonButonu}
            </div>
          </article>
        `;
      }).join("");
    }

    kategoriButonlari.forEach((buton) => {
      buton.addEventListener("click", () => {
        seciliKategori = buton.dataset.kategori;

        kategoriButonlari.forEach((item) => {
          item.classList.remove("aktif");
        });

        buton.classList.add("aktif");
        aramaAlani.value = "";
        kurumlariGoster();
      });
    });

    aramaAlani.addEventListener("input", kurumlariGoster);

    kurumlariGoster();
  </script>
</body>
</html>
