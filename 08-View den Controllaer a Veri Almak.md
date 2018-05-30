**View den Controllaer a Veri Almak**
================================

Bazen gerçekleştirilen işlemlere göre View de girilen verinin alınarak Controller a getirilmesi ve buradan veritabanına kaydedilmesi (POST işlemleri gibi) ya da farklı işlemlerin gerçekleştirilmesi gerekebilir. Bu işlem için 2 yöntem uygulanır.

Yeni bir proje açarak Home Controller oluşturup Home metodunu oluşturduktan sonra Home metoduna sağ tıklayıp Add View işlemini gerçeleştirelim.

Kullanıcının bilgileri doldurması için bir sayfaya ihtiyacı vardır. Bu sayfa Get olarak gelen metottur. Daha önceki yazılardan da hatırlanacağı gibi ilk gelen metot varsayılan olarak 

 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[HttpGet]
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
şeklinde gelir fakat metodun üzerinde bu şekilde yazmaz.

![e87](https://user-images.githubusercontent.com/21074849/40741697-ce4fb0ac-6454-11e8-94a1-46e97d398fe5.png)

Kullanıcılardan gelen bilgileri Controller ın alması için ise metodun

 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[HttpPost]
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
olması gerekir. 

![e88](https://user-images.githubusercontent.com/21074849/40741698-ce9dea06-6454-11e8-8da9-5a51dc5f4d08.png)

İlk oluşturulan Home metodu kullanıcını formu görmesini ve doldurmasını sağlayan Home sayfası diğeri ise kullanıcının formda butona bastığında Controller a bilgileri getiren Home metodudur. İkinci Home metodunda kullanıcıdan alınna bilgileri Controller a getirmesi için metodun parametreye sahip olması gerekir.

Daha iyi anlamak için oluşturulan Home.cshtml sayfasında textbox, checkbox ve kullanıcının verileri controller a göndermesi için button ekleyelim.

![e89](https://user-images.githubusercontent.com/21074849/40741701-ceff3072-6454-11e8-9b30-6ae3ed638428.png)

Controller a hangi verilerin gönderildiğinin anlaşılması için gönderilecek veriler 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
@using (Html.BeginForm()) {} 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

bloğu içerisinde yazılır. Bu blok resimde yorum  satırına alınan ***form*** tagı ile aynı göreve sahiptir.

İnput tagı ile oluşturulan butonun type ise ya ***button*** ya da ***submit*** olmalıdır. Genelde submit tercih edilir. Submit geri gönderen buton türüdür.

Şimdi yukarıda da belirttiğimiz gibi kullanıcı tarafından gönderilen verilerin alınması için post metodunun parametre alması gerekiyor. Controller da alınacak parametreleri yazarak alınan parametrelerinde neler olduğunu görmek için breakpoint bırakalım.

![e90](https://user-images.githubusercontent.com/21074849/40741702-cf5c35ce-6454-11e8-8682-25e73d0e02ed.png)

F10 basıp programı çalıştırdığımızda tarayıcı açılır. Gelen sayfada textbox ve checkbox ı doldurup Gönder butonuna basınca aşağıdaki ekran karşımıza gelir.

![e91](https://user-images.githubusercontent.com/21074849/40741705-cf91f8da-6454-11e8-89eb-f234e5bba65e.png)

Text1 ve check1 parametreleri üzerine geldiğimizde textbox ve checkbox değerleri görülür.

Benzer şekilde dropdown örneği yapalım. Bu sefer  list1  razor bloğu içinde home.cshtml sayfasında oluşturalım. Daha sonra controller a parametreyi belirtelim.

![e92](https://user-images.githubusercontent.com/21074849/40741709-d102d41e-6454-11e8-9c2a-2173212466d5.png)
![e93](https://user-images.githubusercontent.com/21074849/40741710-d13398b0-6454-11e8-8063-6a1a792349b7.png)

F10 a basıp çalıştırdığımızda controllerde seçtiğimiz seçeneğin ***Value*** değeri döner.

![e94](https://user-images.githubusercontent.com/21074849/40741711-d1641850-6454-11e8-8201-c7a4cd05da43.png)

Resimde de görüldüğü gibi Value değeri 1 olan seçenek seçildiği için Controllerda da 1 geldi. Eğer Value değeri yazılmasaydı ve seçeneklerden Kırımlı seçilmiş olsaydı Controller a Kırımlı olarak data gelmiş olurdu. Boş data gelmezdi.
Controller a bilgi çekmek için kullanıla bir başka yöntem ise Request nesnesini kullanmaktır. Request nesnesine ait olan Form özelliği sayesinde girilen key e göre data controller a gelir.

![e95](https://user-images.githubusercontent.com/21074849/40741712-d1962084-6454-11e8-853c-30bbee9e2386.png)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
var c1 = Request.Form.GetValues("check1")[0]; 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

şeklindeki kod satırında [0] kısmı kullanılmazsa ***“true,false”*** döner. [0] kullanarak seçili olan değeri döndürmüş oluruz. Seçim yapıldıysa ***“true,false”*** döner ve sıfırıncı indeksi aldığı için true değeri gelir, seçim yapılmadıysa “false,true” döner ve sıfırıncı indeks döndüğü için false gelir.

F10 basarak programı çalıştırdığımızda Controller a verilerin geldiği görülür.

![e96](https://user-images.githubusercontent.com/21074849/40741713-d1d2da74-6454-11e8-94eb-4f1054c19e38.png)

