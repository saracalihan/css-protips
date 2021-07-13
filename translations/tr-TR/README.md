<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
</p>

# Uzman CSS Tavsiyeleri [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

CSS becerilerinizi profesyonel hale getirmenize yardımcı olacak ipuçları koleksiyonu.

> Diğer yararlı listeler İçin [@sindresorhus](https://github.com/sindresorhus/)'un [awesome lists](https://github.com/sindresorhus/awesome/)'ine göz atın.


## İçindekiler

* [Tavsiyeler](#tavsiyeler)
* [Desteklenenler](#desteklenenler-tarayıcıları)
* [Çeviriler](#çeviriler)
* [Katkı Rehberi](../../CONTRIBUTING.md)


## Tavsiyeler

1. [CSS Sıfırlama Kullanın](#css-sıfırlama-kullanın)
1. [`box-sizing`'i Kalıtın](#box-sizingi-kalıtın)
1. [Tüm Özellikleri Sıfırlamak Yerine `unset` Kullanın](#tüm-özellikleri-sıfırlamak-yerine-unset-kullanın)
1. [Navigasyona Border Eklemek veya Kaldırmak İçin `:not()` Kullanın](#navigasyona-border-eklemek-veya-kaldırmak-i̇çin-not-kullanın)
1. [Font'un Lokal Olarak Yüklenip Yüklenmediğini Kontrol Edin](#fontun-lokal-olarak-yüklenip-yüklenmediğini-kontrol-edin)
1. [`body`'ye `line-height` Ekleyin](#bodyye-line-height-ekleyin)
1. [Form Elemanları İçin `:focus` Ekleyin](#form-elemanları-i̇çin-focus-ekleyin)
1. [Her Şeyi Dikey Ortalayın](#her-şeyi-dikey-ortalayın)
1. [Listeleri Virgül İle Ayırın](#listeleri-virgül-i̇le-ayırın)
1. [`nth-child` Kullanarak Elemanları Native Olarak Seçin](#nth-child-kullanarak-elemanları-native-olarak-seçin)
1. [İkonlar İçin SVG Kullanın](#i̇konlar-i̇çin-svg-kullanın)
1. ["Lobotomized Owl" Seçicisini Kullanın](#lobotomized-owl-seçicisini-kullanın)
1. [Pure CSS Slider'lar İçin `max-height` Kullanın](#pure-css-sliderlar-i̇çin-max-height-kullanın)
1. [Tablo Hücrelerinin Genişliklerini Eşitleyin](#tablo-hücrelerinin-genişliklerini-eşitleyin)
1. [Flexbox İle Margin'den Kurtulun](#flexbox-i̇le-marginden-kurtulun)
1. [Boş Linkler İle Attribute Selector'larini Kullanın](#boş-linkler-i̇le-attribute-selectorlarini-kullanın)
1. [Link'lerin varsayılan halini stillendirin](#linklerin-varsayılan-halini-stillendirin)
1. [Intrinsic Ratio Box'ları](#intrinsic-ratio-boxları)
1. [Bozuk Image'leri stillendirin](#bozuk-imageleri-stillendirin)
1. [Global Boyutlandırma İçin `rem` Kullanın; Lokal Boyutlandırma İçin `em` Kullanın](#global-boyutlandırma-i̇çin-rem-kullanın-lokal-boyutlandırma-i̇çin-em-kullanın)
1. [Sesi Kapatılamayan Otomatik Oynatılan Videoları Gizleyin](#sesi-kapatılamayan-otomatik-oynatılan-videoları-gizleyin)
1. [Flexible Ögeler İçin `:root` Kullanın](#flexible-ögeler-i̇çin-root-kullanın)
1. [Daha İyi Bir Mobil Deneyim İçin Form Elemanlarının `font-size`'ını Ayarlayın](#daha-i̇yi-bir-mobil-deneyim-i̇çin-form-elemanlarının-font-sizeını-ayarlayın)
1. [Fare Olayları İçin Pointer Event'larını Kullanın](#fare-olayları-i̇çin-pointer-eventlarını-kullanın)
1. [Line Break'leri boşluk olarak kullanmak için `display: none` kullanın](#line-breakleri-boşluk-olarak-kullanmak-için-display-none-kullanın)


### CSS Sıfırlama Kullanın

CSS sıfırlama, stil öğeleri için temiz bir sayfa ile farklı tarayıcılar arasında stil tutarlılığının sağlanmasına yardımcı olur. [Normalize](http://necolas.github.io/normalize.css/) gibi CSS sıfırlama kütüphaneleri kullanabilirsiniz veya daha basit bir sıfırlama yöntemini tercih edebilirsiniz :

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Şimdi elementler padding'den ve margin'den sıyrıldı, `box-sizing` ile CSS box model düzenini kontrol edebilirsiniz.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Not:** Eğer [kalıtsal olarak `box-sizing`](#box-sizingi-kalıtın) kullanılıyorsanız CSS sıfırlamaya `box-sizing` eklemenize gerek yok.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


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

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


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

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Navigasyona Border Eklemek veya Kaldırmak İçin `:not()` Kullanın

Tüm navigasyona Border ekledik ...

```css
/* border ekle */
.nav li {
  border-right: 1px solid #666;
}
```

... ve navigasyon içindeki son elemandan border'ı kaldırdık...

```css
/* border kaldır */
.nav li:last-child {
  border-right: none;
}
```

... Bunu yerine istemediğiniz eleman için `:not()` pseudo kodunu ekleyin ve o hariç tüm eleman etkilensin.

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

İşte karşınızda daha okunabilir bir CSS.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Font'un Lokal Olarak Yüklenip Yüklenmediğini Kontrol Edin

Bir yazı tipini kaynağından indirmeden önce yerel olarak yüklenip yüklenmediğini kontrol edebilirsiniz, bu performansınızı iyi bir şekilde etkileyecektir.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* tam ad */
    local("Dank Mono"),
    /* Postscript ad */
    local("Dank Mono"),
    /* server'dan indir */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

Bu ipucunu paylaştığı için Adam Argyle'a şukranlarımızı sunarız, [demo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### `body`'ye `line-height` Ekleyin

Her bir `<p>`, `<h*>`, vb. elemana `line-height` eklemenize gerek yok. `body`'e eklemeniz yeterli olacaktır.

```css
body {
  line-height: 1.5;
}
```

Tüm metinsel elemanlar `body`'den kalıtım alacaklardır.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Form Elemanları İçin `:focus` Ekleyin

Deneyimli kullanıcılar sayfada ilerlemek için klavyeyi kullanırlar ve bir sonraki adımın neresi olduğunu `focus` sayesinde anlarlar. Bir tarayıcının varsayılan uygulamasından sonra form öğelerinin öne çıkmasını ve tutarlı olmasını sağlayın:

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

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


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

Başka bir şeyi ortalamak mı istiyorsun? herhangi bir yerde, herhangi bir zamanda, dikey, yatay hiç farketmez. CSS-Tricks bunları nasıl yapacağını [güzelce yazmış](https://css-tricks.com/centering-css-complete-guide/).

**Not:** IE11 için hatalı flexbox kullanımı ile ilgili şu [videoyu](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) izleyebilirsin.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Listeleri Virgül İle Ayırın

Listelerinizi gerçekçi göstermek için virgül kullanın:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Son elemana da virgül eklememek için `:not()` pseudo sınıfını kullanın

**Not:** Bu ipucu, erişilebilirlik, özellikle ekran okuyucular için ideal olmayabilir ve kopyala/yapıştır CSS tarafından oluşturulan içerikle çalışmaz. Geliştirme yaparken bunları göz önünde bulundur.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


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

Veya zaten öğrendiğimiz [`:not()`'ı](#unavigasyona-border-eklemek-veya-kaldırmak-i̇çin-not-kullanın) deneyebiliriz:

```css
/* ilk üç eleman dışındaki tüm elemanları seçer ve gösterir */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### İkonlar İçin SVG Kullanın

İkonlar için SVG kullanmamanın mantıklıca bir nedeni yok:

```css
.logo {
  background: url("logo.svg");
}
```

SVG, tüm çözünürlük türleri için çok daha iyi ölçeklenir ve [IE9'a kadar](http://caniuse.com/#search=svg) tüm tarayıcılarda desteklenir. png, jpg veya .gif-jif(artık her neyse) gibi dosya tiplerini kullanmayı derhal terk edin.

**Not:** Eğer SVG kullanıyorsanız ve yüklenmiyorsa aşağıdaki kod erişebilirliğin korunmasına yardımcı olur:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### "Lobotomized Owl" Seçicisini Kullanın

Garip bir adı olabilir, ancak evrensel seçiciyi (*) komşu seçiciyle (+) kullanmak güçlü bir CSS yeteneği sağlayabilir.

```css
* + * {
  margin-top: 1.5em;
}
```

Bu örnekte, document üzerindeki diğer öğeleri takip eden tüm öğeler `margin-top: 1.5em` olarak ayarlanır.

"Lobotomized owl" seçicisi hakkında daha fazla bilgi için *A List Apart*'ta bulunan [Heydon Pickering'in paylaşımını](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) okuyabilirsiniz.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Pure CSS Slider'lar İçin `max-height` Kullanın

Yalnızca CSS kullanarak yaptığınız Slider'ınıza `max-height` ekleyerek gizlenebilir hale getirebilirsiniz:

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

üzerine gelindiğinde `max-height` değerine genişler ve taşmanın(overflow) bir sonucu olarak kaydırıcı görüntülenir.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Tablo Hücrelerinin Genişliklerini Eşitleyin

Tablolar çalışmak sancılıdır. Hücreleri eşit genişlikte tutmak için `table-layout: fixed` kullanmayı deneyin:

```css
.calendar {
  table-layout: fixed;
}
```

İşte karşınızda acısız bir tablo düzeni.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Flexbox İle Margin'den Kurtulun

Sütunlar ile çalışırken flexbox'ın `space-between` özelliğini kullanarak `nth-`, `first-` ve `last-child` hack'lerden kurtulabilirsiniz:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Artık sütun olukları her zaman eşit aralıkta görünür.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Boş Linkler İle Attribute Selector'larini Kullanın

`<a>` öğesinin metin değeri olmadığında ama `href` attribute'ü olduğunda da bağlantıları görüntüleyin:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Bu oldukça kullanışlıdır.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Link'lerin varsayılan halini stillendirin

Link'ler için varsayılan stil ekleyin:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Artık `class` özniteliğine sahip olmayan bir CMS aracılığıyla eklenen bağlantılar, genel olarak etkilemeden bir farklılığa sahip olacaklar.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Intrinsic Ratio Box'ları

Gerçek orana sahip bir kutu oluşturmak için tek yapmanız gereken bir div'e üst veya alt `padding` uygulamaktır:

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

Padding için %20 kullanmak, kutunun yüksekliğini genişliğinin %20'sine eşit yapar. Görüntü alanının genişliği ne olursa olsun, alt div en boy oranını (%100 / %20 = 5:1) koruyacaktır.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Bozuk Image'leri stillendirin

Biraz CSS ile çalışmayan görüntüleri daha estetik hale getirin:

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

Şimdi, bozuk görüntünün bir kullanıcı mesajını ve URL referansını görüntülemek için sözde öğeler kuralları ekleyin:

```css
img::before {
  content: "Üzgünüz, resim bulunamıyor veya açılamıyor :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```
[Ire Aderinokun](https://github.com/ireade/)'un [orijinal gönderisinde](http://bitsofco.de/styling-broken-images/) bu modelin stili hakkında daha fazla bilgi edinin.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Global Boyutlandırma İçin `rem` Kullanın; Lokal Boyutlandırma İçin `em` Kullanın

Base'de temel yazı tipi boyutunu ayarladıktan sonra (`html { yazı tipi boyutu: %100; }`) metin öğeleri için yazı tipi boyutunu `em` olarak ayarlayın:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Ardından modüllerin yazı tipi boyutunu `rem` ile ayarlayın:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Artık her modül bölümlere ayrılmış ve stili daha kolay, bakımı daha kolay ve esnek hale geliyor.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Sesi Kapatılamayan Otomatik Oynatılan Videoları Gizleyin

Bu, özel bir kullanıcı stil sayfası için harika bir ipucudur. Sayfa yüklendiğinde otomatik olarak oynatılan bir videodan gelen sesle kullanıcıyı aşırı yormaktan kaçının. Ses kapatılmamışsa videoyu göstermeyin:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Flexible Ögeler İçin `:root` Kullanın

Cihaz boyutuna duyarlı bir tasarımda font boyutu her bir görünüm penceresiyle ayarlanabilmelidir. Font boyutunu görünüm penceresinin yüksekliğine ve genişliğine göre `:root` kullanarak hesaplayabilirsiniz:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Artık `root em` birimini `:root` tarafından hesaplanan değere göre kullanabilirsiniz:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Daha İyi Bir Mobil Deneyim İçin Form Elemanlarının `font-size`'ını Ayarlayın

Bir `<select>` açılır menüsüne dokunulduğunda mobil tarayıcıların (iOS Safari ve diğerleri) HTML form öğelerini yakınlaştırmasını önlemek için `font-size` ekleyin:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Fare Olayları İçin Pointer Event'larını Kullanın

[İşaretçi olayları](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events), farenin dokunduğu öğeyle nasıl etkileşime gireceğini belirtmenize olanak tanır.Örneğin bir düğmeye basarak varsayılan işaretçi olayını devre dışı bırakmak için:

```css
.button-disabled {
  opacity: .5;
  pointer-events: none;
}
```

Bu kadar basit

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


### Line Break'leri boşluk olarak kullanmak için `display: none` kullanın
[Harry Roberts'ın de belirttiği gibi](https://twitter.com/csswizardry/status/1170835532584235008), bu, CMS kullanıcılarının boşluk için fazladan satır sonları kullanmasını önlemeye yardımcı olabilir:

```css
br + br {
  display: none;
}
```

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


## Desteklenenler Tarayıcılar

Chrome, Firefox, Safari, Opera, Edge tarayıcılarının güncel versiyonları ve IE11.

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>


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

<sup>[İçindekilere geri dön](#i̇çindekiler)</sup>
