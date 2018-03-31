**Razor Syntax**
================================

![e7](https://user-images.githubusercontent.com/21074849/38163497-cc759174-34fd-11e8-8cad-3901503aa936.png)

Çerçeve içersine aldığımız yer bir Razor Syntax örneğidir. Html dosyalarında ***@*** işaretini kullanarak C# kodlarını kullanırız. Yani ***@*** işareti ile kodların Html mi C# mı kodları olduğunu 
ayırt ediyoruz.

![e8](https://user-images.githubusercontent.com/21074849/38163498-cc9cd482-34fd-11e8-8fe2-0bbfd06b6f26.png)

Yazdığımız bu kod satırı sadece server tarafında çalışır. Html sayfasında bir çıktı göstermez.
Html dosyasında oluşturduğumuz bu değişkenleri göstermek için; 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@ad 
@soyad 
@adSoyad      
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

yazarak değişkenlerimizi html sayfasına bastırabiliriz.

![e9](https://user-images.githubusercontent.com/21074849/38163499-ccc644c0-34fd-11e8-8d20-24d6f0a67463.png)

Razor blokları arasında döngü işlevlerini de geçekleştirebiliriz. Şimdi bir örnek daha yapalım.

![e10](https://user-images.githubusercontent.com/21074849/38163500-ccefaa90-34fd-11e8-839e-0fcc30f00453.png)

Yukarıdaki örnekte Razor bloğunda C# kodları ile adlar isminde bir dizi tanımladık ve dizideki verileri @ işaretini kullanarak html 
sayfasında listeledik.

***Razor View Engine Açıklama Satırı***
-  //; birden çok satır yazılacaksa kullanılır ve html sayfalarında Razor bloğunun içinde kulanılabilir. Razor bloğunun içinde olmaz ise html sayfalarında kullanılmaz.
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
	// GET: Home
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Html sayfalarında Razor bloğunun içinde kulanılabilir.

-   /**/; tek satır yazılacaksa kullanılır ve html sayfalarında Razor bloğunun içinde kulanılabilir. Razor bloğunun içinde olmazsa kullanılmaz.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/*public ActionResult Kategoriler()
   {
       return View();
}
*/
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   @**@; birden çok satır yazılacaksa kullanılır.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 @*<ul>
    @foreach (var ad in adlar)
    {
        <li>@ad</li>
    }
</ul>*@
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
