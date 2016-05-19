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
