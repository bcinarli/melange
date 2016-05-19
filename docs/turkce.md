# Melange
Melange CSS kodlaması için kullanılabilecek bir kütüphaneden (framework) çok bir tasarım mimarisidir. Tekrar kullanılabilmeyi, gereksiz kod yazımının azaltılması, büyük sistemlerde geliştirmeyi hızlandırmayı ve geniş ayar imkanı ile sistem genelinde ortak geliştirme dili ve değişkenleri kullanabilmeyi amaçlayarak hazırlanmıştır.

## Dosya ve Klasör Yapısı
Temel Melange mimarisi, geliştirmeler için yapılacak klasör yapısına örnek teşkil edecek şekilde hazırlanmıştır. Melange'ı uygulamanıza ekledikten sonra, kullanabileceğiniz örnek yapı [Melange Sample](https://github.com/bcinarli/melange-sample/tree/master/source/scss) çalışması altında gösterilmiştir.

Uygulama içinde genel komponentler ve bunlara bağlı atomik partiküller şeklinde atomik dizayn prensiplerine göre düzenlenmiştir. Bu kurgu içinde [atom] -> [partikül] -> [component] -> [layout] -> [sayfa] sıralamasıyla geliştirmeler yapılmalıdır.

Klasörlerin her birinin içinde klasör ile aynı isimde bir _container_ `scss` dosyası bulunmaktadır. Bu klasör içindeki diğer bütün `scss` dosyaları, bu _container_ içerisine eklenmelidir. Yine bir üst klasör içindeki _container_ dosyasına ya da ana stil dosyasına sadece bu _container_ dosyaları `import` edilmelidir.

Standart klasör yapısı;  
_Klasörler içerisindeki bazı dosyaların içi boştur. Bunlar sadece kendi uygulamanızı geliştirirken, klasör ve dosya kurgusunun nasıl yapılacağına örnek teşkil etmesi için konuşmuştur._
```
.  
|-- _melange.scss  
|-- settings  
|   |-- _animations.scss  
|   |-- _breakpoints.scss  
|   |-- _colors.scss  
|   |-- _fonts.scss  
|   |-- _namespace.scss  
|   |-- _settings.scss  
|   |-- _sizes.scss  
|   '-- _supports.scss  
'-- melange  
    |-- auxiliary
    |   |-- _auxiliary.scss  
    |   '-- _visibility.scss
    |-- components  
    |   |-- _components.scss
    |   '-- _media.scss
    |-- elements  
    |   |-- forms
    |   |   |-- _buttons.scss
    |   |   |-- _fields.scss
    |   |   |-- _forms.scss
    |   |   |-- _inputs.scss
    |   |   '-- _labels.scss
    |   |-- _block.scss
    |   |-- _elements.scss
    |   |-- _headings.scss
    |   |-- _inline.scss
    |   |-- _links.scss
    |   |-- _lists.scss
    |   |-- _tables.scss
    |   '-- _texts.scss
    |-- globals  
    |   |-- _generic.scss
    |   |-- _globals.scss
    |   |-- _helpers.scss
    |   |-- _normalize.scss
    |   '-- _positions.scss
    |-- layout  
    |   |-- _grid.scss
    |   |-- _layout.scss
    |   '-- _widths.scss
    '-- variables 
        |-- _animations.scss
        |-- _breakpoints.scss
        |-- _colors.scss
        |-- _fonts.scss
        |-- _internal.scss
        |-- _namespace.scss
        |-- _number-to-names.scss
        |-- _sizes.scss
        |-- _supports.scss
        '-- _variables.scss
```
Buradaki klasörlerin içerikleri özetle;
* __settings__: Melange'ın stnadart olarak kullandığı değişkenlerin değerlerini kendi tasarımınız ve uygulamanıza göre değiştirebileceğiniz ayarların bulunduğu dosyalar.
* __melange__: Melange mimarisi genel dosya ve klasörleri
  * _auxiliary_: Genel olarak HTML/Sayfa elemanlarının sayfadaki görünümlerinin son/final (pluginlere eklenen gösterme/gizleme gibi) biçimlerini tanımlar. `is-hidden`, `for-screen-readers-only` gibi, başka stilleri ezecek mutlak sonuçları barındırır.
  * _components_: Default komponentleri barındırır. Geliştirmeyi serbest bırakmak ve geliştiriciyi gereksiz HTML yapıları ile kısıtlamamak için Melange içinde mümkün olduğunca az ön tanımlı yapı bulunmaktadır. 
  * _elements_: HTML içindeki en küçük öğelerin bulunduğu, tanımlandığı kısımdır. Bu klasör içinde, link, başlık, form elemanları gibi en küçük ve basit yapılar bulunmaktadır.
  * _globals_: İçerisinde __normalize.css__ ile beraber, genel kullanım için hazırlanmış sağa/sola yaslama, self clear için `group` classı gibi tanımları barındırır.
  * _layout_: içerisinde, genişlik ve basit fluid grid tanımlarının yapıldığı mixinler bulunmaktadır.
  * _variables_: içerisinde hem _settings_ içerisinde ezilmesine izin verilen hem de Melange'ın kendi standart tanımlamalarını yaparken kullandığı değişkenler bulunmaktadır.

