**Controller dan View e Veri Gönderme**
================================

**1. ViewBag, ViewData ve TempData**

Bu yapılar Controller ile View arasında veri taşımamızı sağlar. Aralarında bazı farklar vardır sadece.

**ViewData;** ViewDataDictionary sınıfı ile Key/Value ilişkisine göre çalışır. Söz dizimi;

	 ViewData[“Key”] = Value;
şeklindedir.

**ViewBag;** ViewBag MVC 3 ile C# 4 ile birlikte geldi. ViewData’ nın dinamik halidir ve aynı işi görürler. Dinamik bir tip olduğu için runtime da derlenir. Aynı ViewBag değişkeni için birden fazla tanım yapılırsa son tanımlama geçerli olur.  Söz dizimi;

  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ViewBag.Degisken = Deger;
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  
şeklindedir.

**TempData;** ViewBag ve ViewData ile aynı işlevi görür. TempData veriyi Request bazlı saklamaz. Bu nedenle Action veya farklı Controller Action’lar arasında bir transfer işlemi yapılacaksa veya View üzeride aynı durum söz konusuysa kullanılabilir. Yani View ler arasında da veriyi taşır. Taşıma işlemi diğer action a redirect edilmesi ile yapılır.  
TempData da sayfa PostBack olur ya da yenilenirse veri kaybolur. Söz dizimi;

	 TempData[“Key”] = Value;
şeklindedir.


Şimdi yeni bir uygulama açıp aşağıdaki kodları yazalım. 

