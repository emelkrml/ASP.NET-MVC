**Html Helpers**
================================

***Html Helper***; View içerisinde ki verileri göstermede kullandığımız ve Html olarak çıktı üreten hazır metodlardır.

Microsoft'un Framework içerisinde sunduğu Helper'lerin yanında, Web Helper'leri, ayrıca Paypal gibi firmalar tarafından üretilen, çeşitli Helper'ler da mevcuttur. Ayrıca kendiniz de, isteğinize özel Helper'lar geliştirebilirsiniz.
Html Helper'leri kullanırken,
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ile yazmaya başlarız. Noktadan sonra, kullanılabilecek çeşitli metodlar, IntelliSense tarafından listelenecektir.



**Html.Action**
--------------------------------

***Yazım Şekli :*** 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Action("Action ismi","Controller ismi")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** Sayfa yüklendiğinde, Controller ismi kısmında yazılı olan Controller'in içerisinde ki, Action ismi kısmında belirtilen Action'u çağırır ve dönen sonucu ekrana yansıtır.

***Örnek:***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Action("Index", "Home") 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HomeController içindeki Index Action ını döndürür.


**Html.ActionLink**
--------------------------------
***Yazım Şekli:*** 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ActionLink("Link yazısı","Action ismi","Controller ismi")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama:*** Link olarak kullanılır. Link yazısı kısmına, görünecek metin, Controller ismi kısmına gidilecek Controller'in adı, Action ismi kısmına da çağırılacak olan Action metodun ismi yazılır.

***Örnek:***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ActionLink("Anasayfa ya git", "Home", "Index")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

