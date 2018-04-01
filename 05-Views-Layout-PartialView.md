**Layout, View, ViewStart, Section, PartialView ?**
================================

**Layout Nedir ve Nasıl Kullanılır ?**
--------------------------------

**Layout;** ASP.NET MVC de arayüzü yönetmemizi kolaylaştıran bir özelliktir. Asp.net WebForms’ daki ***MasterPage*** sayfasının MVC’ deki 
karşılığı Layout sayfalarıdır. Fakat Layout lar MasterPage lere göre daha esnek ve yazımı daha kolaydır.

Layout sayfalar, web uygulamalarındaki sayfaların iskeletini oluşturur. Tüm sayfalarımızda yer alacak olan örneğin üst menü, alt menü ya da
solda menü gibi sürekli tekrar eden kısımların tek bir sayfadan yönetilmesini sağlar.

ASP.NET MVC Layout sayfaları, genelde HEAD tagları arasına ya da sayfaya yerleştirdiğimiz JS ve CSS dosyalarımızı da barındırır. Bu sayede 
web uygulamasının kullandığı kaynaklarını yönetmek oldukça basitleşmiş olur.

Bir örnek ile açıklamak gerekirse;

![e32](https://user-images.githubusercontent.com/21074849/38177667-c0ad5dc0-360d-11e8-83f4-8d2e30a50fd5.jpg)

Resimdeki iskelete sahip bir websitesi olsun. Burada bulunan ***Header, Sidebar-left, Sidebar-right*** ve ***Footer*** kısımları websitesine 
ait her sayfada sabit olarak gelsin, sadece ***Content*** yazan kısımda değişiklik olsun. Layout sayesinde websitesinde bulunan bütün 
sayfalarda aynı kalmasını istediğimiz yerlerin her defasında her sayfada yazılmasını engelliyor ve sadece bir kez yazılarak diğer sayfalarında 
bu Layout tan sayfa iskeletini almasını sağlıyoruz.

Peki diğer sayfalar sadece Content kısmının değişeceğini nereden anlıyor? Burada devreye Layout sayfasında yazılacak olan
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@RenderBody() 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
kodu giriyor. ***@RenderBody();*** sadece benim bulunduğum kısımda içerik değişikliği meydana gelecek diyor bize.

***Layout ‘u 2 şekilde oluşturabiliriz;***

1-	 Controller oluşturup içinde bulunan Index e sağ tıklayıp Add View dediğimizde otomatik olarak ***Views*** klasörü içinde ***Shared*** 
isminde bir klasör oluşur ve bu klasörün içinde de hazır bir şekilde ***_Layout.cshtml*** dosyası gelir.  
>Shared olarak gelen klasör ismi tercihe göre değiştirilebilir.

2-	Views klasörü içinde ***Shared*** adında bir klasör oluşturup sağ tıklayıp ***Add -> MVC 5 Layout Page(Razor)*** i seçerek Layout 
dosyası oluşturabiliriz.

>   ***NOT:*** Gerçekleştireceğiniz projelerin daha düzenli ve yönetilebilir olması bakımından Layout dosyaları için Views klasöründe 
Shared gibi bir klasör içinde Layout dosyalarını oluşturmak kolaylık sağlar.

Daha net anlayabilmek için uygulamaya geçelim. İkinci seçeneği kullanrak Layout oluşturalım. İlk olarak MVC projesi açarak HomeController 
isminde Controller ekleyelim, Views  klasörüne sağ tıklayarak Shared klasörü oluşturalım ve son olarak Shared klasörüne sağ tıklayarak 
***Add -> MVC 5 Layout Page(Razor)*** diyelim.

![e33](https://user-images.githubusercontent.com/21074849/38177668-c0e2104c-360d-11e8-9e08-7872f6e42448.png)

İlk resimde ***Content*** olarak bahsettiğimiz yer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<div>
  @RenderBody()
</div>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
kısmıdır ve diğer sayfalarda bu kısımda içerik farklılıkları olacaktır.

Ortak bir örnekten gitmek adına Layout sayfamızda alağıdaki değişiklikleri gerçekleştirelim.

![e34](https://user-images.githubusercontent.com/21074849/38177669-c1124546-360d-11e8-8f84-bb7d3a7060a2.png)

Buraya kadar Layout ouşturmayı öğrendik. Şimdi Layout u View de kullanma işlemine gelelim.

**Layout Kullanan View Oluşturma**
--------------------------------

Layout sayfalar direk çalıştırılamazlar. Layout ları kullanan View ler çalıştırılabilir. Şimdi Layout u görüntülemek için daha önce 
oluşturduğumuz HomeController içindeki Index metoduna sağ tıklayarak Add View diyelim.

![e35](https://user-images.githubusercontent.com/21074849/38177670-c13ca732-360d-11e8-8b31-c56d1fca623b.png)

Karşımıza gelen pencerede ***'Use a layout page'*** işaretli. Bir Layout kullan diyor fakat bu kısım boş. Layout ismi yazmıyor. 
Solda üç noktaya tıklayarak eklemiş olduğumuz Layout u seçerek OK diyelim.

![e36](https://user-images.githubusercontent.com/21074849/38177671-c17d2d5c-360d-11e8-82f5-cd298cdf8a14.png)

Daha sonra gelen pencereyi de onayladıktan sonra HomeController da bulunna Index methodumuza oluşturduğumuz Layout iskeletini vermiş 
olduk.

>   ***NOT:*** Biz Layout u elimizle kendimiz oluşturduk. Aslında Layout oluşturmadan HomeController da Index e sağ tıklayıp Add View 
deseydik ve gelen pencerede hiçbir şeye tıklamadan Add tıklasaydık Views klasörümüzde hali hazırda Shared klasörü ve Shared klasörü 
içinde ise ***_Layout.cshtml*** dosyası oluşmuş olacaktı.

![e37](https://user-images.githubusercontent.com/21074849/38177672-c216c4bc-360d-11e8-82ba-330700945745.png)

Oluşan Index.cshtml sayfasında Layout kısmında Index sayfasının kullanmış olduğu Layout bize gösterilmektedir. Index.cshtml e sağ tıklayıp 
View in Browser diyelim.

![e38](https://user-images.githubusercontent.com/21074849/38177673-c2e417dc-360d-11e8-87d6-b36a35a9beb6.png)

Index web sayfasında sadece Index yazısı bulunmaktaydı. Oluşan kırmızı çerçeve ise Layout sayfasından gelmektedir.

Şimdi Layout ve HomeController da aşağıdaki değişiklikleri yaparak uygulamamızı geliştirelim.

![e39](https://user-images.githubusercontent.com/21074849/38177680-d044cdb8-360d-11e8-934b-38ec39b0e0f4.png)

![e40](https://user-images.githubusercontent.com/21074849/38177681-d077cf74-360d-11e8-83af-472c3057d83e.png)

HomeController da About ve Contact metodlarını ekledikten sonra ikisine de ayrı ayrı sağ tıklayıp Add View diyerek ve oluşturduğumuz 
Layout sayfasını seçerek View ekleyelim.

Daha sonra Index sayfasına sağ tıklayarak tarayıcıda çalıştıralım.

![e41](https://user-images.githubusercontent.com/21074849/38177682-d0a16294-360d-11e8-964e-80b0f9b018cc.png)

Görüldüğü gibi az önce ***_Layout.cshtml*** sayfamızda eklemeler yaptık ve burada yaptığımız değişiklikleri Anasayfa, Hakkımızda ve 
İletişim e tıklayınca aynı şekilde görebildik.

**ViewStart Ne İşe Yarar ?**
--------------------------------
Varsayılan  Layout tanımı yaparak websitesinde bulunan tüm sayfalara ayrı ayrı Layout tanımı yapmamızı engeller. 

***Örneğin;*** websitemizde 20 sayfa var. 20 sayfaya ayrı ayrı Layout tanımı yapmak yerine sadece ViewStart.cshtml sayfasında Layout 
tanımı yaparak bu 20 sayfanın Layout u buradan almasını sağlayabiliriz.

***_ViewStart.cshtml*** sayfası Views klasörünün içinde bulunur. Views klasörüne sağ tıklayıp Add -> MVC 5 ViewPage(Razor) i seçip 
dosyaya _ViewStart.cshtml ismini verelim.

![e42png](https://user-images.githubusercontent.com/21074849/38177683-d0cfa352-360d-11e8-9deb-670a5c5823bd.png)

Karşımıza gelen sayfada html kodlarını silerek yukarıdaki gibi sanal path ile razor bloğuna Layout yolumuzu tanımlayalım. Daha sonra önceden
oluşturduğumuz Index.cshtml, About.cshtml ve Contact.cshtml sayfalarımızdan Layout un tanımlı olduğu kod satırını silebiliriz.

![e43](https://user-images.githubusercontent.com/21074849/38177684-d17ae000-360d-11e8-9985-9f781bc0b624.png)

Yukarıdaki kod satırını silip tarayıcıda sayfayı çalıştırdığımızda hiçbir değişiklik olmamış gibi o sayfalarda ***_Layout.cshtml***
sayfasına ait elemanlar gelecektir.

>   ***NOT1:*** ViewStart ın bir diğer avantajı ise şöyledir; ***_Layout2.cshtml*** sayfamız olduğunu düşünelim ve tüm sayfalarda artık 
bu iskeleti kullanmak istiyoruz. Bunu için sadece; ***_ViewStart.cshtml*** sayfasına gelip ***_Layout2.cshtml*** in yolunu belirteceğiz.
Eğer ***_ViewStart*** dosyamız olmasa websitesinin sahip olduğu 20 sayfaya girip ayrı ayrı ***_Layout2.cshtml*** yazacaktık. Sadece 
***_ViewStart.cshtml*** de belirttiğimiz Layout tanımıyla bu sayfalara ayrı ayrı girmeyi önlemiş olduk.

>   ***NOT2:*** Daha önce HomeController da herhangi bir metoda tıklayıp Add View deyip karşımıza gelen pencerede hiçbir şeye tıklamadan
sadece Add dersek otomatik olaraz hazır bir şekilde ***_Layout.cshtml*** sayfası oluşacak demiştik. Bu işlem sırasında aynı zamanda 
***_ViewStart.cshtml*** sayfası da Layout yolu belirtilmiş bir şekilde oluşur. Biz öğrenmek amacıyla yukarıdaki örnekte el ile oluşturduk.

Şimdi baştan yeni bir proje açarak NOT olarak anlattıklarımızı uygulamalı olarak görelim. Proje açıp Controller ekleyelim ve daha sonra
Controllerde bulunan Index e sağ tıklayıp Add View diyelim.

![e44](https://user-images.githubusercontent.com/21074849/38177686-d1a760b2-360d-11e8-9a7c-1e6944c93353.png)

Burada altı çizili olarak belirtilen yer bize ***‘Eğer _viewstart dosyası ayarlayacaksan burayı boş bırak’*** diyor. 
Hiçbir yere tıklamadan Add diyelim.

![e45](https://user-images.githubusercontent.com/21074849/38177687-d1d070ec-360d-11e8-98bb-46ed06f5c201.png)

Solution Explorer ı incelersek;

***Content, fonts ve Scripts*** klasörleri oluştu. Bunlar MVC tarafından hazır olarak oluşturulan ve websitesinde kullanacağımız 
Bootstrap in CSS, Font ve JavaScript dosyalarını bulundururlar. Tercihe göre kullanmayıp kendi CSS, Font ve JavaScript dosyalarınızı da 
ekleyebilirsiniz. Ama biz genelde sayfa taasarımlarında Bootstrap üzerinden gideğiz. 

Views kalsörü içinde ise ***_ViewStart.cshtml*** dosyası ve Shared klasörü hazır olarak geldi. Shared klasörü içinde ise ***_Layout.cshtml*** 
dosyası hazır bir şekilde geldi. ***_Layout.cshtml*** dosyasına göz atarsanız Bootstrap  e sahip hazır basit bir tasarım gelmiştir.

Index.cshtml sayfasını tarayıcı da çalıştırırsak aşağıdaki gibi bir görüntü elde edeceğiz.

![e47](https://user-images.githubusercontent.com/21074849/38177688-d1fc27c8-360d-11e8-9276-51d423ea063b.png)

Aynı zamanda Index.cshtml dosyasını incelersek; Layout tanımını olmadığını göreceğiz. Çünkü ***_ViewStart.cshtml*** dosyasında hazır 
olarak oluşturuldu.

Bu şekilde hazır olarak CSS, fonts, Scripts, Layout  ve ViewStart ın hazır olarak getirilmesini öğrendik.

**Nested Layout – (İç içe Layout Oluşturma)**
--------------------------------

İç içe Layout u bir örnek ile açıklamaya çalışalım. Mesela sahip olduğumuz temel Layout’ ta header ve footer kısımları sabit olsun. 
Bu kısımlara ilaveten sağ tarafta bir kısım daha ayıralım  ve bu yer gelecek sayfalara göre içerik olarak değişsin. Contact sayfasında 
adres bilgileri olarak gelsin, Indek sayfasında gelmesin istiyoruz. Bu tarz bir durum için İç içe Layout kullanırız. 

![e48](https://user-images.githubusercontent.com/21074849/38177689-d22a873a-360d-11e8-9e05-a3ee4ed84957.png)

Yukarıda anlattığımız örneğe göre Mavi çerçevenin tamamı ***@RenderBody()*** dir, içerisindeki kırmızı taralı alan ise Contact sayfasında 
gelecek, Index sayfasında ise gelmeyecektir.

Şimdi en son örnek olarak açtığımız proje üzerinden uygulamaya geçelim.  Shared klasörüne sağ tıklayıp ***Add -> MVC 5 View Page with Layout(Razor)***
seçerek ***_RightLayout*** ismini girelim ve ekrana gelen pencereden ***_Layout.cshtml*** i seçelim.

Oluşan ***_RightLayout.cshtml*** sayfasında yazılacak olan html kodları ***_Layout.cshtml*** sayfasının @RenderBody() kısmında gözükür. 
Çünkü ***_RightLayout.cshtml*** i oluştururken ***_Layout.cshtml*** in iskelet yapısını al dedik.

Şimdi alttaki kodları ekleyelim.

![e49](https://user-images.githubusercontent.com/21074849/38177690-d25679c6-360d-11e8-9cbc-b72c64270699.png)

Css kodlarını ***_Layout.cshtml*** e keleyelim. ***_RightLayout.cshtml*** a da ekleyebilirsiniz ama zaten hepsi Tarayıcı da bir bütün olarak çalışacak. 
Düzen açısından ***_Layout.cshtml*** e eklemek daha iyi.

![e50](https://user-images.githubusercontent.com/21074849/38177691-d2874a60-360d-11e8-917a-630bfd483108.png)

***@RenderBody()***; Mavi çerçeve içindeki gri alanı göstermektedir.

![e51](https://user-images.githubusercontent.com/21074849/38177692-d2b57a48-360d-11e8-8cdd-7f605e9f2ea0.png)

***Contact*** metoduna sağ tıklayıp Add View diyelim. Karşımıza gelen pencere de Layout alanını ***_RightLayout.cshtml*** olarak seçelim.  
Daha sonra oluşan ***Contact.cshtml*** sayfalarını tarayıcı da çalıştıralım. Aşağıdakine benzer bir görüntü alacaksınız.

![e52](https://user-images.githubusercontent.com/21074849/38177693-d34e0dc6-360d-11e8-9fc3-23534e78f17f.png)

Şimdi de ***Index.cshtml*** i tarayıcıda çalıştırıp farkı görelim.

![e47](https://user-images.githubusercontent.com/21074849/38177688-d1fc27c8-360d-11e8-9276-51d423ea063b.png)

***Özet olarak;*** Contact sayfalarının kullandığı ***@RenderBody()*** kodu ***_RightLayout.cshtml*** den geldi. 
***_RightLayout.cshtml*** ise ***_Layout.cshtml*** sayfasındaki ***@RenderBody()*** i kullandı. Böylece iç içe Layout kullanmış olduk. 
Index sayfası ise sadece _Layout.cshtml sayfasını kullandı.

**Section Bölüm Oluşturma**
--------------------------------

Section ı da uygulama üzerinden anlatmaya anlatmaya çalışalım. Bir Layout sayfamızda Index, About ve Contact seçeneklerinden oluşan 
menü olsun ve Index sayfasında bu 3 seçenek gözüksün, About sayfasında sadece Index seçeneği gözüksün.  Bu isteğimizi Layout oluşturarak
yapabiliriz ama projede buna benzer isteklerimiz artarsa ortalık Layout kaynar. Bunun yerine Section kullanarak daha düzenli bir yapı 
oluşturabiliriz.

***_Layout2.cshtml*** isminde yeni bir Layout Page açalım ve içeriğini aşağıdaki gibi yapalım.

***_ViewStart.cshtml*** yolunu ***_Layout2.cshtml*** olarak değiştirmeyi unutmayalım.

![e53](https://user-images.githubusercontent.com/21074849/38177694-d37d82f4-360d-11e8-8196-3bfecd723ab0.png)

![e54](https://user-images.githubusercontent.com/21074849/38177695-d3a70f2a-360d-11e8-9960-f7123061c28e.png)

Yukarıdaki resimde bulunan ul li bloğunda Index in sabit kalmasını About ve Contact ın ise Index sayfasında olmasını About sayfasında 
gelmemesini istiyoruz. Bu isteğimiz için ***_Layout2.cshtml*** sayfasına section eklemeliyiz.

![e55](https://user-images.githubusercontent.com/21074849/38177696-d3d67e5e-360d-11e8-80fb-05c3bb8a12aa.png)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@RenderSection("header", false); 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

burada false yazarsak her sayfada girilmesi zorunlu değil anlamına gelir.

Eklediğimiz @RenderSection("header", false) ı Index sayfasında görmek için Index.cshtml sayfasına herhangi bir yere aşağıdaki kodları 
ekleyelim ve tarayıcıda çalıştıralım. Aşağıdaki görüntüyü alırız.

![e56](https://user-images.githubusercontent.com/21074849/38177697-d403e826-360d-11e8-8734-1bdc30a132ca.png)

![e57](https://user-images.githubusercontent.com/21074849/38177698-d4382802-360d-11e8-9191-7f766eed732a.png)

Index sayfamızda menüm tam geldi. About sayfasında sadece Anasayfa yazan seçenek gelecek. HomeController da About metoduna sağ 
tıklayıp Add View diyelim. Daha sonra tarayıcıda çalıştıralım. Aşağıdaki görüntüyü alırız.

![e58](https://user-images.githubusercontent.com/21074849/38177699-d469716e-360d-11e8-9d48-2b38f718ee0f.png)

**Partial View**
--------------------------------
***ASP.NET Web Form*** da ***User Control*** e karşılık gelmektedir. Tekrar etmemiz gereken nesneleri, html sayfalarını bir modül 
haline getirerek kullanmamızı sağlar. Views klasörü içinde oluştururuz. Düzen açısından genelde Shared klasörü içinde oluşturulur.

Örneğin bir blog websitesinde sağ tarafta faydalı linkler diye bir alan bulunmakta. Bu kısmı aynı sayfa da footerda da kullanmak 
istiyoruz. 2 kez faydalı linkler için kod yazmak yerine bunu bir modul olarak olutururuz ve kullanmak istediğimiz alanlarda çağırırız.

En son çalıştırdığımız projede _ViewStart.cshtml i ***_Layout.cshtml*** olarak değiştirelim. Shared  klasörüne sağ tıklayıp 
***Add -> MVC 5 Parial View(Razor)*** ekleyelim. Aşağıdaki kodları oluşturduğumuz partial view a ekleyelim.

![e59](https://user-images.githubusercontent.com/21074849/38177700-d49bf724-360d-11e8-949f-16cc1cd0c438.png)

Index.cshtml de oluşturulan partial view ı çağıralım. Partial View 2 farklı şekilde çağrılır.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1.	@Html.Partial("Partial adi")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
2.	@{
        Html.RenderPartial("_PartialFaydaliLink");
     }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
Index.cshtml sayfasında 2 şekilde de partial ı çağıralım.

![e60](https://user-images.githubusercontent.com/21074849/38177701-d4c6b27a-360d-11e8-9ef0-6931c159ae03.png)

Aynı zamanda About ve Contact sayfalarında da partial ı çağırabilirdik. Tarayıcıda  Index.cshtml sayfasını çalıştırdığımızda aşağıdaki 
gibi bir görüntü alırız. 

![e61](https://user-images.githubusercontent.com/21074849/38177702-d4f7e8ae-360d-11e8-9bc2-00ed35c8209c.png)

>   ***NOT:***  Yaptığımız örnekte partial ı Shared klasöründe oluşturduğumuz için direkt ismi ile çağırdık.  Mesela  Views klasörü 
içinde Home ve Home2 klasörleri mevcut. Partial  Home klasörünün içindeyse ve Home2 de bulunan sayfalardan birinde çağırmak istiyorsak 
direkt ismiyle çağıramayız. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Partial("../Home/_PartialFaydaliLink")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
şeklinde yol belirtmemiz lazım. 





