Kendi uygulamanız içerisine benzer klasör yapısını
```
.  
|-- styles.scss  
|-- settings  
|   |-- _animations.scss  
|   |-- _breakpoints.scss  
|   |-- _colors.scss  
|   |-- _fonts.scss  
|   |-- _namespace.scss  
|   |-- _settings.scss  
|   |-- _sizes.scss  
|   |-- _supports.scss  
|   '-- // uygulamanız için ekleyeceğini diğer ayar/değişken tanım dosyaları
'-- gui  
    |-- auxiliary  
    |-- components  
    |   |-- navigations // menu tanımlarınız
    |   |-- _components.scss
    |   '-- // uygulamanız için ekleyeceğiniz diğer komponent dosyaları
    |-- elements  
    |   |-- forms
    |   |   |-- _buttons.scss
    |   |   |-- _fields.scss
    |   |   |-- _forms.scss
    |   |   |-- _inputs.scss
    |   |   '-- _labels.scss
    |   |-- _elements.scss
    |   |-- _headings.scss
    |   |-- _links.scss
    |   |-- _lists.scss
    |   |-- _tables.scss
    |   |-- _texts.scss
    |   '-- // uygulamanız içine ekleyeceğiniz diğer element tanımları
    |-- externals
    |   |-- _externals.scss
    |   '-- // uygulamanıza ekleyeceğiniz external kütüphane ve pluginlerin orjinal stilleri
    |-- globals  
    |   |-- _globals.scss
    |   '-- // uygulamanız için ekleyeceğini diğer ortak tanımlar, genel olarak font-face ve font-icon tanımları
    |-- layout
    |   |-- _content.scss
    |   |-- _footer.scss
    |   |-- _header.scss
    |   |-- _layout.scss
    |   |-- _sidebar.scss
    |   `-- _page.scss
    |-- page
    |   |-- _page.scss
    |   '-- // uygulamanızda genel layout tanımları dışında özel olarak hazırlanma ihtiyacı olan sayfa tanımları
    |-- particules
    |   |-- _particules.scss
    |   '-- // uygulamanız için farklı farklı komponentler içinde kullanılabilecek tekrar kullanılabilen element gruplarının tanımları
    '-- tools 
        |-- tools.scss
        '-- // uygulamanız için kendi hazırladığınız mixin ve fonksiyonlar
