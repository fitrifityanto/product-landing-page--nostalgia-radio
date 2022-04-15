# Product Landing Page - Nostalgia Radio
---
Product Landing Page ini saya buat untuk memenuhi project di Freecodecamp, yaitu [Build a product landing page](https://www.freecodecamp.org/learn/responsive-web-design/responsive-web-design-projects/build-a-product-landing-page).

Assets icon di landing page ini saya mendownloadnya di [iconscout.com](https://iconscout.com/).

### Beberapa code yang menarik perhatian saya
* untuk menampilkan video (meskipun pada device dibawah 560px, tampilannya tidak sesuai rasio :D)

```html
<div class="container-video">
            <iframe id="video" src="https://www.youtube.com/embed/OnIwEWQONqU" height="315"></iframe>
        </div>
```

```css
.container-video > iframe {
    max-width: 560px;
    width: 100%;
}
```

* menampilkan card pada device ukuran maksimal lebar 50em

```css
.container-pricing {
        flex-direction: column;
        align-items: center;
        gap: 1.6rem;
    }
    
    .items-pricing {
        width: calc(100% / 1.5);
    }
```