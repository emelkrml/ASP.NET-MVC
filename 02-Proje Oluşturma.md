**Proje Oluşturma**
================================

Visual Studio’ da sol üstte File -> New -> Project diyoruz.

![e1](https://user-images.githubusercontent.com/21074849/38163491-caaf4254-34fd-11e8-98a4-a698cff0b684.png)

Gelen ekranda sol tarafta Web kısmını seçip solda ***ASP.NET Web Application (.NET Framework)*** seçip ***Browse*** kısmından projeyi kaydedeceğimiz klasörü seçiyoruz.
***Name*** yazan yere proje adımızı yazıp OK diyelim. 

![e2](https://user-images.githubusercontent.com/21074849/38163492-cad72f08-34fd-11e8-8022-e86b45dbf61e.png)

Sonraki ekranda ise ***Empty*** seçip ***MVC*** kısmına tıklayarak OK diyelim. 

Bu kısımda Empty yerine MVC yi seçseydik bazı sayfalar hazır olarak gelecekti. Biz şuan boş gelmesi için Empty i seçelim. 

Sol tarafta Solution Explorer da ***Controllers, Models*** ve ***Views*** olmak üzere hazır kalıp klasörlerimiz gelecek. Bu klasörlere 
ilgili class lar yazılacak.Bu mimari neyin nerede olacağını belirten bir düzen sağladığından dolayı birden çok kişinin çalışacağı uygulamalarda kimin 
nereye ne yazması gerektiğini düzenliyor.Böylece kodlarda meydana gelebilecek düzensizlikler engellenmiş olur. 

![e3](https://user-images.githubusercontent.com/21074849/38163493-cafc39f6-34fd-11e8-932d-cd248b35e177.png)

Controllers a sağ tıklayıp ***Add -> Controller -> MVC 5 Controller – Empty***  ı seçip Controller ismini **HomeController** olarak girip Controller ekleyelim.

![e4](https://user-images.githubusercontent.com/21074849/38163494-cb2328ea-34fd-11e8-86dd-2a361e9fb1b6.png)

Oluşturulan Controller ların isimleri her zaman Controller uzantılı olmalı. Aynı zamanda Controller eklediğimizde Views klasörü içinde 
oluşturulan Controller isminde bir klasör oluşur.

HomeController ı olurturduğumuzda Views klasörünün içinde ***Home*** isminde klasör oluştu. ***HomeController*** da oluşturduğumuz her 
method/action da Home klasörünün içinde **.cshtml** uzantılı bir dosyamız oluşacak. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
public class HomeController : Controller 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
satırı bize HomeController ın Controller methodundan miras aldığını gösterir.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// GET: Home
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Index metodunun GET olarak geleceğini belirtir. Eğer metodun üzerinde GET ya da POST yazmazsa GET olarak çalışır. Metodun POST olarak 
gelmesini istiyorsak 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[HttpPost]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
şeklinde yazarız.

>   GET methodu HTTP istekleri arasındaki varsayılan yöntemdir. GET metodu ile yapılan istekler tarayıcının adres satırında görünür. 
Sadece belirli boyutta veri gönderileceği zaman kullanılır.

>   POST metodu ise URL’ de görünmesini istemediğimiz veriler olduğunda, dosya yükleyeceğimiz zaman, querystring’in çok büyük olduğu 
durumlarda kullanılır. POST yönteminde gönderebileceğimiz verinin boyutu ile ilgili bir sınır yoktur. Ayrıca gönderdiğimiz parametrelerin
adres satırında görünmemesi dolayısıyla GET yöntemine göre daha güvenlidir. HTML form gönderileceği zaman genelde POST yöntemi tercih 
edilir.

>   GET -> Sayfayı çağırmak

>   POST -> Sayfadan veriyi almak. Veriler sunucuya tekrar geri döner.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
public ActionResult Index() 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ise bir metod/action dır. Controller da oluşturduğumuz her bir method bizi bir sayfaya yönlendirir.

Şimdi View oluşturmak için ***Index()*** e sağ tıklayıp  Add View diyelim.

![e5](https://user-images.githubusercontent.com/21074849/38163495-cb494782-34fd-11e8-852c-46eae4c7bbad.png)

Burada hiçbir şeye tıklamadan Add diyelim. ***Views -> Home*** klasörü içinde HomeController da bulunan Index Action için ***Index.cshtml***
isimli html dosya oluşur. Bu şekilde hangi action ın hangi klasör içinde olacağını ASP.NET isimlerden anlayarak yapıyor.

Index.cshtml dosyasına sağ tıklayıp View in Browser deyip çalıştıralım.

![e6](https://user-images.githubusercontent.com/21074849/38164008-4bd1000e-3506-11e8-94d8-aa6f9edb7836.png)

Tarayıcıda ***Home/Index***’ te; Home; Controller ı Index ise o Controller daki actionı gösterir.

Kısacası MVC nin çalışma mantığı bu şekildedir. 