```
Uygulama içindeki klasörlerde özetle beklenen kurgu aşağıdaki gibidir;
* __style.scss__: Herhangibir değişik yapma ihtiyacı hissetmeyeceğiniz [uygulama stil dosyası](https://github.com/bcinarli/melange-sample/blob/master/source/scss/styles.scss)
* __settings__: Uygulamanız için ihtiyacınız olan yeni değişkenler ve Melange metodları için kullanacağınız tasarımınıza uygun olan değişken tanımları.
* __gui__: Uygulamanızın stil tanımları
  * _auxiliary_: Melange'ın benzeri, kendi uygulamanız için son/final görünüm tanımları.
  * _components_: Uygulamanızın komponentleri. Burada uygulama menülerinizi için (header, footer vs.) `navigation`, kullanıcı ile alakalı komponent hazırlayacaksanız, `user` gibi alt klasörler ekleyebilirsiniz.
  * _elements_: Uygulamanızın link, başlık, tablo görünümü, liste gibi tanımları.
  * _externals_: Uygulamanızda sizin geliştirmediğiniz başka stil kütüphaneleri ya da JS komponentlerinin stil dosyalarının orjinal versiyonlarını buraya ekleyebilirsiniz.
  * _globals_: Bütün uygulamanızdaki seçiciler içinde ortak kullanabileceğiniz tanımlar ya da sass placeholderlarını buraya ekleyebilirsiniz. Genel olarak `font-face` ya da `font-icon` gibi jenerik tanımların yeri burasıdır.
  * _layout_: Tasarımınızdaki wrapper, header, footer, içerik alanı gibi kısımların boyutları, arkaplan rengi/resimleri gibi _içerilerindeki elemanların değil_, kendilerine ait tanımları.
  * _page_: Normalde durumlarda, _layout_ içerisinde zaten sayfalarınızın genel görünümü/layoutu ile alakalı bütün varyasyonları sağlayabiliyor olduğu varsayılmaktadır. Çok özel durumlar layout görünümleri dışında __kullanılması tavsiye edilmez__.
  * _particules_: Komponent kadar büyük olmayıp, birden fazla komponentin içinde tekrar tekrar kullanılabilecek küçük eleman gruplarıdır. Buralarda örneğin, _tag_, _fiyat gösterimi_ gibi yapılar düşünülebilir.
  * _tools_: Kullanabileceğiniz, _Caffeine_ yada benzeri başka bir mixin kütüphanesinde bulunmayan, uygulamanıza özel hazırlayabileceğiniz _mixin_ ve _fonksiyon_ tanımlarıdır.

## İsimlendirme
Melange içindeki isimlendirmeler, günlük kullanımda kolay anlaşılabilecek, iç güdüsel olarak benzer ögelerin isimlerini tahmin etmeye yarayacak ve tasarımdan bağımsız olarak genel-geçer kullanılabilecek şekilde düşünülmüştür. Buradaki kullanım mantığı için detaylı anlatımı [HTMLMagazin](http://htmlmag.com)'in, [CSS Tanımlarını İsimlendirme - Temel Kavramlar](http://hmgz.in/o) makalesinde bulabilirsiniz.

Buradan yola çıkarak, fluid grid içerisindeki tanımlar ilk bakışta anlaşılması zor olan `col-2-3` yerine `three-columns`, `five-columns` gibi zaten kolon genişliğinin/sayısının günlük konuşma dilinde söyleneceği gibi hazırlanmıştır. Benzer şeklide, genişlik sınıfları da, `one-whole`, `one-half`, `two-quarters` şeklinde belirlenmiştir.

## Tanımların Yapılması
Seçicilerinizi planlarken ve içerisine tanımları eklenirken mümkün olduğu kadar sadece ve sonradan overwriteların az olağı şeklide çalışılması tavsiye edilmektedir. Uygulamayı bir bütün olarak planlamalıdır. Özellikle responsive tasarımlarda tanımların küçük ekrandan büyüğe ya da büyük ekrandan küçüğe göre kurgusunda yapılacak düzenlemeler, kodunuzun daha yönetilebilir ve sade olmasına imkan verecektir. Bu konuyla alakalı detaylı anlatımı HTMLMagazin'in [Overwrite Edeceğiniz Kodu Baştan Yazmayın!](http://hmgz.in/9) makalesinde bulabilirsiniz.

## Melange Kullanım Detayları
### Ayarlar (settings)
Hem uygulamanız için kendi hazırladığınız kodlarda hem de Melange'ın ön tanımlı kodlarındaki değerleri değiştirebileceğiniz değişkenlere sahiptir. Ayarlar klasörünün içindeki dosyaları aynen kullanabileceğiniz gibi, ihtiyacınız olan yeni ayar grupları için istediğiniz şekilde yeni ayar dosyalarını ekleyebilirsiniz.

#### Animations
Uygulamanız içerisinde kullanabileceğiniz [_Caffeine_](https://github.com/bcinarli/caffeine) `app-transition` mixini için gerekli duration ve easing tanımlarını animations ayarları içerisine ekleyebilirsiniz. `$base-duration` için default değer `.4s`, `$base-easing` için default değer ise `ease`dir.

#### Breakpoints
Sayfanızın reponsive design kırılım noktaları için kullanabileceğiniz kırılım noktaları değerleridir. Geniş ekran, masa üstü, tablet ve telefon için tanımlanmışlardır. Genel olarak _media queryler_ içinde `min-width` ile beraber kullanılabilecek geniş ekran genişlik tanımı `$base-widescreen` için default değer `1824px` dir. Yine `min-width` ile kullanılması tavsiye edilen desktop genişlik tanımı `$base-desktop` için default değer `1224px`dir. Tabletler için `max-width` ile kullanılabilecek `$base-tablet-landscape` için default değer `1024px`, `min-width` ile kullanabileceğini `$base-tablet-portrait` için default değer `768px`dir. Telefonlar için de `max-width` ile kullanabileceğiniz `$base-phone` genişlik değeri `420px` dir. 

#### Renkler (colors)
Uygulama içinde kullanımının kolaylaşması ve renklerin uygulama boyunca standart kalması için renk tanımları eklenmiştir. Buradaki renkler `$color-primary`, `$color-secondary`, `$color-tertiary`, `$color-error`, `$color-text` gibi renklerin kullanım şekillerine göre isimlendirilmiştir. 

Yine renkler içinde, butonların, input elemanlarının, linklerin renk tanımları da yapılmıştır.

#### Fontlar
Uygulama standardında font ailesi `"Helvetica Neue", Helvetica, Arial, sans-serif`, font boyutu da `16px` olarak belirlenmiştir. `_fonts.scss` dosyası içinde tasarımınıza göre bu tanımları revize edebilirsiniz.

#### Namespace
Melange'ın en önemli özelliklerinden biri, bir kütüphane kullanmanıza rağmen sizi bazı isim ve kod kısıtlamalarına zorunlu tutmamasıdır. `_namespace.scss_` içerisinde grid kolon isimleri, row isimleri, genel class isimleri, buton isimleri, resim klasörü gibi tanımları değiştirebilirsiniz.

#### Genişlikler (sizes)
Grid gutter genişliği, grid max kolon sayısı, input genişlikleri ve border boyutları gibi tanımları `_sizes.scss` içerisinde değiştirebilirsiniz. Benzer şekilde buton ve input alanlarının border-radius tanımlarını da bu dosya içindeki değişkenler ile yapabilirsiniz.

#### Tarayıcı/Tanım Desteği (support)
Genellikler _Caffeine_ mixinlerinde kullanılan ve uygulamanın IE8'e destek verip vermeyeceği (IE8 fallback kodu) tanımı yapılabilir.

### Fluid Grid ve Genişlikler
Melange içerisinde 2 çeşit genişlik tanımlanmışlar. Birisi fluid grid, diğeri ise fluid genişliklerdir.

#### Fluid Grid
Grid kolonları `float` ile tanımlanmıştır. Uygulamanın maksimum kolon sayısı `_sizes.scss` içerisinden tanımlanabilir. Maksimum tanımlanabilecek kolon sayısı _24_ tür. _Namespace_ içerisinde bir değişiklik yapmadıysanız grid kolon isimleri `one-column`, `two-columns`, `three-columns`... şeklinde verdiğiniz kolon sayısına kadar isimlendirilmektedir. 
* Bir satırdaki kolonların toplam değeri, tanımladığınız max kolon sayısını geçmeyecek şekilde olmalıdır.
* Backend tarafından programatik şekilde kolon classı verilmesini kolaylaştırmak için, kolonların prefixleri (default da _column_) hem çoğul hem de tekil olarak kullanılmaktadır. Örn: hem `one-column` hem de `one-columns` classı üretilmektedir. 
* Nested grid kullanımında row-parentlarına `.namespacesiniz-kolon-adiniz-parent` (default durumda `.column-parent`) classını verebilirsiniz.

Grid kolonları arasında boşluklar `padding` ile verilmiştir ve `$base-gutter` tanımına göre grid kolonunun her iki köşesine uygulanmaktadır. Dolayısı ile tasarımınızda iki grid arasında boşluk 20px olarak tanımlanmış ise, `$base-gutter` tanımınızı `10px` olarak yapmanız gerekmektedir.

Gridin satırının başındaki, sonundaki ya da iki tarafındaki `$base-gutter` dan kaynaklı boşlukları kaldırmak için grid `row` elemanına `pull` (grid başındaki boşluğu alır), `push` (grid sonundaki boşluğu alır), `pull-push` (gridin iki tarafındaki boşluğu alır) classları kullanılabilir.

Bazı durumlarda gridiniz içindeki satırının tamamında kolon kullanmayabilirsiniz. Bu durumda satırdaki kolon sayısını tamamlayabilmek için _offset_ tanımlarını kullanabilirsiniz. _offset_ tanımları da grid mantığında isimlendirilmiştir. Standart durumda `offset-by-one`, `offset-by-two`, `offset-by-three` ... şeklinde verdiğiniz kolon sayısının bir eksiğine kadar isimlendirilmektedir.
* Offset kullanıldığı durumlarda da, kolon sayısı ile offset miktarının toplamın max kolon sayısına eşit olması beklenmektedir.
* Bir elemanı gridin tamamı kadar kaydırmak alt satıra atmak ile aynı olacağı için, kolonun max sayısı miktarında _offset_ tanımı bulunmamaktadır.

#### Fluid Genişlikler
Grid şeklinde kullanılmayacak, içinde bulunduğu elemanın genişliğine göre kendisini oranlayacak büyüklükler için `fragment` dediğimiz genişlikler eklenmiştir. Fragment genişlikleri için en fazla 12de 1e kadar bir parça tanımlanabilir. Konuşma dilinden esinlenerek, fragment isimleri `one-whole`, `one-half`, `two-thirds`, `three-quarters` gibi isimlendirilmiştir.
* Her fragmentin kendisi kadar uzunluğu zaten `one-whole` yani %100 olacağı için, bütün fragmentlerin son değeri yoktur. Örn: yarım tanımı `half` için sadece `one-half` tanımı vardır ama `two-half` tanımı yoktur. Çeyrek tanımları için `one-quarter`, `two-quarters` ve `three-quarters` tanımları varken, `four-quarter` zaten `one-whole` olacağı, bunun tanımı yapılmamıştır.
* Farklı fragmentler içindeki aynı genişlikler ayrı ayır tanımlanmak yerine, kodu sadeleştirmek açısında gruplanmıştır. Örn: aynı genişlikte olan `one-half`, `two-quarters`, `three-sixths`, `four-eights`, `six-twelfths` tanımları ayrı aynı `width: 50%` şeklinde tanımlanmak yerine bir arada gruplanarak tanımlanmıştır.
* Backend tarafından programatik şekilde fragment classı verilmesini kolaylaştırmak için, fragment parçalarında hem çoğul hem de tekil olarak kullanılmaktadır. Örn: 1/3 ve daha küçük oranlar için hem `one-third` hem de `one-thirds` classı üretilmektedir. 

### Global Sınıflar
Uygulamanın tamamında `box-sizing:border-box` olarak yapılmıştır. Bu sayede hem fluid griddeki hesaplamalar sadeleşmiş hem de herhangibir elemana yapılacak genişlik hesaplarındaki padding/border taşmalarının önüne geçilmiştir.

Float edilmiş satırların, containerdan taşmasını engellemek için `clearfix` tanımı `group` classı olarak eklenmiştir. İçerisindeki elemanların float tanımı aldığı container elemanlara `group` classı verilerek content-overflow problemi engellenebilir.

Elemanları resetlemek, ortalamak gibi helper classlar eklenmiştir.
* `%reset`; elemanların _margin, padding, border, background, list-style_ tanımlarını `0` ya da `none` olarak overwrite eder.
* `%center`, `%vertical`, `%horizontal`; elemanları belirlenen konumlara ortalamaya yarar. `Caffeine` kullanıldığı durumlarda, dilerseniz `Caffeine`'e ait `center()`, `center-vertical()`, ya da `center-horizontal()` mixinleri de kullanılabilir.

İçerik dilinin yazım yönünden bağımsız olarak (hem soldan sağa hem de sağdan sola) tanımlanmış metin ve eleman hizalama classları, global sınıflar içinde tanımlanmıştır.
* `.move-to-start`; elemanın satırın başına hizalar (ltr için sola, rtl için sağa)
* `.move-to-end`; elemanın satırın sonuna hizalar (ltr için sağa, rtl için sola)
* `.align-start`; metinleri okuma yönünün başına hizalar (ltr için sola, rtl için sağa)
* `.align-end`; metinleri okuma yönünün sonuna hizalar (ltr için sağa, rtl için sola)

### Elemanlar (_elements_)
Elemanlar, HTML içinde kullanılacak en küçük sınıflar veya doğrudan HTML etiketlere verilmiş tanımları barındırmaktadır.

#### Form Elemanları
Formlar içerisinde kullanılan fieldlar ve butonları genel olarak bir grup olarak algılandığı için _form-elements_ içinde tanımlanmıştır.
* __buttons__:  `.button` classı buton olarak kullanılacak link, button ve input elemanlarını biçimlendirmek için kullanılmaktadır.
-Butonlarda hover ve basma etkileşimi için transition eklenmiştir.  
-Tıklama sırasında metin seçilmiş gibi gözükmesini engelmek için `disable-text-selection` metodu eklenmiştir.  
-Basma efekti için `inset` box-shadow tanımı bulunmaktadır.  
-Butonun standart rengi, metin ile kenar boşlukları, border-radius gibi tanımların hepsi _settings_ içinden değiştirilebilir.
    * _primary-action_: Butonun call-to-action amaçlı (form submit, register vs gibi) kullanılacağı durumda, aksiyon önceliğine göre birincil öncelik olarak tanımlanmıştır. Default class ismi `.primary-action` dır. Ayrıca `.button` classı tanımlanması gerekmez. 
    * _secondary-action_: Butonun ikincil öncelikli call-to-action amaçlı (browse, check) kullanılacağı durumlar için tanımlanmıştır. Default class ismi `.secondary-action`dır. Ayrıca `.button` classı tanımlanması gerekmez.
    * _tertiary-action_: Butonun üçüncül öncelikli call-to-action amaçlı kullanılacağı durumlar için tanımlanmıştır. Default class ismi `.tertiary-action`dır. Ayrıca `.button` classı tanımlanması gerekmez.
    * _cancel-action_: Butonun işlemi iptal edecek call-to-action amaçlı (cancel, back) kullanılacağı durumlar için tanımlanmıştır. Default class ismi `.cancel-action`dır. Ayrıca `.button` classı tanımlanması gerekmez.
* __fields__: `fieldset` ve `legend` tanımları yapılmıştır.
-Legend tanımı daha kolay stillendirilmesi için `block` şeklinde getirilmiştir.
    * _form-elements_: Genel olarak form içindeki inputların konulacağı sırasız liste (`ul`) için kurgulanmıştır. `%reset` tanımı uygulanmış ve formun her satırı için kullanılacak `li` elemanlarına `1em` yüksekliğinde bottom margin eklenmiştir. 
* __inputs__: Kolay tanımlama ve kullanım için `$_text-fields`, `$_checkable_fields`, `$_media-fields`, `$_button-fields` şeklinde input typelarına göre gruplanmışlardır.  
-Default olarak text-fieldlar için `.text-field` classı eklenmiştir. Bu sayede, input gibi gözükecek bazı alanlara bu classı uygulama imkanı sağlanmıştır.  
-Text-fieldların `focus`, `active`, `readonly`, `disabled` görünümleri _settings_ içinden değiştirilebilir.  
-Text-fieldlarına border-radius, padding, background ve border tanımları yine _settings_ içinden değiştirilebilir.  
-Checkable-fieldların (checkbox, radio) metinler ile daha rahat hizalanması için `vertical-align: middle` tanımı eklenmiştir.
* __labels__: Erişilebilirlik ve kullanılabilirlik prensipleri açısından, her input'un bir `label` içinde olması tavsiye edilmektedir. Bu labeller için de `item` classı tanımlanmıştır.   
-Her label içerisinde bir tane `item-label` classına sahip `span` bir de inputun kendisinin olması beklenmektedir.
-Label içerisinde label metni ile inputu alt alta göstermek için `label` elemanına `item-stacked`, yan yana göstermek için de `label` elemanına `item-field` classı eklenebilir.  
-Label'ın hata mesajı gösterimi için `item-error` classı `label` elemanına eklenebilir.  
-Labelların altında fieldlar ile alakalı yardım metni gösterimleri için `field-help` classı kullanılabilir.

#### Listeler
#### Linkler
#### Tablo

### Komponentler
#### Media Komponent