![e62](https://user-images.githubusercontent.com/21074849/38460285-3915a9c4-3abf-11e8-9315-c54e3d6dd283.png)


![e63](https://user-images.githubusercontent.com/21074849/38460286-3947f14a-3abf-11e8-9c20-8e57664c947a.png)


HomeController da Index metoduna dikkat edilirse RediretToAction ile About sayfasına yönlendirme gerçekleşiyor. Bu şekilde ViewBag ve ViewData verileri görüntülenmeyecek. Çünkü sadece Index metodunca çalışabilir. 1 tane sıçrama yapılabilir. Fakat TempData 2 sıçrama yapabilir. Hem Index hem de About metodunda görüntülenir.

About.cshtml i tarayıcı da çalıştıralım.


![e64](https://user-images.githubusercontent.com/21074849/38460287-39783eea-3abf-11e8-9214-3a2f8cd1bd61.png)


Şimdi sayfayı yenilersek TempData ile gelen verinin kaybolduğunu göreceğiz.


![e65](https://user-images.githubusercontent.com/21074849/38460288-39aa5fc4-3abf-11e8-9d0c-5d5d3f5a7030.png)


TempData üzerindeki veriyi üçüncü request e aktarmak istiyorsak Keep() metodunu kullanabiliriz.

![e66](https://user-images.githubusercontent.com/21074849/38460289-3f4ff826-3abf-11e8-85e7-61794b2a728e.png)

**2. HtmlHelper**

Daha önce HtmlHelper lardan bahsetmiştik. Şimdi ise HtmlHelper kullanarak Controller dan veri çekmeye bakacağız. 

About2 adında ActionResult oluşturup About2 ye sağ tıklayarak Add View -> Add diyelim. 


![e75](https://user-images.githubusercontent.com/21074849/40741683-ca76d8de-6454-11e8-8f89-58c3598bdbc1.png)


![e76](https://user-images.githubusercontent.com/21074849/40741684-caa680c0-6454-11e8-8472-48dfc0c56836.png)

ViewBag olarak oluşturduğumuz text1 ve check değerlerini  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 @ViewBag.text1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

şeklinde çağırabileceğimiz gibi

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 @Html.TextBox("text1")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

şeklinde de çağırırız.


![e77](https://user-images.githubusercontent.com/21074849/40741685-cad54680-6454-11e8-9cce-63be087164cd.png)

Farklı HtmlHelper tiplerini kullanarak sonuçları görelim.

![e78](https://user-images.githubusercontent.com/21074849/40741686-cb023a50-6454-11e8-95d7-af07b4937dfa.png)

![e79](https://user-images.githubusercontent.com/21074849/40741688-cb2e05f4-6454-11e8-91c1-8461243710cc.png)

Sayfa tarayıcı da çalıştırıldığında text1 parametresinin geldiği görülür. Bir diğer dikkat edilmesi gereken konu ise sayfaya incele denildiğinde input ta gelen id ve name isimlerinin text1 isminde gelmesidir.


Bu kısımda genelde gelen HtmlHelper lar input olduğu için bir hata ile karşılaşılmadı. Fakat dropdown olsaydı hata alınacaktı. Dropdown olarak ViewBag deki parametre Dropdown HtmlHelper olarak çağırmak için parametrenin seçenekli yapıya uygun olması gerekir.

![e80](https://user-images.githubusercontent.com/21074849/40741689-cb681a8c-6454-11e8-981c-6037196a84a9.png)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.DropDownList("list1") 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

yazarak ViewBag çekilebilir.

![e81](https://user-images.githubusercontent.com/21074849/40741690-cbb48bf6-6454-11e8-8fa4-bc0eaf1b726b.png)

Aynı şekilde dropdown ı incelendiğinde id ve name isimleri list1 şeklinde gelir.

HtmlHelper yapısını kullanmadan input tagını kullanrakta ViewBag çekilebilir.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
<input type="text" value="@ViewBag.text1" />
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bu şekilde yukarıdaki örnekte TextBox HtmlHelper ında geldiği gibi bir çıktı alınır. id ve name isimlerinin girilmesine gerek yoktur.


Şimdi ise ViewBag lerin ömrünü anlamak adına bir örnek gerçekleştirelim.
Contact2 adında ActionResult oluşturarak sağ tıklayıp Add View diyelim.

![e82](https://user-images.githubusercontent.com/21074849/40741691-cc099d6c-6454-11e8-9356-b03c1b6cbfae.png)

Önceki örnekte oluşturulan About2.cshtml sayfasına 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.ActionLink("Contact2 sayfasına git", "Contact2") 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
kodunu yazalım.

Oluşturulan Contact2.cshtml sayfası aşağıdaki kod satırlarını yazalım.

![e83](https://user-images.githubusercontent.com/21074849/40741692-cc443896-6454-11e8-855d-022061349525.png)

Gerçekleştirdiğimiz işlem şu şekilde olacaktır; About2 sayfası çalıştırılacak, bu sayfada Contact2 sayfasına git linkine tıklanacak ve gelen sayfada About2 sayfasındaki ViewBag lerin gelip gelmediğini kontrol edeceğiz. Bu işlemleri gerçekleştirince Contact2 sayfası aşağıdaki gibi gelir.


![e84](https://user-images.githubusercontent.com/21074849/40741693-ccabcd4e-6454-11e8-9567-5e6514dc7507.png)

İkinci bir sıçramayı TempData kullanrak sağlayabiliriz. TempData 1sıçramalık veriyi tutabilir.

![e85](https://user-images.githubusercontent.com/21074849/40741695-cd73e96e-6454-11e8-9314-60eb060e691d.png)

About2 metodunda tuttuğumuz text1 ve check1 parametrelerini Contact2 metodunda çağırarak ikinci sıçramada verilerin gelmesini sağlayabiliriz. 

Az önceki işlemleri sırası ile tekrar yapalım. About2 sayfasını çalıştırarak Contact2 sayfasına geçildiğinde verilerin geldiği görülür.

![e86](https://user-images.githubusercontent.com/21074849/40741696-ce210b58-6454-11e8-8dfd-b04565881b1c.png)

Contact2 den başka bir sayfa sıçrama gerçekleştirmek isteseydik veriler TempData da 1 sıçramalık durduğu için gözükmeyecekti.



