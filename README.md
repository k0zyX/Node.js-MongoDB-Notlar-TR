# Node.js-MongoDB-Notlar-TR
Aşağıda Node.js ve MongoDB için oluşturmuş olduğum Türkçe notları göreceksiniz. Anlayamadığım bazı konular için kendime çıkartmış olduğum bu notları başkalarının da yararlanması için paylaşmak istedim. Kendim ihtiyaç duydukça notlarımı güncelleyeceğim.

# Promise Yapısı Nasıl Kullanılır
Promise yapısı oluşturulurken kullanacağımız fonksiyonda ```return new Promise()``` nesnesi return ederiz ve Promise nesnemin constructor fonksiyonuna da bir anonim fonksiyon ( Arrow Function ) ``` () => {} ``` göndeririz. Gönderdiğimiz arrow function içerisinde ise fonksiyonumuzun gerçekleştireceği işlemleri yaparız. Göstermiş olduğum örnekte fonksiyonuma gelen datayı (parametre ismi olarak post yazmışım) data isimli dizime push ediyorum.

Push işleminden sonra ise çağırmam gereken iki adet fonksiyonum var bunlar ```resolve``` ve ```reject``` fonksiyonları.

```resolve``` -> İşlemim başarılı bir şekilde gerçekleştiyse, işlem gerçekleşirken hata almadıysam ```resolve``` fonksiyonumu çağıracağım.
```reject``` -> İşlemim başarılı bir şekilde gerçekleşmedi ve işlem gerçekleşirken hata aldıysam ```reject``` fonksiyonumu çağıracağım.

Aşağıdaki örnekte ```const error = false;``` şeklinde bir sabit değişken tanımlamamın sebebi hatayı manuel olarak true veya false şeklinde değiştirerek örneğimin çalışıp çalışmadığını kontrol etmek.

```javascript
function createData(post) {
    return new Promise((resolve, reject) => {
        data.push(post)
        const error = false;
        if (!error) {
            resolve()
        } else {
            reject("Bir hata var!")
        }
    })
}
```
Aşağıdaki kod parçası da promise içeren fonksiyonumu kullanacağım kod parçası. Burada üstte gösterdiğim ```createData()``` fonksiyonuma bir obje gönderiyorum (Gönderdiğimiz verinin konumuzla bir alakası yok ama yine de belirtmek istedim). Fonksiyonumu çalıştırdıktan sonra ```.then()``` diyerek yaptığım işlem başarılıysa (yani üstteki ```resolve()``` durumunda yapılacak işlemleri yaptırıyorum.
Fonksiyonuma aynı şekilde ```.catch()``` ile devam ediyorum. Catch ise benim üstteki fonksiyonumun ```reject()``` durumunda ne yapacağımı söylediğim fonksiyon.

Bu örneğimde ```.then()``` durumunda ```getData()``` diye tanımladığım bir fonksiyonu çağırmışım. ```.catch()``` durumunda ise err değişkeni ile hatamı loglamışım.
```javascript
createData({ title: "Title 3", description: "Title Content 3" })
    .then(getData)
    .catch(err => console.log("createData Error ->", err))
```
