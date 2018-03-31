**MVC Nedir?**
================================

**MVC;** Model-View-Controller yapılarından oluşan bir Design Pattern’ dır.

Günümüzde MVC denince Microsoft’ un ASP.NET MVC Framework’ u akla gelmektedir. Fakat MVC Microsoft ile değil 1979 yılında 
**Trygve Reenskaug** tarafındna geliştirilmiştir. Daha sonra Microsoft bu mimari yapıyı geliştirmiş ve kendi bünyesine de dahil etmiştir.   

**Model:** Veritabanı ya da direkt olarak verinin tutulduğu ve verilerin işlenme mantığının tutulduğu yerdir.

**View:** Uygulamanın kullanıcılar tarafından görülen arayüz kısmıdır.

**Controller:** Kulanıcıların View üzerinden gerçekleştirdiği işlemleri Model e götürür ve Model den aldığı veriyi View e taşır. Yani Model ve View arasında getir götür işlemlerini gerçekleştirir genelde.

![e0](https://user-images.githubusercontent.com/21074849/38163730-727e1ca0-3501-11e8-8745-6ef5620363d3.jpg)

**NOT:** Model ve View arasında direkt iletişim bulunmaz. Controller ile sağlanır iletişim !!!

Yukarıdaki şema ile 4 durumdan bahsedilebilir;

**1. Request -> Controller -> Model -> View -> Responsive (User)**

Kullanıcı istek gönderir. İstek Controller tarafından alınır ve Model’ e iletilerek gerekli veri alınır. İşlenmiş veri View e gelir ve kullanıcıya yansır.

**2. Request -> Controller -> View -> Responsive (User)** 

Kullanıcı istek gönderir ve Controller tarafından istek alınır. İstek Controller da değerelendirilerek View e gelir ve kullanıcıya yansır. Bu durum static sayfalar için kullanılır. Mesele Hakkımızda sayfası için Model den veri çekmeye gerek yoksa sadece hazır .html sayfası görüntülenecekse bu iş akışı gerçekleşir.

**3. Request -> Controller -> Responsive (User)** 

Kullanıcı istek alır, Controller da değerlendirilir ve kullanıcıya sonuç döner. Controller da JSON, string gibi değer döndüren methodlar örnek verilebilir.

**4. Request -> Controller -> Model -> Responsive (User)**

Kullanıcı istek alır. Controller a gelen istek yorumlandıktan sonra Model e gelir ve kullanıcıya sonuç yansır. JSON örnek olarak verilebilir
