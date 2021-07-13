<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
</p>

# Uzman CSS Tavsiyelerin [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

CSS becerilerinizi profesyonel hale getirmenize yardımcı olacak ipuçları koleksiyonu.

> Diğer yararlı listeler İçin [@sindresorhus](https://github.com/sindresorhus/)'un [awesome lists](https://github.com/sindresorhus/awesome/)'ine göz atın.


## İçindekiler

* [Tavsiyeler](#tavsiyeler)
* [Desteklenenler](#desteklenenler)
* [Çeviriler](#çeviriler)
* [Katkı Rehberi](../../CONTRIBUTING.md)


## Tavsiyeler

1. [CSS Sıfırlama Kullanın](#use-a-css-reset)
1. [`box-sizing`'i Kalıtın](#inherit-box-sizing)
1. [Tüm Özellikleri Sıfırlamak Yerine `unset` Kullanın](#use-unset-instead-of-resetting-all-properties)
1. [Navigasyona Border Eklemek veya Kaldırmak İçin `:not()` Kullanın](#use-not-to-applyunapply-borders-on-navigation)
1. [Font'un Lokal Olarak Yüklenip Yüklenmediğini Kontrol Edin](#check-if-font-is-installed-locally)
1. [`body`'ye `line-height` Ekleyin](#add-line-height-to-body)
1. [Form Elemanları İçin `:focus` Ekleyin](#set-focus-for-form-elements)
1. [Her Şeyi Dikey Ortalayın](#vertically-center-anything)
1. [Listeleri Virgül İle Ayırın](#comma-separated-lists)
1. [`nth-child` Kullanarak Elemanları Native Olarak Seçin](#select-items-using-negative-nth-child)
1. [İkonlar İçin SVG Kullanın](#use-svg-for-icons)
1. ["Lobotomized Owl" Seçicisini Kullanın](#use-the-lobotomized-owl-selector)
1. [Pure CSS Slider'lar İçin `max-height` Kullanın](#use-max-height-for-pure-css-sliders)
1. [Tablo Hücrelerinin Genişliklerini Eşitleyin](#equal-width-table-cells)
1. [Flexbox İle Margin'den Kurtulun](#get-rid-of-margin-hacks-with-flexbox)
1. [Boş Linkler İle Attribute Selector'larini Kullanın](#use-attribute-selectors-with-empty-links)
1. [Link'lerin varsayılan halini stillendirin](#style-default-links)
1. [Intrinsic Ratio Box'ları](#intrinsic-ratio-boxes)
1. [Hatalı Image'leri stillendirin](#style-broken-images)
1. [Global Boyutlandırma İçin `rem` Kullanın; Lokal Boyutlandırma İçin `em` Kullanın](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Sesi Kapatılmayan Otomatik Oynatılan Videoları Gizleyin](#hide-autoplay-videos-that-arent-muted)
1. [Flexible Ögeler İçin `:root` Kullanın ](#use-root-for-flexible-type)
1. [Daha İyi Bir Mobil Kullanım İçin  Form Elemanlarının `font-size`'ını Ayarlayın](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [Fare Olayları İçin Pointer Event'larını Kullanın](#use-pointer-events-to-control-mouse-events)
1. [Line Break'leri boşluk olarak kullanmak için `display: none` kullanın](#set-display-none-on-line-breaks-used-as-spacing)


### CSS Sıfırlama Kullanın

CSS sıfırlamaları, stil öğeleri için temiz bir sayfa ile farklı tarayıcılar arasında stil tutarlılığının sağlanmasına yardımcı olur. [Normalize](http://necolas.github.io/normalize.css/) CSS sıfırlama kütüphaneleri kullanabilirsiniz veya daha basit bir sıfırlama yöntemini tercih edebilirsiniz :

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Şimdi elementler padding ve margin ayrıldı, `box-sizing` ile CSS box model düzenini kontrol edebilirsiniz.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Not:** Eğer [kalıtsal olarak `box-sizing`](#inherit-box-sizing) kullanılıyorsanız CSS sıfırlamaya `box-sizing` eklemenize gerek yok.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### `box-sizing`'i Kalıtın

Hadi `box-sizing`'i `html`'den kalıtalım:

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

Bu eklentilerdeki veya komponentlerdeki `box-sizing`'i değiştirmeyi kolaylaştırır.

#### [Demo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Tüm Özellikleri Sıfırlamak Yerine `unset` Kullanın

Bir elemanın özelliklerini sıfırlarken, her bir özelliği ayrı ayrı sıfırlamak gerekli değildir:

```css
button {
  background: none;
  border: none;
  color: inherit;
  font: inherit;
  outline: none;
  padding: 0;
}
```

`all` kullanarak bir elemanın tüm özelliklerini belirtebilirsiniz.Değerini `unset` olarak ayarlamak elemanı başlangıçtaki özelliklerine döndürür.

```css
button {
  all: unset;
}
```

**Not:** `all` ve `unset` kısayolları IE11 tarafından desteklenmemektedir.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Navigasyona Border Eklemek veya Kaldırmak İçin `:not()` Kullanın

Tüm navigasyona Border ekledik ...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

... ve navigasyon içindeki son elemandan border'ı kaldırdık...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

... Bunu yerine istemediğiniz eleman için `:not()` pseudo sınıfını ekleyin ve o hariç tüm eleman etkilensin.

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

İşte daha okunabilir bir CSS seçicisi.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Font'un Lokal Olarak Yüklenip Yüklenmediğini Kontrol Edin

Bir yazı tipini indirmeden önce yerel olarak yüklenip yüklenmediğini kontrol edebilirsiniz, bu performansınızı iyi bir şekilde etkileyecektir.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* Full name */
    local("Dank Mono"),
    /* Postscript name */
    local("Dank Mono"),
    /* Otherwise, download it! */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

Bu ipucunu paylaştığı için Adam Argyle'a sonsuz teşekkürler, [demo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### `body`'ye `line-height` Ekleyin

Her bir `<p>`, `<h*>`, vb. elemana `line-height` eklemenize gerek yok. `body`'e eklemeniz yeterli olacaktır.

```css
body {
  line-height: 1.5;
}
```

Metinsel elemanlar `body`'den kalıtım alacaklardır.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Form Elemanları İçin `:focus` Ekleyin

Deneyimli kullanıcılar sayfada ilerlemek için klavyeyi kullanır ve bir sonraki adımın neresi olduğunu `focus` sayesinde anlarlar. Bir tarayıcının varsayılan uygulamasından sonra form öğelerinin öne çıkmasını ve tutarlı olmasını sağlayın:

```css
a:focus,
button:focus,
input:focus,
select:focus,
textarea:focus {
  box-shadow: none;
  outline: #000 dotted 2px;
  outline-offset: .05em;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Her Şeyi Dikey Ortalayın

Hayır, bu bir kara büyü değil, gerçekten elemanları dikey ortalamanın bir yolu var.Flexbox kullanarak bunu yapabilirsin...

```css
html,
body {
  height: 100%;
  margin: 0;
}

body {
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  display: -webkit-flex;
  display: flex;
}
```

...CSS Grid ile de yapılabilir:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Başka bir şeyi ortalamak mı istiyorsun? Dikey, yatay...herhangi bir şey, herhangi bir zaman, herhangi bir yerde? CSS-Tricks bunları nasıl yapacağını [güzelce yazmış](https://css-tricks.com/centering-css-complete-guide/).

**Not:** IE11 için hatalı flexbox kullanımı ile ilgili şu [videoyu](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) izleyebilirsin.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Listeleri Virgül İle Ayırın

Listelerinizi gerçekçi göstermek için comma-separated kullanın:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Son elemana da virgül eklememek için `:not()` pseudo sınıfını kullanın

**Not:** Bu ipucu, erişilebilirlik, özellikle ekran okuyucular için ideal olmayabilir ve kopyala/yapıştır CSS tarafından oluşturulan içerikle çalışmaz. Bunları göz önünde tut.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### `nth-child` Kullanarak Elemanları Native Olarak Seçin

CSS içinde 1'den n. elemana seçim yapmak için native olarak desteklenen `nth-child`'ı kullanın

```css
li {
  display: none;
}

/* 1'den 3'e kadar olan öğeleri seçin ve görüntüleyin */
li:nth-child(-n+3) {
  display: block;
}
```

Veya zaten öğrendiğimiz [`:not()`'ı](#use-not-to-applyunapply-borders-on-navigation) deneyebiliriz:

```css
/* ilk üç eleman dışındaki tüm elemanları seçer ve gösteriri */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### İkonlar İçin SVG Kullanın

İkonlar için SVG kullanmamanın bir nedeni yok:

```css
.logo {
  background: url("logo.svg");
}
```

SVG, tüm çözünürlük türleri için iyi ölçeklenir ve [IE9'a kadar](http://caniuse.com/#search=svg) tüm tarayıcılarda desteklenir. png, jpg, veya .gif-jif- her neyse gibi dosya tiplerini terk edin.

**Not:** Eğer SVG kullanıyorsanız ve yüklenmiyorsa bu erişebilirliğin korunmasına yardımcı olur:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Use the "Lobotomized Owl" Selector

It may have a strange name but using the universal selector (`*`) with the adjacent sibling selector (`+`) can provide a powerful CSS capability:

```css
* + * {
  margin-top: 1.5em;
}
```

In this example, all elements in the flow of the document that follow other elements will receive `margin-top: 1.5em`.

For more on the "lobotomized owl" selector, read [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) on *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Use `max-height` for Pure CSS Sliders

Implement CSS-only sliders using `max-height` with overflow hidden:

```css
.slider {
  max-height: 200px;
  overflow-y: hidden;
  width: 300px;
}

.slider:hover {
  max-height: 600px;
  overflow-y: scroll;
}
```

The element expands to the `max-height` value on hover and the slider displays as a result of the overflow.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Equal-Width Table Cells

Tables can be a pain to work with. Try using `table-layout: fixed` to keep cells at equal width:

```css
.calendar {
  table-layout: fixed;
}
```

Pain-free table layouts.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Get Rid of Margin Hacks With Flexbox

When working with column gutters you can get rid of `nth-`, `first-`, and `last-child` hacks by using flexbox's `space-between` property:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Now column gutters always appear evenly-spaced.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Use Attribute Selectors with Empty Links

Display links when the `<a>` element has no text value but the `href` attribute has a link:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

That's pretty convenient.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Style "Default" Links

Add a style for "default" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Now links that are inserted via a CMS, which don't usually have a `class` attribute, will have a distinction without generically affecting the cascade.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Intrinsic Ratio Boxes

To create a box with an intrinsic ratio, all you need to do is apply top or bottom padding to a div:

```css
.container {
  height: 0;
  padding-bottom: 20%;
  position: relative;
}

.container div {
  border: 2px dashed #ddd;
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
```

Using 20% for padding makes the height of the box equal to 20% of its width. No matter the width of the viewport, the child div will keep its aspect ratio (100% / 20% = 5:1).

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Style Broken Images

Make broken images more aesthetically-pleasing with a little bit of CSS:

```css
img {
  display: block;
  font-family: sans-serif;
  font-weight: 300;
  height: auto;
  line-height: 2;
  position: relative;
  text-align: center;
  width: 100%;
}
```

Now add pseudo-elements rules to display a user message and URL reference of the broken image:

```css
img::before {
  content: "We're sorry, the image below is broken :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Learn more about styling for this pattern in [Ire Aderinokun](https://github.com/ireade/)'s [original post](http://bitsofco.de/styling-broken-images/).

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Use `rem` for Global Sizing; Use `em` for Local Sizing

After setting the base font size at the root (`html { font-size: 100%; }`), set the font size for textual elements to `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Then set the font-size for modules to `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Now each module becomes compartmentalized and easier to style, more maintainable, and flexible.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Hide Autoplay Videos That Aren't Muted

This is a great trick for a custom user stylesheet. Avoid overloading a user with sound from a video that autoplays when the page is loaded. If the sound isn't muted, don't show the video:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Once again, we're taking advantage of using the [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-class.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Use `:root` for Flexible Type

The type font size in a responsive layout should be able to adjust with each viewport. You can calculate the font size based on the viewport height and width using `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Now you can utilize the `root em` unit based on the value calculated by `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Set `font-size` on Form Elements for a Better Mobile Experience

To avoid mobile browsers (iOS Safari, _et al_.) from zooming in on HTML form elements when a `<select>` drop-down is tapped, add `font-size` to the selector rule:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Use Pointer Events to Control Mouse Events

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) allow you to specify how the mouse interacts with the element it's touching. To disable the default pointer event on a button, for instance:

```css
.button-disabled {
  opacity: .5;
  pointer-events: none;
}
```

It's that simple.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


### Set `display: none` on Line Breaks Used as Spacing

As [Harry Roberts pointed out](https://twitter.com/csswizardry/status/1170835532584235008), this can help prevent CMS users from using extra line breaks for spacing:

```css
br + br {
  display: none;
}
```

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


## Desteklenenler

Chrome, Firefox, Safari, Opera, Edge tarayıcılarının güncel versiyonları ve IE11.

<sup>[İçindekilere geri dön](#table-of-contents)</sup>


## Çeviriler

* [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)
* [正體中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-TW)
* [Deutsch](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/de-DE)
* [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
* [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
* [λληνικά](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gr-GR)
* [ગુજરાતી](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gu-IND)
* [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
* [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
* [한국어](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ko-KR)
* [Polskie](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pl-PL)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Português do Europe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-PT)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [Tiếng Việt](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/vn-VN)
* [Türkçe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/tr-TR)

<sup>[İçindekilere geri dön](#table-of-contents)</sup>
