**ViewBag, ViewData ve TempData**
================================

Bu yapılar Controller ile View arasında veri taşımamızı sağlar. Aralarında bazı farklar vardır sadece.

**ViewData;** ViewDataDictionary sınıfı ile Key/Value ilişkisine göre çalışır. Söz dizimi;
	 
   ***ViewData[“Key”] = Value;***
   
şeklindedir.

**ViewBag;** ViewBag MVC 3 C# 4 ile birlikte geldi. ViewData’ nın dinamik halidir ve aynı işi görürler. Dinamik bir tip olduğu için runtime da derlenir. Aynı ViewBag değişkeni için birden fazla tanım yapılırsa son tanımlama geçerli olur.  Söz dizimi;

	***ViewBag.Degisken = Deger;***
  
şeklindedir.

**TempData;** ViewBag ve ViewData ile aynı işlevi görür. TempData veriyi Request bazlı saklamaz. Bu nedenle Action veya farklı Controller Action’lar arasında bir transfer işlemi yapılacaksa veya View üzeride aynı durum söz konusuysa kullanılabilir. Yani View ler arasında da veriyi taşır. Taşıma işlemi diğer action a redirect edilmesi ile yapılır.

TempData da sayfa PostBack olur ya da yenilenirse veri kaybolur. Söz dizimi;
	 
   ***TempData[“Key”] = Value;***
   
şeklindedir.

Şimdi yeni bir uygulama açıp aşağıdaki kodları yazalım. 

![e62](https://user-images.githubusercontent.com/21074849/38460285-3915a9c4-3abf-11e8-9315-c54e3d6dd283.png)

![e63](https://user-images.githubusercontent.com/21074849/38460286-3947f14a-3abf-11e8-9c20-8e57664c947a.png)

HomeController da Index metoduna dikkat edilirse RediretToAction ile About sayfasına yönlendirme gerçekleşiyor. Bu şekilde ViewBag ve ViewData verileri görüntülenmeyecek. Çünkü sadece Index metodunca çalışabilir. 1 tane sıçrama yapılabilir. Fakat TempData 2 sıçrama yapabilir. Hem Index hem de About metodunda görüntülenir.

About.cshtml i tarayıcı da çalıştıralım.

![e64](https://user-images.githubusercontent.com/21074849/38460287-39783eea-3abf-11e8-9214-3a2f8cd1bd61.png)

Şimdi sayfayı yenilersek TempData ile gelen verinin kaybolduğunu göreceğiz.

![e65](https://user-images.githubusercontent.com/21074849/38460288-39aa5fc4-3abf-11e8-9d0c-5d5d3f5a7030.png)

TempData üzerindeki veriyi üçüncü request e aktarmak istiyorsak ***Keep()*** metodunu kullanabiliriz.

![e66](https://user-images.githubusercontent.com/21074849/38460289-3f4ff826-3abf-11e8-85e7-61794b2a728e.png)

