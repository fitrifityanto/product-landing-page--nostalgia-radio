# Product Landing Page - Nostalgia Radio

Halo semua :wave: ...
di Halaman README.md ini saya akan menjelaskan sedikit tentang koding saya dalam membangun **Halaman Landing Page - Nostalgia Radio**. Sebelumnya saya sudah pernah membuat halaman yang sama dengan materi konten yang sama. kodingan-nya bisa kalian cek di v.1.0. Dan kali ini saya bangun ulang, entahlah, saya hanya ingin membuat ulang saja. hehe..

Oke, disini saya akan menjelaskan sedikit tentang kodingan saya dan beberapa kodingan yang telah saya pelajari. saya masih menggunakan HTML dan CSS saja. saya kira baris kode kodingan saya bakalan berkurang dari yang v.1.0, tapi ternyata kok lebih panjang, hahaha

- [Product Landing Page - Nostalgia Radio](#product-landing-page---nostalgia-radio)
  - [Struktur Markup HTML](#struktur-markup-html)
    - [Header](#header)
    - [main](#main)
    - [footer](#footer)
  - [Style CSS](#style-css)
    - [Style pembungkus utama](#style-pembungkus-utama)
    - [Style Header](#style-header)
    - [Style Hero](#style-hero)
    - [Style Features](#style-features)
    - [Style Howitworks](#style-howitworks)
    - [Style Pricing](#style-pricing)
    - [Style Footer](#style-footer)
  - [Kesimpulan](#kesimpulan)


## Struktur Markup HTML

Dalam struktur HTML Halaman Landing Page ini, saya kelompokkan dalam 3 bagian, yaitu **header**, **main**, **footer**.

### Header

Di dalam header, saya memiliki pembungkus yang saya beri nama class `.header--section`, di dalamnya ada elemen DIV untuk membungkus images yang saya beri nama `.header-img` dan elemen NAV yang saya beri nama `#nav-bar`.

### main

Untuk main, didalamnya saya punya konten inti, yaitu `#hero`, `#features`, `#howitworks`, dan `#pricing`.


- #hero

Di dalam hero, saya punya h1 dan form yang saya bungkus dengan elemen DIV yang saya beri nama `.hero--section`. Lalu itemnya form dengan 1 label, dan 2 input (input type email dan type submit), 3 item ini saya bungkus dengan elemen DIV yang saya beri nama `.form--item`.


- #features

Untuk features, ada 3 `.feature--item` yang di bungkus dengan elemen DIV `.features--section`. Setiap `.feature--item` ada `.feature-item__icon` untuk membungkus images svg icon, dan ada `.feature-item__content` untuk membungkus judul h2 dan deskripsi singkat p.


- #howitworks

Untuk howitworks, ada iframe dengan `id="video"` yang saya bungkus dengan elemen DIV `.howitworks--section`


- #pricing

Pricing, materi ini dalam bentuk card. Jadi ada 3 card yang saya beri nama `.pricing--item` yang ketiganya saya bungkus dengan elemen DIV `.pricing--section`.

Setiap `.pricing--item` berisi pertama, `.pricing-item__title` sebagai pembungkus Judul H2. Lalu kedua, `.pricing-item__content` sebagai pembungkus `.pricing-content__price` (harga H3), `.pricing-content_des` (yang berisi deskripsi 3 paragraf), dan `.pricing-content__btn` (yang berisi button SELECT ).


### footer

Di dalam footer, ada `.footer-link` dan `.footer--brand` yang dibungkus dengan elemen DIV `.footer`.


## Style CSS

### Style pembungkus utama

Setiap pembungkus-pembungkus konten, saya bungkus dengan `.fluid` (yang lebar) dan `.container`. Keduanya saya atur style-nya seperti ini :

```css
.fluid {
    margin-inline: max(.6rem, 50% - 85rem/2);
}

.container {
    margin-inline: max(1rem, 50% - 60rem/2);
}
```

1 baris kode di dalam fluid dan container, saya dapatkan dari [ChallengesCss](https://twitter.com/ChallengesCss/status/1469270181205749771?s=20&t=zjqjggXRwjobeM5H67PpYA)

untuk fluid punya max-width 85rem, sedangkan container punya max-width 60rem. margin-inline adalah margin secara horizontal (left dan right). Disini, fluid memiliki margin-inline tambahan pada ukuran layar yang lebih besar dari 85rem dan mempertahankan margin-inline minimum yaitu .6rem pada ukuran layar yang lebih kecil dari 85rem. Jadi max() memilih nilai terbesar (nilai positif) dari daftar ekspresi yang dipisahkan dengan koma.

Misal, saat viewport lebarnya 1440px. Berarti nilai margin-inline kedua adalah 720px (59% dari 1440px) dikurangi 680px (85rem dibagi 2) sama dengan 40px. Jadi Saat viewport 1440px, nilai margin-inline yang menang adalah 40px (left / right). Saat viewport lebarnya 85rem (1360px), berarti nilai margin-inline kedua adalah 680px (50% dari 1360px) dikurangi 680px (85rem dibagi 2) sama dengan 0px. Jadi saat viewportnya 1360px, nilai margin-inline yang menang adalah .6rem (left / right).

yup, ini rumus yang ajaib banget kan.


### Style Header

Untuk `.header--section` yang didalamnya ada `.header-img` dan `#nav-bar`, saya atur display nya grid. Dengan `grid-template-columns: repeat(2, 1fr);` yang saya atur di media Desktop dan tablet. 

Untuk `#nav-bar ul` saya atur display nya flex dengan `flex-direction:column`, kecuali pada media Desktop, `flex-direction:row` dan `justify-content: space-around;`.


### Style Hero 

Tidak ada yang special pada styling hero disini. Saya hanya mengatur si pembungkus form, yaitu `.form--item` dengan display grid.


### Style Features

Untuk `features--section` saya atur display nya grid dengan gap 2rem. lalu untuk setiap `feature--item` saya atur displaynya flex. Dimana pengaturan lebar itemnya, yaitu `.feature-item__icon` dan `.feature-item__content` saya taruh di Media Desktop

```css
.feature-item__icon {
        flex: 0 1 288px;
    }
    
    .feature-item__content {
        flex: 0 1 617px;
    }
```

Si pembungkus icon lebarnya 288px, bisa shrink (menciut) saat viewportnya berkurang. Dan si pembungkus content lebarnya 617px, bisa shrink (menciut) saat viewportnya berkurang.

Sedangkan saat Media Mobile, `feature--item`, saya atur `flex-direction: column;`


### Style Howitworks

Disini pengaturan responsive untuk ukuran video adalah

```css
#video {   
    max-width: 560px;
    width: 100%;
}
```


### Style Pricing

Dalam styling pricing ini, cukup memakan waktu bagi saya, hehe.. karena saya tidak ingin susunan card nya turun satu, dan itu membuat tampilannya tidak enak dilihat. jadi saya putuskan untuk tidak memakai flex-wrap.

Untuk `.pricing--section` saya atur display nya flex, dengan `align-items: center;` , `justify-content: center;`, dan `gap: 3rem;`. 

Kemudian untuk `.pricing--item` saya atur `width: 250px` dan `flex: 0 1 auto`

Jadi lebar kotak cardnya 250px, dia tidak bisa grow, tapi bisa shrink (menciut) saat viewport nya berkurang. Tapi, saat viewport mencari Media Table dan Mobile, saya atur `flex-direction: column;` pada `.pricing--section`, agar tampilan cardnya turun kebawah semua dengan mempertahankan width 250px.


### Style Footer

Disinipun juga tidak ada yang special. saya atur sipembungkus yaitu `.footer` dengan display grid, dan `justify-content: end;`

Lalu `.footer-link ul` saya atur displaynya flex, dengan `justify-content: end;` dan `gap: 1rem;`


## Kesimpulan

Bagi saya, membangun halaman dengan HTML dan CSS merupakan hal yang seru, semetara ini terkadang saya masih kebingungan dalam memahami arti dari property css, hahaha.. apakah saya kurang latihannya. Mungkin itu termasuk alasannya. Oleh karena itu, saya buat penjelasan dalam README.md ini agar saya bisa baca ulang, dan semoga juga bisa bermanfaa untuk kalian, yang membaca.

Preview : [Landing Page - Nostalgia Radio](https://fitrifityanto.github.io/product-landing-page--nostalgia-radio/)

Code : [Repository di GitHub saya](https://github.com/fitrifityanto/product-landing-page--nostalgia-radio)