![e11](https://user-images.githubusercontent.com/21074849/38163501-cd2dcb86-34fd-11e8-98c8-ced54ebd136d.png)

[Anasayfa ya git](https://github.com/emelkrml/ASP.NET-MVC) yazısına tıklayınca HomeController içindeki Index Action ını döndürür.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ActionLink("Anasayfa ya git", "Home", "Index")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
kod satırı aynı zamanda 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<a href="Home/Index">Ana Sayfa</a>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
html kod satırı ile aynı işleve sahiptir.


***Html.BeginForm***
--------------------------------

***Yazım Şekli :*** @Html.BeginForm("Action ismi","Controller ismi")

***Açıklama :*** Formlarda kullanılır(Üyelik girişi, iletişim formu gibi).
 
***Örnek:***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@using (Html.BeginForm("Index", "Home"))
{
    @Html.Label("Adınız:  ")
    @Html.TextBox("ad");
    <br />
    <input type="submit" value="Gönder" />
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

***Çıktı:***

![e12](https://user-images.githubusercontent.com/21074849/38163502-cd5977ea-34fd-11e8-96ea-79f9f95af6e2.png)

Yukarıdaki kod satırı aşağıdaki kod satırı ile aynı işlevi görür.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<form action="/Home/Index" method="post">
    <label for="Ad_n_z:__">Adınız:  </label><input id="ad" name="ad" type="text" value="" />   
    <br />
    <input type="submit" value="Gönder" />
</form>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


**Html.CheckBox**
--------------------------------

***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.CheckBox("İsim","İşaretli mi")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** Onay işlemlerinde, bir şeyin seçili olup olmamasını belirlemek için kullanılır. İsim kısmına, CheckBox'ın adı, İşaretli mi kısmına da true ya da false yazılır.

***Örnek:***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.CheckBox("Adresime E-posta gelsin", true)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yukarıdaki kod aşağıdaki kod ile aynı işleve sahiptir.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<input checked="checked" id="Adresime_E-posta_gelsin" name="Adresime E-posta gelsin" type="checkbox" value="true" />
<input name="Adresime E-posta gelsin" type="hidden" value="false" />
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.DropDownList**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.DropDownList("İsim","Liste")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** Alta açılır oluşturur. İsim kısmına, herhangi bir isim, Liste kısmına da, listenin içinde gösterilecek bir veri listesi yüklenir.

***Örnek :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.DropDownList("sehirler", new[] { new SelectListItem { Text = "İstanbul", Value = "34" }, 
new SelectListItem { Text = "Ankara", Value = "06" } })
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

![e13](https://user-images.githubusercontent.com/21074849/38163503-cda4e0b8-34fd-11e8-99c8-41642f9d5fb0.png)

Yukarıdaki kod aşağıdaki kod ile aynı işleve sahip.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<select id="sehirler" name="sehirler">
    <option value="34">İstanbul</option>
    <option value="10">Ankara</option>
</select>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.EndForm**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.EndForm()
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** @using ifadesi içerisinde sarmalanmadan, @Html.BeginForm ifadesi ile başlangıcı açılan, form elementini kapatır. @using ifadesi kullanıldıysa, zaten bu elemana ihtiyaç yoktur. Süslü parantez bittiği zaman, otomatik olarak kapanacaktır.


**Html.Hidden**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Hidden("İsim","Değer")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :***  Verilerin, gizli olarak saklanabileceği elemanlar oluşturmak için kullanılır. İsim kısmına, herhangi bir isim, Veri kısmına da saklanacak veri girilir. Yalnız şu unutulmamalıdır, veriler tarayıcıların geliştirici araçları ile görüntülenebilir. Bu yüzden tam bir gizlilikten söz edilemez.

***Örnek :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Hidden("hiddenId", "1")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Yukarıdaki kod aşağıdaki kod ile aynı işleve sahiptir.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<input id="hiddenId" name="hiddenId" type="hidden" value="1">
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.Label**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-
@Html.Label("Tanımlayıcı eleman", "Metin")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

***Açıklama :*** Bir eleman ile ilgili tanımlayıcı metin eklemeye yarayan elemandır. Tanımlayıcı eleman kısmına, açıklama için kullanılacak elemanın (TextBox,TextArea,RadioButton vs.) id'si, Metin kısmına da, metinsel açıklama yazılır. 

***Örnek :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Label("textBoxIsim", "İsim giriniz : ")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.ListBox**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ListBox("İsim","Liste")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** Listeler oluşturmak için kullanılır. İsim kısmına, herhangi bir isim, Liste kısmına da listenin içinde gösterilecek bir veri listesi yüklenir.

***Örnek :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ListBox("sehirler", new[] { new SelectListItem { Text = "İstanbul", Value = "34" }, 
new SelectListItem { Text = "Ankara", Value = "06" } })
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Yukarıdaki kod aşağıdaki kod ile aynı işleve sahiptir.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<select id="sehirler" multiple="multiple" name="sehirler">
    <option value="34">İstanbul</option>
    <option value="06">Ankara</option>
</select>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.Password**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Password("İsim", "Şifre")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** İçerisine girilen elemanları, şifreleyerek göstermeye yarayan bir elemandır. Şifre girişlerinde bu eleman kullanılır. İsim kısmına elemanın ismi, Şifre kısmına da şifreli eleman yazılır. Şifre kısmı kullanıcı tarafından girileceği için, çoğu zaman boş olarak gönderilir.

***Örnek:***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Password("paswSifre", "123465")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.RadioButton**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.RadioButton("İsim","Değer","İşaretli mi")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** İçerisine girilen elemanı, seçenek olarak işaretleyebilmemize yarayan elemandır. İsim kısmına elemanın ismi, Değer kısmına elemana atanacak değer, İşaretli mi kısmına da,varsayılan olarak, elemanın işaretli olup olmamasına göre true ya da false atanır.

***Örnek:***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.RadioButton("rdbCinsiyet", "Bay", true)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yukarıdaki kod aşağıdaki kod ile aynı işleve sahiptir.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<input checked="checked" id="rdbCinsiyet" name="rdbCinsiyet" type="radio" value="Bay">
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.TextArea**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.TextArea("İsim","Değer",new{cols="Sütun sayısı",rows="Satır sayısı"})
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** Birden fazla sütundan oluşan metin kutuları oluşturmak için kullanılır. Genellikle adres, mesaj vb. bilgi girişleri için kullanılabilir. İsim kısmına elemanın ismi, Değer kısmına veri yazılır. Değer kısmı, çoğunlukla kullanıcı tarafından girileceği için, genellikle içi boş olarak gönderilir. Tercihe bağlı olarak cols ve rows kullanılabilir. cols, sütun sayısını, rows da, satır sayısını ifade eder.

***Örnek :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.TextArea("txtAreaAdres", "", new { cols = 70, rows = 10 })
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Yukarıdaki kod aşağıdaki kod ile aynı işleve sahiptir.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<textarea cols="70" id="txtAreaAdres" name="txtAreaAdres" rows="10"> </textarea>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.TextBox**
--------------------------------
Yazım Şekli : 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.TextBox("İsim","Değer")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** İçerisine girilen elemanları metin kutusu içerisinde gösteren bir elemandır. İsim kısmına elemanın ismi, Değer kısmına veri yazılır. Değer kısmı çoğunlukla kullanıcı tarafından girileceği için boş olarak gönderilir.

***Örnek :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.TextBox("txtIsim")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yukarıdaki kod aşağıdaki kod ile aynı işleve sahiptir.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<input id="txtIsim" name="txtIsim" type="text" value="">
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.ValidationMessage**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ValidationMessage("Model","Hata mesajı")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** Bağlı bulunduğu elemanın, doğrulama kriterlerini geçmemesi durumunda, kullanıcıyı bilgilendirmek için bir hata mesajı görüntüler. Model kısmına, doğrulama yapılacak model, Hata mesajı kısmına doğrulamanın olmaması durumunda ekranda gösterilecek mesaj yazılır.

***Örnek :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ValidationMessage("kullanici", "İsim boş geçilemez")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Yukarıdaki kod aşağıdaki kod ile aynı işleve sahiptir.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<span class="field-validation-valid" data-valmsg-for="kullanici" data-valmsg-replace="false">İsim boş geçilemez</span>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Html.ValidationSummary**
--------------------------------
***Yazım Şekli :***
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ValidationSummary("Hata Mesajı")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
***Açıklama :*** İçerisinde bulunduğu formda, doğrulama hataları meydana gelmesi halinde, liste halinde tüm hataları gösterir.


**Custom HtmlHelper Metotlar**
================================

Geliştirdiğimiz projeye göre bazen mevcut Helper lar dışında ihtiyaçlarımız ortaya çıkabilir. Bu durumlarda kendi HtmlHelper larımızı yazabiliriz.
Şimdi projeye Library isminde bir klasör açıp MyExtensions adında class ekleyelim.

Extensions yazıyorsak class ın bulunduğu metodun static olma zorunluluğu var. Static class ların üyeleri de static olabilir. 

>   Static Sınıf Nedir ?
>   Bir sınıf içerisindeki static olmayan metotlara ve özelliklere o sınıftan oluşturduğumuz nesneler üzerinden erişiriz. Static olan metotlara ve özelliklere ise nesne oluşturmadan sınıf adı ile erişiriz. Static sınıflar;
>   *	new anahtar sözcüğü ile bir örnek oluşturarak kullanılmaz.
>   *	Sealed denen mühürlenmiş sınıflardır. Bu yüzden miras alınamaz ve ya veremezler.
>   *	Yapıcıları kendinden private dır ve bu sınıftan nesne üretilmesini engeller.

>   ***Örnek;***
>  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   class OrnekSinif
   {
       public static int a = 0;
   }
   class Program
   {
       static void Main(string[] args)
       {
           Console.WriteLine(OrnekSinif.a); //Sınıf ismi ile static üyeye eriştik.
       }
   }
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
> OrnekSinif içinde oluşturduğumuz static a değişkenine new ile nesne oluşturmadan Main() içinde ulaşarak kullandık.

Şimdi HtmlHelper olarak Button Helper oluşturalım. Button a özellikleri olarak id, type  ve text özelliklerini ekleyelim. Daha sonra html sayfamızda kullanalım.

![e14](https://user-images.githubusercontent.com/21074849/38163504-cdcbe550-34fd-11e8-9cab-3403926c3aca.png)

C# extensionları yazdığımız gibi bu methodu oluştururken string döndürürken ***MvcHtmlString*** döndürmeye özen göstermeliyiz. 
MvcHtmlString gönderdiğimiz string  i html e dönüştürecektir.
this HtmlHelper helper ile View de yazdığımız ***@Html.*** yazdıktan sonra Button yazısının gelmesi için yazarız.

Aynı zamanda Button extension metodunun görünür olması için oluşturduğumuz class ımızın namespace inin ***(FirstProject.Library)*** de 
View e eklenmesi gerekiyor.

![e15](https://user-images.githubusercontent.com/21074849/38163506-ce832170-34fd-11e8-9909-c84268da4728.png)

Gördüğünüz gibi ***@Html.*** dedikten sonra yazmış olduğumuz Button Helper geliyor ve onun içine girilecek değerleri (id, type, text) 
bize gösteriyor.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.Button("helperBtn", "button", "Gönder") 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
şeklinde değerlerimizi girip tarayıcımız çalıştıralım.

![e16](https://user-images.githubusercontent.com/21074849/38163509-ceda9964-34fd-11e8-8c5b-d09bd9eff910.png)

Böylece Button Helper ını ekleyip kullanmış bulunmaktayız. Şimdi Butona sağ tıklayıp Sayfa Kaynağını görüntüle dersek butonu aşağıdaki 
gibi görürüz.

![e17](https://user-images.githubusercontent.com/21074849/38163513-cf1f2c64-34fd-11e8-9e0f-bbde6cfc5d1a.png)

Şimdi ButtonHelper ı biraz daha genişletmek adına Button a type tiplerini (button, submit ve commit) ekleyelim ve id, type ve text 
değerlerinin default olarakta görünebilmesini sağlayalım.

![e18](https://user-images.githubusercontent.com/21074849/38163515-cf465d52-34fd-11e8-9641-d504d23bfb82.png)

![e19](https://user-images.githubusercontent.com/21074849/38163517-cf6cc15e-34fd-11e8-9fc4-529b7de1576f.png)

![e20](https://user-images.githubusercontent.com/21074849/38163519-cfbbeab8-34fd-11e8-9b33-12f08675f306.png)


**HtmlHelper TagBuilder**
================================

Aynı işlemleri MVC ile birlikte gelen TagBuilder ile de yapabiliriz. TagBuilder sayesinde oluşturulan Html tagına class, id, type gibi 
özellikler verilebilir.

![e21](https://user-images.githubusercontent.com/21074849/38163520-cfe31c3c-34fd-11e8-9739-78fda6da6ab5.png)

![e23](https://user-images.githubusercontent.com/21074849/38163522-d09b0720-34fd-11e8-9683-bd5570195c98.png)

***Çıktı :***

![e22](https://user-images.githubusercontent.com/21074849/38163521-d03a00f6-34fd-11e8-99d2-5c9ca70bc723.png)

**HtmlHelper Metot ile HTML Kullanma**
================================

Html de Paragraph tagını belli özellikler ile birlikte  hazır olarak kullanmak için HtmlHelper yazalım. Paragraph a id, name, border ve 
text ekleyelim.

![e24](https://user-images.githubusercontent.com/21074849/38163523-d0e71d36-34fd-11e8-8b15-654fa17337ef.png)

![e25](https://user-images.githubusercontent.com/21074849/38163524-d10f5dc8-34fd-11e8-98a5-a02cee5e4def.png)

***Çıktı:***

![e26](https://user-images.githubusercontent.com/21074849/38163525-d138f912-34fd-11e8-81e8-8b56299a5299.png)

Paragraph ın almış olduğu text i Func kullanarak özelleştirebiliriz.

![e27](https://user-images.githubusercontent.com/21074849/38163526-d16151d2-34fd-11e8-8f6e-7ce8404a9b57.png)

text tagları arasına değerleri girebiliriz.

![e28](https://user-images.githubusercontent.com/21074849/38163527-d1887514-34fd-11e8-9825-3475fa3c72da.png)

![e29](https://user-images.githubusercontent.com/21074849/38163528-d1b06344-34fd-11e8-9389-7797b76193f7.png)

**URL Helpers**
================================
URL Helper’ları geriye HTML döndürmek yerine, URL’leri build edip URL’leri string gibi döndürürler. Yani sadece URL adres döndürürler. 

***Action***
--------------------------------
MVC’ de link oluştururken 2 farklı yöntem kullanılabilir. Bunlar @Url.Action ve @Html.ActionLink dir. @Url.Action ile geriye sadece URL 
adres dönerken @Html.ActionLink ile geriye etiketli URL adresi tanımlanmış ve isimlendirilmiş şekilde dönmektedir.

*	@Html.ActionLink aşağıdaki gibi bize URL adresini verir ve HTML i döndürür.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ActionLink("Ana Sayfa", "Index", "Home")

<a href="/Admin/Home">Ana Sayfa</a>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*	@Url.Action aşağıdaki gibi URL in gideceği sadece string değeri verir.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<a href="@Url.Action("Index","Home")">Ana Sayfa</a>

<a href="/Admin/Home">Ana Sayfa</a>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

***Content***
--------------------------------
Script, CSS, resim gibi içeriklerin adreslerini belirtmek için kullanılır. Sanal bir yol oluşturur.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<link href="@Url.Content("~/Content/Site.css")" rel="stylesheet" type="text/css" />

<link href="/Content/Site.css" rel="stylesheet" type="text/css" />
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**HttpUtility**
================================

HttpUtility sınıfı, client tarafından yapılan isteğe karşı gönderilen verinin encode ve decode edilme işlemlerini gerçekleştirmektedir. Bazı durumlarda HTML karakter kodlamasında oluşan sıkıntıları gidermek için kullanılmaktadır. 

![e30](https://user-images.githubusercontent.com/21074849/38163529-d1e1a67a-34fd-11e8-9808-1f22f6a1fa25.png)

![e31](https://user-images.githubusercontent.com/21074849/38163530-d208d146-34fd-11e8-9b5d-8b66cab06c26.png)




