### Liskov_Subsitute_Principle nedir?

Bu prensibin odak noktası alt seviyedeki nesnelerin, üst seviyedeki nesneler ile yer değiştirebilir olmasını garanti etmek ve mümkün kılmaktır. Alt seviye bir nesne, üst seviyesi nesne ile aynı şekilde davranmalıdır ki bu sayede yer değişmeleri halinde her şeyin aynı şekilde çalışabilmesi sağlanabilsin.

Örneğin arabalar bir taşıttır. Ancak her arabanın özellikleri aynı değildir. Bazı arabalarda navigasyon bulunurken, bazı arabalarda bulunmaya bilir. Bu gibi durumlarda ortak olarak bu methodları tüm taşıt sınıfları için ortak yazarsak bu prensibimizin mantığına ters düşmüş oluruz.

```
import Foundation

protocol Vehicle {
    func run()
    func sunroof() -> Bool?
    func navigation() -> Bool?
}

class Car: Vehicle {

    func run() {
        print("hann hannnnn...")
    }

    func sunroof() -> Bool? {
        return true
    }

    func navigation() -> Bool? {
        return true
    }
}

class RangeRover: Car {

    override func run() {
        print("Vınn Vınn...")
    }

    override func sunroof() -> Bool? {
        return true
    }

    override func navigation() -> Bool? {
        return true
    }
}

class Sahin: Car {

    override func run() {
        print("Zınn Zınnn...")
    }

    override func sunroof() -> Bool? {
        return nil //
    }

    override func navigation() -> Bool? {
        return nil //
    }
}
```

Sahin sınıfı Car sınıfını kalıtım yolu ile aldığı zaman çalıştıramayacağı methodlarıda almış olur. Bu yapıyı prensibimize uyarlamamız için yapılarımızı ayırıp daha özel bir şekilde yazmamız gerekli yada Vehicle protokolünde bulunan methodları ve değişkenleri tüm arabalarda bulunacak özellikler olacak şekilde tasarlamamız gerekli. Örneğin (gaza bas, fren yap, araba hızı vs gibi bilgiler)

## Liskov_Subsitute_Principle neden vardır?

Bir programdaki nesneler, o programın doğruluğunu değiştirmeden alt türlerinin örnekleriyle değiştirilebilir olmalıdır. Başka bir deyişle, her alt sınıf, alt sınıfa özgü tüm yeni davranışlarla birlikte temel sınıftaki tüm davranışları korumalıdır. Alt sınıf, aynı istekleri işleyebilmeli ve üst sınıfıyla aynı görevleri tamamlayabilmelidir.

Liskov Subsitute Principle(LSP)’nin avantajı, aynı türdeki tüm alt sınıfların tutarlı bir kullanımı paylaştığı için yeni alt sınıfların geliştirilmesini hızlandırmasıdır. Yeni oluşturulan tüm alt sınıfların mevcut kodla çalışabilir. Yeni bir alt sınıfa ihtiyacınız olduğu zaman mevcut kodu yeniden çalışmadan oluşturabilmenize olanak sağlar.

## Liskov_Subsitute_Principle nasıl vardır?

Orjinal ifadesi ile “Subclasses should be substitutable for their base classes“, her bir alt sınıf, türetilmiş olduğu, temel sınıflar yerine kullanılabiliyor olmalıdır. Bir diğer ifade ile, temel sınıfı kullanan herhangi bir kullanıcı sınıf, aynı şekilde, bu temel sınıftan türetilmiş olan sınıfı da kullanabiliyor olmalıdır. Bunu aşağıdaki figür ile gösterebiliriz.

![alt text](https://sp-ao.shortpixel.ai/client/to_webp,q_glossy,ret_img,w_300/https://www.yazilimperver.com/wp-content/uploads/2019/09/img_5d7565426ac73-300x206.png)

Bu ifade, ilk bakışta, gayet açık gelebilir, ama burada göz önünde bulundurmamız gereken bir takım hususlar var. Buna geometrik sınıflar üzerinden bir göz atalım. Bu anlamda Çember/Elipse sınıflarına ve bunların ilişkilerini ele alalım. Çoğumuz bu iki sınıfı düşünürken, aslında elipsin daha genel ve çemberin de aslında elipsin özel bir durumu olduğunu düşüne gelmişizdir. Bu da bizi, bu iki sınıfı miras mekanizması ile ilişkilendirmeye itebilir. Bunun sonucu olarak, elips temel sınıf ve çember de bunun alt sınıfı olarak kabul edilebilir.

![alt text](https://sp-ao.shortpixel.ai/client/to_webp,q_glossy,ret_img,w_150/https://www.yazilimperver.com/wp-content/uploads/2019/09/img_5d75690f9e39f-150x266.png)

İlk bakışta bu yaklaşımda herhangi bir sıkıntı görünmese de, biraz daha yakından baktığımızda bir takım hususların kendisini göstereceğini göreceğiz.

![alt text](https://sp-ao.shortpixel.ai/client/to_webp,q_glossy,ret_img,w_300/https://www.yazilimperver.com/wp-content/uploads/2019/09/img_5d756b04919af-300x177.png)
