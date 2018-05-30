**Models & Model Binding**
================================

Daha önceki bölümlerde Controller ve View arasında veri iletişimini ViewBag, TempData ve Request kullanarak gerçekleştireceğimizden bahsetmiştik. Bir diğer iletişimi sağlama yöntemi ise Model kullanmak.

Boş bir mvc projesi açıp controller oluşturalım. Proje açıldıktan sonra daha önceki derslerden de hatırlanacağı gibi Model isminde bir klasör oluşuyor. Bu klasör verileri taşıyan nesneleri içerir. Genelde veritabanındaki nesneleri de bunun içerisine koyarız. Hem veritabanından çekilen nesne hem de view e giden nesneleri Model klasörünün içerisinde oluşturulur.

Model klasörüne sağ tıklayıp -> Add -> class seçerek Kisi isminde class oluşturalım. Kisi class ında bulunmasını istediğimiz verileri gireceğiz.

![e97](https://user-images.githubusercontent.com/21074849/40741714-d201cc26-6454-11e8-8da5-9442f5a44400.png)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
public int MyProperty { get; set; } 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

kod satırında ***int*** nesnenin tipini, ***MyProperty***  ise nesnenin adını temsil eder. Bu kod kabı ile nesnelerimizi oluştururuz. Bu kalıbı uzun yazmak yerine prop yazıp 2 kez Tab tuşuna basmamız yeterlidir.
 
Kisi class ına Ad, Soyad ve Yas nesnelerini ekleyelim.

![e98](https://user-images.githubusercontent.com/21074849/40741715-d2443cfa-6454-11e8-8883-24c56d7d6490.png)

Nesneleri oluşturduktan sonra View ile iletişimini sağlamak için Controller da Kisi class ına ait nesne oluşturmamız gerekir.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Kisi kisi = new Kisi();
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

kod satırı ile Kisi class ına ulaşmak için kisi adında bir nesne oluşturuldu.

kisi nesnesini kullanarak Kisi class ında bulunan nesnelere ulaşılır. Daha sonra bu nesneleri View de görebilmek için 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
return View(kisi); 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

metodunda kisi nesnesini belirterek View e gideceği belirtilir.

![e99](https://user-images.githubusercontent.com/21074849/40741716-d27235ba-6454-11e8-9558-188703a0ab77.png)

Burada dikkat edilirse Kisi kısmında hata veriyor. Bunun sebebi Kisi nereden geldiğini bilmemesidir. Kisi kelimesine tıklayıp Ctrl + . ya basılırsa Models klasörünün yolunu gösterir, ona tıklayınca Controller ın en üstüne 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
using fourthProject.Models;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ekler ve hata giderilmiş olur.

![e100](https://user-images.githubusercontent.com/21074849/40741717-d2a4c3ae-6454-11e8-8cdb-2be1746457d5.png)

View sayfasında da bu model nesnesinin kullanılacağının belirtilmesi gerekir.

Projenin ismini kullanarak 2 şekilde model nesnesini tanımlayabilirsiniz.

![e101](https://user-images.githubusercontent.com/21074849/40741718-d30447de-6454-11e8-8716-d964e61c80c2.png)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Model
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

metodunu kullanarak Ad, Soyad ve Yas nesnelerini View e çekebiliriz.

![e102](https://user-images.githubusercontent.com/21074849/40741719-d345e766-6454-11e8-955c-d264ecb2b7f4.png)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Model.Ad + " " + @Model.Soyad
@(Model.Ad + " " + Model.Soyad)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yukarıdaki 2 kod satırında Ad ve Soyad nesnelerini yanyana yazmak istiyoruz. Fakat 1.kod satırında yanyana yazarken hangisinin html hangisinin razor kodu olduğunu anlamıyor. Bu karışıklığı engellemek için 2.kod satırını kullanmak daha doğru.

![e103](https://user-images.githubusercontent.com/21074849/40741721-d3a42862-6454-11e8-853e-05793be7fc5b.png)

Buraya kadar modeldeki nesneyi Controller dan View e almış olduk. Şimdi View den nesneyi model tipinde geri almayı deneyelim. Bunun için bir metod oluşturup metodun 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[HttpPost]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

şeklinde çağrılması gerekiyor.



Post olarak çağrılan homepage metodu Kisi class ında bulunan nesneleri parametre olarak alır. 

model isminde Kisi class ı için oluşturduğumuz nesneyi View metodunda geri döndürelim.

![e104](https://user-images.githubusercontent.com/21074849/40741722-d3d5018a-6454-11e8-8244-de86a6ecdb17.png)

View in hangi nesnelerin çekileceğini anlaması amacıyla 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@using (Html.BeginForm()){} 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

bloğu ve gönderme işlemini gerçekleştirmek için ***submit*** tipinde buton kullanılır.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Html.TextBoxFor(m => m.Ad)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

satırında TextBoxFor şeklinde belirtilen kısım Ad isminde nesnenin alınacağını  belirtir. Genelde For uzantısına sahip olanlar alınacak nesneyi ifade eder. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
m => m.Ad 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ise lambda kulanımıdır. Burada m harfi yerine tercihe göre istediğinizi kullanabilirsiniz.

![e105](https://user-images.githubusercontent.com/21074849/40741723-d408e72a-6454-11e8-8b4a-ff7e615adf40.png)

Projeyi çalıştırdığımızda ilk olarak varsayılan olarak gelen GET metodu çalışır. Daha sonra @using (Html.BeginForm()){} şeklinde oluşturduğumuz kısımlarda değişiklik yapıp butona tıkladığımız an POST metodu çalışır.

Aşağıdaki resim GET olarak gelen kısımdır.

![e106](https://user-images.githubusercontent.com/21074849/40741725-d44e89b0-6454-11e8-8835-7cb7b1f255dc.png)

Şimdi alt kısımda gelen bilgileri değiştirerek butona basalım.

![e107](https://user-images.githubusercontent.com/21074849/40741726-d4a5cd1a-6454-11e8-8726-87dd9c4422f5.png)

Butona basıldığında POST metodunda nesneyi tekrar View de döndürdüğümüz için aynı sayfada değişikler gelmiş oldu.

Bir sayfada bir nesne (Kisi class ı) kullanarak nesneleri kullanma işlemini gördük. Fakat bir sayfada birden fazla nesne getirmemizde gerekebilir. Bu durumda nasıl ilerleyeceğimize bakalım.

***Model*** klasöründe ***Adres*** isminde class oluşturarak içerisine Sehir ve AdresTanim nesnelerini tanımlayalım.

![e108](https://user-images.githubusercontent.com/21074849/40741727-d4e9666a-6454-11e8-99ff-6e31c607dd48.png)

![e109](https://user-images.githubusercontent.com/21074849/40741728-d53994dc-6454-11e8-91de-5f12f42bdd99.png)

Yukarıda ***return View*** metodlarında sadece Kisi nesne döndürülüyor. Fakat hem Kisi hem de Adres nesnesini döndürmek istiyorsak bu 2 nesneye özel class yapmamız gerekir. Bu özel class ları Models klasörünün içinde oluşturmamak daha doğru olur. Çünkü Models klasöründe bulunan class lar bir veritabanına ya da bir veritabanında bulunan bir tabloya karşılık gelmektedir ve Models klasöründe oluşturulan bu özel class lar karışıklığa sebep olacaktır. Karışıklığı engellemek için projede ayrı olarak bir klasör oluşturmak daha iyi olur. ***ModelViews*** isminde bir klasör oluşturarak özel class ları bu klasörde oluşturabiliriz.  

***ModelViews*** klasörü içinde ***homepageViewModel*** isminde class olşturalım. Özel oluşurulan bir class olduğunu anlamak için ViewModel isim uzantısının kullanılması daha sağlıklı olur.

![e110](https://user-images.githubusercontent.com/21074849/40741729-d59591f6-6454-11e8-8e8e-021d64119795.png)

***Kisi*** tipinde ***KisiNesnesi*** ve ***Adres*** tipinde AdresNesnesi oluşturduk. Kisi ve Adres tiplerinin tanınması için Models klasörünün yolunu da tanımlamamız gerekir.

Özel modeli tanımladıktan sonra Controller da yapılacak işlemlere geçelim;

1-	Adres class ında bulunan nesnelere (AdresTanim, Sehir) değer atayalım.

2-	View de 2 class ın nesnelerini görebilmek için özel class ı çağıralım.

3-	Return View de özel class ın nesnesini döndürelim.

![e111](https://user-images.githubusercontent.com/21074849/40741731-d5c49df2-6454-11e8-804c-7052d1fea4a0.png)

![e112](https://user-images.githubusercontent.com/21074849/40741733-d61bc7e4-6454-11e8-9777-b0c132a95a39.png)

Özel class oluşturup onun nesnesini döndürdüğümüz için homepage.cshtml de 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@model Kisi
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

olarak tanımladığımız modeli 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@model homepageViewModel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

olarak değiştimemiz gerekiyor. Buna bağlı olarakta;

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Model.Ad
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

olarak çağırdığımız nesneleri
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@Model.KisiNesnesi.Ad
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

şeklinde çağırırız.

![e113](https://user-images.githubusercontent.com/21074849/40741734-d6502642-6454-11e8-9823-8533737e3967.png)

Projeyi tarayıcıda çalıştırınca Kisi ve Adres class larına ait nesnelerin gelmiş olduğu görülür.

![e114](https://user-images.githubusercontent.com/21074849/40745985-b1d2478e-6461-11e8-984e-2c0267b5311b.png)

