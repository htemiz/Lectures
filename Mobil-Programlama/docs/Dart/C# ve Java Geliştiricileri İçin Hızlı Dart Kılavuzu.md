<a id="top"></a>
# C# ve Java Geliştiricileri İçin Hızlı Dart Kılavuzu


Bu kılavuz, statik tipli (C#/Java) dillerden gelen geliştiricilerin Dart diline hızlı adapte olmasını sağlamak amacıyla hazırlanmıştır. 

---

 ✎ **Geri Bildirim**

Bu doküman hazırlanırken mümkün olan en yüksek özen gösterilmiştir.  
Buna rağmen gözden kaçmış hata veya eksiklikler bulunabilir.  
Tespit ettiğiniz hataları bildirmeniz içeriğin geliştirilmesine katkı sağlayacaktır.

✉ **İletişim:** [Doç. Dr. Hakan Temiz](mailto:htemiz@artvin.edu.tr)

---

<a id="toc"></a>
## İçindekiler

- [1. Temel Sözdizimi ve Değişkenler](#1-temel-sözdizimi-ve-değişkenler)
  - [1.1. Değişken Tanımlama ve Tip Çıkarımı (Type Inference)](#11-değişken-tanımlama-ve-tip-çıkarımı-type-inference)
  - [1.2. final ve const](#12-final-ve-const)
  - [1.3. Enum Yapıları (Modern Dart)](#13-enum-yapıları-modern-dart)
    - [1.3.1. Basit Enum](#131-basit-enum)
    - [1.3.2. Enum + Switch Kullanımı](#132-enum--switch-kullanımı)
    - [1.3.3. Gelişmiş Enum (Alan ve Metot İçeren)](#133-gelişmiş-enum-alan-ve-metot-içeren)
    - [1.3.4. Nerelerde Kullanılır?](#134-nerelerde-kullanılır)

- [2. Null Safety (Null Güvenliği) ve late](#2-null-safety-null-güvenliği-ve-late)
  - [2.1. Null Safety (Null Güvenliği)](#21-null-safety-null-güvenliği)
  - [2.2 late Anahtar Kelimesi](#22-late-anahtar-kelimesi)

- [3. Fonksiyonlar (Functions)](#3-fonksiyonlar-functions)
  - [3.1. Temel ve Arrow (Ok) Fonksiyonları](#31-temel-ve-arrow-ok-fonksiyonları)
  - [3.2. İsimlendirilmiş Parametreler (Named Parameters)](#32-isimlendirilmiş-parametreler-named-parameters)
    - [3.2.1. Üç Farklı Durum (Null Safety ile Birlikte)](#321-üç-farklı-durum-null-safety-ile-birlikte)
      - [3.2.1.A. Zorunlu Parametreler (required)](#321a-zorunlu-parametreler-required)
      - [3.2.1.B. Varsayılan Değerli (Default Value)](#321b-varsayılan-değerli-default-value)
      - [3.2.1.C. Null Olabilir (Nullable)](#321c-null-olabilir-nullable)
    - [3.2.2. Karışık Kullanım (Positional + Named)](#322-karışık-kullanım-positional--named)
    - [3.2.3. C# Geliştiricileri İçin Kritik Fark](#csharp-gelistiricileri-icin-kritik-fark)
    - [3.2.4. Flutter İçin Neden Hayati?](#324-flutter-i̇çin-neden-hayati)
  - [3.3. typedef (Fonksiyon Tipi Takma Adı)](#33-typedef-fonksiyon-tipi-takma-adı)
  - [3.4. Veri Tipi İçin typedef (Type Alias)](#34-veri-tipi-i̇çin-typedef-type-alias)

- [4. Sınıflar ve OOP (Classes)](#4-sınıflar-ve-oop-classes)
  - [4.1. Erişim Belirleyiciler (Access Modifiers)](#41-erişim-belirleyiciler-access-modifiers)
  - [4.2. Constructor (Yapıcı Metotlar)](#42-constructor-yapıcı-metotlar)
  - [4.3. factory Neden Gereklidir?](#43-factory-neden-gereklidir)
  - [4.4. factory ile fromJson Deseni](#44-factory-ile-fromjson-deseni)
  - [4.5. Normal Constructor vs Factory Constructor](#45-normal-constructor-vs-factory-constructor)
  - [4.6. Nesne Eşitliği (== ve hashCode)](#46-nesne-eşitliği--ve-hashcode)
  - [4.7. Varsayılan Davranış (Referans Eşitliği)](#47-varsayılan-davranış-referans-eşitliği)
  - [4.8. Object Sınıfı ve Temel Metotlar](#48-object-sınıfı-ve-temel-metotlar)
  - [4.9. const Constructor ve Immutable Nesneler](#49-const-constructor-ve-immutable-nesneler)

- [5. Kalıtım ve Arayüzler (Inheritance & Interfaces)](#5-kalıtım-ve-arayüzler-inheritance--interfaces)
  - [5.1. Interface (Implements)](#51-interface-implements)
  - [5.2. Mixins (with Anahtar Kelimesi)](#52-mixins-with-anahtar-kelimesi)
  - [5.3. covariant Anahtar Kelimesi](#53-covariant-anahtar-kelimesi)
  - [5.4. sealed, base ve final Sınıflar (Dart 3+)](#54-sealed-base-ve-final-sınıflar-dart-3)

- [6. Asenkron Programlama (Future & Stream)](#6-asenkron-programlama-future--stream)
  - [6.1. Asenkron Programlama Nedir?](#61-asenkron-programlama-nedir)
  - [6.2. Future](#62-future)
  - [6.3. Birden Fazla Asenkron İşlem](#63-birden-fazla-asenkron-i̇şlem)
  - [6.4. Asenkron Hata Yönetimi](#64-asenkron-hata-yönetimi)
  - [6.5. Stream](#65-stream)
  - [6.6. StreamController (Giriş)](#66-streamcontroller-giriş)
  - [6.7. Future vs Stream (Özet Tablo)](#67-future-vs-stream-özet-tablo)

- [7. Dart’ta Hata Yönetimi (Error Handling)](#7-dartta-hata-yönetimi-error-handling)
  - [7.1. try / catch Temel Kullanım](#71-try--catch-temel-kullanım)
  - [7.2. assert Anahtar Kelimesi](#72-assert-anahtar-kelimesi)

- [8. Koleksiyonlar ve Döngüler (Imperative Yaklaşım)](#8-koleksiyonlar-ve-döngüler-imperative-yaklaşım)

- [9. Koleksiyonlar ve Fonksiyonel Metotlar (LINQ Karşılıkları)](#9-koleksiyonlar-ve-fonksiyonel-metotlar-linq-karşılıkları)
  - [9.1. Karşılaştırma Tablosu (C# - Java - Dart)](#91-karşılaştırma-tablosu-c---java---dart)
  - [9.2. Detaylı Örnekler ve Kritik Farklar](#92-detaylı-örnekler-ve-kritik-farklar)
  - [9.3. Koleksiyonlar İçinde "For" ve "If" (Collection For & If)](#93-koleksiyonlar-i̇çinde-for-ve-if-collection-for--if)
  - [9.4. Spread Operator (...)](#94-spread-operator)
  - [9.5. Iterable için Extension Metotlar](#95-iterable-için-extension-metotlar)

- [10. Dart Paket Yönetimi: Pub & pubspec.yaml](#10-dart-paket-yönetimi-pub--pubspecyaml)
  - [10.1. pubspec.yaml Dosyası (Projenin Kalbi)](#101-pubspecyaml-dosyası-projenin-kalbi)
  - [10.2. Versiyonlama ve Caret (^) Sembolü](#102-versiyonlama-ve-caret--sembolü)
  - [10.3. pubspec.lock (Gerçek Kayıt)](#103-pubspeclock-gerçek-kayıt)

- [11. Dart/Flutter Proje Mimarisi ve Klasör Yapısı](#11-dartflutter-proje-mimarisi-ve-klasör-yapısı)
  - [11.1. Kök Dizin (Root Directory)](#111-kök-dizin-root-directory)
  - [11.2. "Lib" Klasörünün İçi: Mimari Yaklaşımlar](#112-lib-klasörünün-i̇çi-mimari-yaklaşımlar)
  - [11.3. "Barrel File" Deseni](#113-barrel-file-deseni)
  - [11.4. Import Yöntemleri: Relative vs Absolute](#114-import-yöntemleri-relative-vs-absolute)
  - [11.5. Private Dosyalar ve Kapsülleme](#115-private-dosyalar-ve-kapsülleme)

- [12. Örnek Proje: Kullanıcı Yönetim Simülasyonu](#12-örnek-proje-kullanıcı-yönetim-simülasyonu)
  - [C# Geliştiricisi Gözüyle Kod Analizi](#c-geliştiricisi-gözüyle-kod-analizi)


---


## 1. Temel Sözdizimi ve Değişkenler

__Dart__, Google tarafından geliştirilen, Type Safe (Tip Güvenli), hem JIT (Just In Time - Geliştirme anında hızlı derleme) hem de AOT (Ahead Of Time - Production için makine koduna derleme) özelliklerine sahip bir dildir.

Dart sözdizimi C# ve Java'ya çok benzer. Noktalı virgül (;) kullanımı zorunludur.


### 1.1. Değişken Tanımlama ve Tip Çıkarımı (Type Inference)

C# 'taki var kullanımı Dart'ta da geçerlidir. Dart tip güvenli bir dildir, ancak tipleri otomatik olarak çıkarabilir.


```dart
// Açık tip belirtme (Java/C# tarzı)
String name = "Ahmet";
int age = 30;

// Tip çıkarımı (Type Inference) - Önerilen
var city = "Istanbul"; // Dart bunun String olduğunu bilir.
// city = 10; // HATA! String bekler.

// Dinamik tip (C# dynamic benzeri)
dynamic anything = "Hello";
anything = 123; // Hata vermez, ancak dikkatli kullanılmalıdır.
```
### 1.2. final ve const

Java'daki final ve C# 'taki readonly/const kavramlarının karşılığıdır.

- final: Çalışma zamanında (runtime) değer atanır ve bir daha değiştirilemez. (Örnek: HTTP isteğinden gelen veri).
- const: Derleme zamanında (compile-time) değeri bilinmelidir ve sabittir.

final: Çalışma zamanında (runtime) değer atanır ve bir daha değiştirilemez. (Örnek: HTTP isteğinden gelen veri).

const: Derleme zamanında (compile-time) değeri bilinmelidir ve sabittir.


```dart
final DateTime now = DateTime.now(); // Çalışma zamanında oluşur.
const double pi = 3.14; // Derleme zamanında bellidir.
```

### 1.3. Enum Yapıları (Modern Dart)

Enum’lar, sabit ve sınırlı durumları temsil etmek için kullanılır.

C# ve Java geliştiricileri için tanıdık bir yapıdır ancak
Dart’ta **çok daha güçlüdür**.

---

#### 1.3.1. Basit Enum

```dart
enum UserRole {
  admin,
  editor,
  user
}
```

```dart
UserRole role = UserRole.admin;
```

---

#### 1.3.2. Enum + Switch Kullanımı

```dart
switch (role) {
  case UserRole.admin:
    print("Admin");
    break;
  case UserRole.editor:
    print("Editor");
    break;
  case UserRole.user:
    print("User");
    break;
}
```

---

#### 1.3.3. Gelişmiş Enum (Alan ve Metot İçeren)

Dart 2.17+ ile enum’lar constructor alabilir.

```dart
enum OrderStatus {
  pending("Beklemede"),
  shipped("Kargoya verildi"),
  delivered("Teslim edildi");

  final String label;
  const OrderStatus(this.label);
}
```

```dart
var status = OrderStatus.shipped;
print(status.label);
```

---

#### 1.3.4. Nerelerde Kullanılır?

- UI state
- API response status
- Workflow yönetimi
- Yetkilendirme (role)

📌 Enum kullanmak:
- Magic string’leri ortadan kaldırır
- Kod güvenliğini artırır

</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)


## 2. Null Safety (Null Güvenliği) ve late

### 2.1. Null Safety (Null Güvenliği)
Dart 2.12+ sürümü ile birlikte "Sound Null Safety" özelliği gelmiştir. C# 8.0'daki "Nullable Reference Types" özelliğine çok benzer ancak daha katıdır. Varsayılan olarak değişkenler null olamaz.


```dart
// Non-nullable (Null olamaz)
String title = "Dart"; 
// title = null; // DERLEME HATASI!

// Nullable (Null olabilir)
String? description = null; // '?' işareti null olabileceğini belirtir.

// Null Check (Kontrol)
if (description != null) {
  print(description.length);
}

// Null-aware operatörler (C# ile aynı)
print(description?.length); // null ise null döner, değilse uzunluğu.
print(description ?? "Varsayılan Açıklama"); // null ise sağdaki değeri yaz.
```

> ?? : null kontrolü

> ?. : null-safe erişim


### 2.2 late Anahtar Kelimesi

Dart’ta **Null Safety** varsayılan olarak aktiftir. Bu da bir değişkenin
`null` olabilmesi için açıkça belirtilmesini zorunlu kılar.

Ancak bazı senaryolarda bir değişken:

- Null olmayacaktır
- Ancak, tanımlandığı anda değil
- Daha sonra (`constructor, init, lifecycle` vb.) atanacaktır

Bu durum için `late` anahtar kelimesi kullanılır.

---

#### C# Geliştiricileri İçin Karşılık

C#’ta şu senaryo çok yaygındır:

```csharp
class Service {
    private string token;

    public void Initialize() {
        token = "abc";
    }
}
```

Dart’ta bu yapı **Null Safety** nedeniyle doğrudan mümkün değildir.
Karşılığı `late` kullanmaktır.

---

#### Temel Kullanım

```dart
class UserService {
  late String token;

  void initialize() {
    token = "abc123";
  }

  void sendRequest() {
    print(token);
  }
}
```

- `token` **null olamaz**
- Ama tanım anında atanmaz
- `initialize()` çağrılmazsa **runtime error** oluşur

---

#### Hatalı Kullanım (Runtime Error)

```dart
class Example {
  late String value;

  void printValue() {
    print(value); // LateInitializationError
  }
}
```

📌 `late`, compile-time değil **runtime** güvenliği sağlar.

---

#### late vs Nullable (`?`)

```dart
late String name;   // Null olmayacak, sonra atanacak
String? email;     // Null olabilir
```

| Yapı | Anlam |
|----|-----|
| `String?` | Null olabilir |
| `late String` | Null olmayacak ama sonra atanılacak |

---

#### late final Kullanımı

`late`, `final` ile birlikte de kullanılabilir.

```dart
class Config {
  late final String apiKey;

  void load() {
    apiKey = "KEY123";
  }
}
```

Bu durumda:
- `apiKey` **sadece bir kez atanabilir**
- Ama bu atama constructor dışında yapılabilir

---

#### Nerelerde Kullanılır?

- Flutter `initState()`
- Dependency Injection
- Lazy initialization
- API / config değerleri

📌 `late`, yanlış kullanılırsa hatayı derleme zamanında değil,
çalışma zamanında verir. Bu nedenle bilinçli kullanılmalıdır.


#### late: Lazy mi, Değil mi?

`late`, sıkça **lazy initialization** ile karıştırılır.
Ancak `late` tek başına lazy değildir.

```dart
late String value;

void init() {
  value = expensiveCall();
}
```

Bu yapı:
- Değeri geç atar
- Ama erişimde hesaplama yapmaz.

#### Gerçek Lazy Initialization

```dart
late final String value = expensiveCall();
```

Bu durumda:
- İlk erişimde hesaplanır
- Sonraki erişimlerde tekrar hesaplanmaz

</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)



## 3. Fonksiyonlar (Functions)

Dart'ta fonksiyonlar "First-class citizen"dır (değişken gibi atanabilirler). En büyük fark Parametre yapısıdır.


### 3.1. Temel ve Arrow (Ok) Fonksiyonları


```dart
// Klasik
int add(int a, int b) {
  return a + b;
}

// Arrow Syntax (Tek satırlık return işlemleri için - C# Lambda benzeri)
int multiply(int a, int b) => a * b;
```


### 3.2. İsimlendirilmiş Parametreler (Named Parameters)

Bu özellik Flutter geliştirmede çok sık kullanılır. C# 'taki Optional Arguments'a benzer ancak daha esnektir.

Dart'ta bir fonksiyon tanımlarken parametreleri süslü parantez { } içine alınırsa, bu parametreler **Named Parameter** olur.

- **Sıra Bağımsızdır:** Çağırırken parametrelerin sırasının bir önemi yoktur.
- **İsim Zorunludur:** Değeri gönderirken parametrenin adını yazmak zorunludur.


```dart
// Süslü parantez {} içindekiler isimlendirilmiş parametredir.
// 'required' anahtar kelimesi zorunlu olduğunu belirtir.
void createUser({required String name, int? age, String role = "User"}) {
  print("User: $name, Age: $age, Role: $role");
}

void main() {
  // Çağırırken parametre sırası önemli değildir, isimleri önemlidir.
  createUser(name: "Ali", age: 25); 
  createUser(role: "Admin", name: "Ayşe");
}
```

```dart
// Tanımlama: Parametreler {} içinde
void updateSettings({bool? isNotificationOn, double? volume}) {
  print("Bildirim: $isNotificationOn, Ses: $volume");
}

void main() {
  // Kullanım: İsimlerini yazmak zorundayız
  updateSettings(volume: 0.5, isNotificationOn: true); 
  
  // Sıra fark etmez
  updateSettings(isNotificationOn: false, volume: 1.0); 

  // updateSettings(true, 0.5); // HATA! İsimsiz gönderemezsiniz.
}
```


#### 3.2.1. Üç Farklı Durum (Null Safety ile Birlikte)

Dart'ın Null Safety yapısı ile birlikte Named Parameter'lar üç farklı şekilde tanımlanabilir:


##### 3.2.1.A. Zorunlu Parametreler (required)

Parametrenin isimlendirilmiş olmasını istiyor ama değerinin mutlaka girilmesini zorunlu kılınmak istendiğinde required kullanılır. C# 'taki normal parametre davranışı gibidir ama ismiyle çağrılır.


```dart
void login({required String username, required String password}) {
  // username ve password null olamaz ve mutlaka gönderilmelidir.
}

// Kullanımı:
login(username: "admin", password: "123"); 
// login(username: "admin"); // HATA! password eksik.
```


##### 3.2.1.B. Varsayılan Değerli (Default Value)

Eğer kullanıcı bir değer göndermezse varsayılan bir değer atayabilirsiniz.


```dart
// timeOut gönderilmezse 30 olarak kabul edilir.
void connect({String host = "localhost", int timeOut = 30}) {
  print("Host: $host, Süre: $timeOut");
}

// Kullanımı:
connect(); // Host: localhost, Süre: 30
connect(host: "192.168.1.1"); // Host: 192.168.1.1, Süre: 30
```


##### 3.2.1.C. Null Olabilir (Nullable)

Eğer parametre opsiyonelse ve varsayılan bir değeri yoksa (yani gönderilmezse null olsun isteniyorsa), tipin yanına ? konur.


```dart
void search({String? query, int? page}) {
  if (query != null) {
    print("$query aranıyor...");
  } else {
    print("Arama metni girilmedi.");
  }
}
```

#### 3.2.2. Karışık Kullanım (Positional + Named)

Dart'ta fonksiyonlar hem Sıralı (Positional) hem de İsimlendirilmiş (Named) parametreleri aynı anda alabilir.

- Kural: Önce sıralı parametreler yazılır, en sona süslü parantez {} açılır.


```dart
// 'id' zorunlu ve sırasına göre girilmeli (Positional)
// 'force' ve 'reason' isimlendirilmiş (Named)
void deleteUser(int id, {bool force = false, String? reason}) {
  print("User $id siliniyor. Zorla: $force");
}

void main() {
  deleteUser(101); // Sadece ID yeterli
  deleteUser(102, force: true); // ID ve force
  deleteUser(103, reason: "Hatalı kayıt", force: true); // Karışık
}
```

<a id="csharp-gelistiricileri-icin-kritik-fark"></a>
#### 3.2.3. C# Geliştiricileri İçin Kritik Fark

C# 'ta "Optional Parameters" ve "Named Arguments" kavramları vardır ama Dart'taki yaklaşım daha katıdır.

C#:

`void Foo(int a, int b = 0)` tanımlandığında; Foo(1), Foo(1, 5) veya Foo(a: 1, b: 5) denebilir. Yani isimlendirme çağırırken yapılan bir tercihtir.

Dart:

 `void Foo(int a, int b = 0)`
- Dart: Eğer {} kullanıldıysa, çağırırken mutlaka ismi kullanmak zorunludur (b: 5). Sadece 5 yazılamaz. Eğer {} kullanılmadıysa, ismiyle çağırılamaz.


#### 3.2.4. Flutter İçin Neden Hayati?

Flutter'da UI kodlarken her şey bir sınıftır (Widget). Bir butonun rengini, üzerindeki yazıyı, tıklanınca ne olacağını belirlerken yüzlerce parametre ihtimali vardır.

Dart'ta Named Parameters olmasaydı Flutter kodu şöyle görünürdü (Okunamaz):


```dart
// KÖTÜ SENARYO (Named Parameter olmasaydı)
Button("Kaydet", Colors.Blue, true, 12.0, () => print("Tıklandı"));
// Hangi true? 12.0 neyin boyutu?
```

Named Parameters sayesinde Flutter kodu şöyle görünür (Okunaklı):


```dart
// DART/FLUTTER GERÇEĞİ
ElevatedButton(
  onPressed: () => print("Tıklandı"),
  child: Text("Kaydet"),
  style: ElevatedButton.styleFrom(
    backgroundColor: Colors.blue,
    elevation: 12.0,
  ),
)
```



### 3.3. typedef (Fonksiyon Tipi Takma Adı)

Dart’ta fonksiyonlar `first-class citizen`’dır.
Yani değişkenlere atanabilir, parametre olarak geçilebilir.

Fonksiyon tipleri karmaşıklaştığında okunabilirliği artırmak için
`typedef` kullanılır.

---

#### C# Karşılığı

```csharp
Func<int, int, int>
```

---

#### Dart’ta typedef

```dart
typedef Operation = int Function(int a, int b);
```

Bu tanım:
> “İki `int` alıp `int` dönen fonksiyon”

---

#### Kullanım

```dart
int add(int a, int b) => a + b;
int multiply(int a, int b) => a * b;

void execute(Operation op) {
  print(op(3, 4));
}

void main() {
  execute(add);       // 7
  execute(multiply);  // 12
}
```

---

#### Nerelerde Kullanılır?

- Callback yapıları
- Event handler’lar
- State management
- API response işleyicileri

📌 `typedef`, özellikle Flutter ve fonksiyonel tasarımda
kodu ciddi şekilde okunur hâle getirir.


### 3.4. Veri Tipi İçin typedef (Type Alias)

`typedef`, sadece fonksiyonlar için değil,
mevcut veri tipleri için takma ad oluşturmak amacıyla da kullanılabilir.

```dart
typedef IntList = List<int>;

void main() {
  IntList numbers = [1, 2, 3];
  print(numbers);
}
```

</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)



## 4. Sınıflar ve OOP (Classes)

Dart, tamamen nesne yönelimli bir dildir. Ancak Java/C# 'tan farklı bazı pratik sözdizimi şekerlerine (syntactic sugar) sahiptir.


### 4.1. Erişim Belirleyiciler (Access Modifiers)

Dart'ta public, private, protected anahtar kelimeleri **yoktur**.

- Varsayılan her şey Public'tir.
- Bir değişkenin veya sınıfın başına _ (alt çizgi) konursa Private (Library/Dosya bazlı özel) olur.


```dart
class BankAccount {
  double _balance = 0; // Private değişken (_ ile başlar)

  void deposit(double amount) {
    _balance += amount;
  }
  
  // Getter (C# Property benzeri)
  double get balance => _balance;
}
```

### 4.2. Constructor (Yapıcı Metotlar)

Dart, constructor (yapıcı metot) tanımlamayı C# ve Java’ya göre
çok daha kısa ve okunabilir hâle getirir.
Temel amaç, bir nesne oluşturulurken gerekli alanların
güvenli ve kontrollü şekilde atanmasıdır.

---

#### 4.2.1. Klasik Constructor

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);
}
```

Bu yapı:

- C#’taki constructor ile aynıdır
- `new` anahtar kelimesi kullanılmaz (opsiyoneldir).

---

#### 4.2.2. İsimlendirilmiş Constructor (Named Constructor)

Dart’ta constructor overload yerine
`isimlendirilmiş constructor` kullanılır.

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  Person.guest()
      : name = "Guest",
        age = 18;
}
```

Kullanım:

```dart
var p1 = Person("Mehmet", 30);
var p2 = Person.guest();
```

---

#### 4.2.3. Factory Constructor (Özel Nesne Üretimi)

Normal constructor’lar **her zaman yeni bir nesne üretir**.
`factory` constructor ise nesne üretimini kontrol etmeyi sağlar.

`factory` kullanıldığında:
- Yeni nesne üretilebilir
- Gerekirse mevcut bir nesne döndürülebilir
- Nesne farklı bir kaynaktan (JSON, cache, API) üretilebilir

Bu nedenle özellikle **JSON → Model dönüşümlerinde**
`factory constructor` standart hâle gelmiştir.

---

### 4.3. factory Neden Gereklidir?

Dart’ta runtime reflection **yoktur**.
Bu yüzden JSON verileri otomatik olarak nesneye çevrilemez.

Her model sınıfı:
> “Bu JSON verisini kendime nasıl dönüştürürüm?”
sorusunu **kendisi cevaplamak zorundadır**.

---

### 4.4. factory ile fromJson Deseni

```dart
class Product {
  final int id;
  final String name;

  const Product({
    required this.id,
    required this.name,
  });

  factory Product.fromJson(Map<String, dynamic> json) {
    return Product(
      id: json['id'],
      name: json['name'],
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'name': name,
    };
  }
}
```

Bu yapı sayesinde:
- JSON → Dart dönüşümü **tek noktada** yapılır
- Tip güvenliği (type-safety) sağlanır
- Kod tekrarı azalır
- Hatalar merkezi olarak yönetilir

---

### 4.5. Normal Constructor vs Factory Constructor

| Özellik | Normal Constructor | Factory Constructor |
|------|------------------|-------------------|
| Her çağrıda yeni nesne | Evet | Hayır (opsiyonel) |
| Kontrol edilebilir üretim | Hayır | Evet |
| JSON dönüşümü için uygun | Hayır | Evet |
| Cache / singleton desteği | Hayır | Evet |

---

### 4.6. Nesne Eşitliği (== ve hashCode)

C# geliştiricileri için:
- `Equals()`
- `GetHashCode()`
- `record` yapıları

nesne karşılaştırmasının temelidir.

Dart’ta da benzer bir kavram vardır ancak varsayılan davranış farklıdır.

---

### 4.7. Varsayılan Davranış (Referans Eşitliği)

```dart
class User {
  final int id;
  final String name;

  User(this.id, this.name);
}

void main() {
  var u1 = User(1, "Ali");
  var u2 = User(1, "Ali");

  print(u1 == u2); // false
}
```

Dart’ta `==`, override edilmezse **referans karşılaştırması** yapar.

---

#### İçeriğe Göre Karşılaştırma

Model sınıflarında genellikle **içerik eşitliği** istenir.

```dart
class User {
  final int id;
  final String name;

  User(this.id, this.name);

  @override
  bool operator ==(Object other) =>
      identical(this, other) ||
      (other is User && other.id == id && other.name == name);

  @override
  int get hashCode => Object.hash(id, name);
}
```

Artık:

```dart
print(User(1, "Ali") == User(1, "Ali")); // true
```

---

#### hashCode Neden Önemli?

`Set` ve `Map` gibi koleksiyonlar `hashCode` kullanır.

```dart
var users = <User>{
  User(1, "Ali"),
  User(1, "Ali"),
};

print(users.length); // 1
```

Eğer `hashCode` override edilmezse:
- Aynı görünen nesneler farklı kabul edilir

---

#### İpucu: Immutable Sınıflar

- `final` alanlar
- Constructor ile set
- `==` ve `hashCode` override

Bu yaklaşım, C#’taki `record` yapısına denktir.


### 4.8. Object Sınıfı ve Temel Metotlar

Dart’ta tüm sınıflar dolaylı olarak `Object` sınıfından türetilir.
Bu yapı C#’taki `object`, Java’daki `Object` sınıfına denktir.

#### Object’ten Gelen Temel Metotlar
- `toString()`
- `==`
- `hashCode`
- `runtimeType`

```dart
class User {
  final int id;
  final String name;

  User(this.id, this.name);

  @override
  String toString() => 'User(id: $id, name: $name)';
}

void main() {
  var user = User(1, "Ali");
  print(user);              // User(id: 1, name: Ali)
  print(user.runtimeType);  // User
}
```

📌 `toString()` özellikle loglama ve debug sırasında çok faydalıdır.


### 4.9. const Constructor ve Immutable Nesneler

`const` constructor, **tamamen immutable** nesneler oluşturmak için kullanılır.

```dart
class Point {
  final int x;
  final int y;

  const Point(this.x, this.y);
}

void main() {
  const p1 = Point(1, 2);
  const p2 = Point(1, 2);

  print(identical(p1, p2)); // true
}
```

Bu sayede:
- Bellek yeniden kullanılır
- Performans artar

📌 Flutter’da performans için kritik bir yapıdır.

</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)



## 5. Kalıtım ve Arayüzler (Inheritance & Interfaces)

Dart, Java ve C# 'taki gibi `extends` kullanılır. Ancak interface anahtar kelimesi yoktur. Her sınıf aynı zamanda bir interface'dir.


### 5.1 Interface (Implements)

Bir sınıfın sadece imzasını (metotlarını) almak istendiğinde `implements` kullanılır.


```dart
// Bu normal bir sınıf ama interface gibi davranabilir.
class Animal {
  void makeSound() => print("Ses");
}

// Animal'ın davranışını MİRAS alır (Kodu kullanır)
class Dog extends Animal {
  @override // ata sınıfta (türetilen, yani Animal sınıfı) mevcut fonksiyonu baskıla/üzerine yaz/ez.
  void makeSound() => print("Hav");
}

// Animal'ın yapısını ZORUNLU KILAR (Kodu kullanmaz, yeniden yazdrır)
class RobotDog implements Animal {
  @override // ata sınıftaki bu fonksiyonu baskıla ve bunu kullan
  void makeSound() => print("Bip Bop");
}
```


### 5.2 Mixins (with Anahtar Kelimesi)

Mixins, Dart'ın C# ve Java'daki katı "Tekli Kalıtım" (Single Inheritance) kuralını esneten ve kod tekrarını önleyen en güçlü silahlarından biridir.

C# ve Java'da bir sınıf sadece bir sınıftan türeyebilir (extends). Birden fazla özellik kazandırmak için Interface kullanırız, ancak Interface'ler (C# 8.0 ve Java 8 öncesinde) sadece imza taşırdı, kodun gövdesini taşımazdı. Interface içinde kod yazılabilse bile (Default Interface Methods), state (değişken) tutamazlar.

Dart Mixin'leri ise hem metot gövdesini hem de değişkenleri (state) başka sınıflara "Enjekte" etmenizi sağlar.

> Kalıtım (Inheritance) "Dikey" bir ilişkidir (Parent -> Child). Mixin ise "Yatay" bir ilişkidir. Birbiriyle alakasız sınıflara aynı yetenekleri kazandırmak için kullanılır.

C# ve Java'da çoklu kalıtım (bir sınıfın birden fazla sınıftan türemesi) yoktur. Dart'ta bunu çözmek için Mixin (with anahtar kelimesi) kullanılır.


#### 5.2.1 Temel Sözdizimi: mixin ve with

Bir sınıfı Mixin yapmak için class yerine mixin yazılır (veya constructor'ı olmayan bir sınıf kullanılır). Kullanmak için ise `with` anahtar kelimesi kullanılır.

Senaryo: Hem bir Kuş hem de bir Uçak uçabilir. Ama ikisi aynı atadan gelmez. C# 'ta bunu yapmak için kod tekrarı gerekirdi veya ayrı bir "UçuşYöneticisi" class'ı yazılırdı. Dart'ta:

```dart
// Yetenek 1
mixin Ucabilen {
  // State (Değişken) tutabilir!
  double irtifa = 0;

  void uc() {
    irtifa += 100;
    print("Uçuyor. İrtifa: $irtifa");
  }
}

// Yetenek 2
mixin Yuzebilen {
  void yuz() {
    print("Yüzüyor...");
  }
}

// Ana Sınıf
class Hayvan {
  void nefesAl() => print("Nefes alıyor");
}

// Ördek: Hem Hayvan'dır, hem uçar, hem yüzer.
// Sıralama: Önce extends, sonra with
class Ordek extends Hayvan with Ucabilen, Yuzebilen {
  // Ordek artık uc() ve yuz() metotlarına ve irtifa değişkenine sahip.
}

// Uçak: Hayvan değildir ama uçabilir.
class Ucak with Ucabilen {
  // Sadece uçma yeteneğini aldı.
}

void main() {
  var o = Ordek();
  o.nefesAl(); // Hayvan'dan geldi
  o.uc();      // Ucabilen'den geldi
  o.yuz();     // Yuzebilen'den geldi
  
  var u = Ucak();
  u.uc();      // Ucabilen'den geldi (Kod tekrarı yok!)
}
```


#### 5.2.2 C# Geliştiricileri İçin Kritik Kurallar

Mixin'leri anlamak için şu kısıtlamaları bilmek gerekir:

1. Constructor Yoktur: Mixin'lerin kurucu metodu (Constructor) olamaz.
2. extends Edilemez: Bir mixin tek başına new ile örneklenemez (instantiate edilemez).
3. Çoklu Mixin: with A, B, C diyerek birden fazla mixin eklenebilir.


#### 5.2.3 İleri Seviye: on Anahtar Kelimesi (Kısıtlama)

Bazen bir Mixin'in sadece belirli bir türdeki sınıflarda kullanılmasını istersiniz. C# 'taki where T : SomeClass (Generic Constraints) yapısına benzer.

Bunu on anahtar kelimesi ile yaparız. Bu aynı zamanda Mixin içinde super çağrısı yapılabilmesini sağlar.


```dart
class MuzikAleti {
  void akortEt() => print("Genel akort yapıldı.");
}

// Bu Mixin SADECE MuzikAleti ve türevlerinde kullanılabilir.
mixin Elektro on MuzikAleti {
  void elektrigeBagla() {
    print("Fiş takıldı.");
  }

  @override
  void akortEt() {
    // 'on MuzikAleti' dediğimiz için super'in MuzikAleti olduğunu biliyor.
    super.akortEt(); 
    print("Elektronik ince ayar yapıldı.");
  }
}

class Gitar extends MuzikAleti with Elektro {
  // Sorun yok, çünkü Gitar bir MuzikAleti'dir.
}

// class Araba with Elektro {} // HATA! Araba, MuzikAleti değildir.
```


#### 5.2.4 Diamond Problemi ve Çalışma Sırası

C++ gibi dillerde çoklu kalıtımda yaşanan "Diamond Problem" (İki atada aynı metot varsa hangisi çalışacak?) Dart'ta Lineerizasyon ile çözülür.

Kural: En son eklenen Mixin (with listesindeki en sağdaki) her zaman kazanır ve ezer (override eder).


```dart
mixin A {
  void test() => print("A");
}

mixin B {
  void test() => print("B");
}

// B en sonda olduğu için B'nin dediği olur.
class MyClass with A, B {} 

void main() {
  MyClass().test(); // Çıktı: B
}
```


#### 5.2.5. Flutter'da Nerede Göreceksiniz?

Flutter geliştirirken Mixin'ler çok sık kullanılır. En ünlü örnek Animasyon konusudur.

Flutter'da bir Widget'ın ekran yenileme hızına (60fps) senkronize olması için SingleTickerProviderStateMixin kullanılır.

`SingleTickerProviderStateMixin`

```dart
// C# benzetmesi: Form : FormBase, ITickerProvider
class _MyAnimationState extends State<MyAnimation> with SingleTickerProviderStateMixin {
  late AnimationController _controller;

  @override
  void initState() {
    super.initState();
    // 'vsync: this' diyebilmemizi sağlayan şey Mixin'dir.
    // Mixin sayesinde bu sınıf TickerProvider yeteneği kazandı.
    _controller = AnimationController(vsync: this, duration: Duration(seconds: 1));
  }
}
```


### 5.3. covariant Anahtar Kelimesi

Dart’ta override edilen metotlarda parametre tipleri normalde daraltılamaz.
`covariant`, bu kuralı bilinçli olarak gevşetmeye yarar.

```dart
class Animal {}

class Dog extends Animal {}

class Feeder {
  void feed(Animal animal) {}
}

class DogFeeder extends Feeder {
  @override
  void feed(covariant Dog animal) {
    print("Köpek besleniyor");
  }
}
```

📌 `covariant`, kalıtımda dikkatli ve sınırlı kullanılmalıdır.


### 5.4. sealed, base ve final Sınıflar (Dart 3+)

Dart 3 ile birlikte kalıtımı **kontrollü hâle getiren** anahtar kelimeler gelmiştir.

```dart
sealed class Shape {}

class Circle extends Shape {}
class Rectangle extends Shape {}
```

- `sealed`: Alt sınıflar aynı dosyada olmalıdır
- `base`: Sadece aynı paket içinde extend edilebilir
- `final`: Extend edilemez

C# karşılığı:
- `sealed class`
- `abstract` + erişim kısıtları

📌 sealed class + pattern matching birlikte kullanıldığında
exhaustive switch (tüm durumların ele alınması) garanti edilir.

</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)



## 6. Asenkron Programlama (Future & Stream)

Bu bölüm, Dart’taki asenkron programlama modelini **tek ve bütüncül** bir yapı altında açıklar.
C# geliştiricileri için temel eşleştirme:

- C# Task<T> → Dart Future<T>
- C# async / await → Dart async / await
- C# IAsyncEnumerable / Rx → Dart Stream

Dart, "Single Threaded" (Tek iş parçacıklı) bir dildir (JavaScript gibi). Ancak "Event Loop" (Olay Döngüsü) sayesinde asenkron işlemleri ana iş parçacığını (UI thread) kilitlemeden yönetir.

Java Karşılığı: `CompletableFuture<T>`

---

### 6.1. Asenkron Programlama Nedir?

Asenkron programlama; ağ çağrıları, dosya okuma, veritabanı işlemleri gibi
zaman alan işlerin ana akışı durdurmadan çalıştırılmasını sağlar.

Amaç:
- UI donmasını engellemek
- Uygulamayı tepkisel (responsive) tutmak

---

### 6.2. Future

Future, tek bir değerin veya hatanın gelecekte döneceğini taahhüt eden bir objedir. İşlem biter, sonucu verir ve kapanır.

C# 'taki async/await ile neredeyse birebir aynıdır.

#### Basit Future Örneği

```dart
Future<String> getUserName() async {
  await Future.delayed(Duration(seconds: 2));
  return "Ahmet";
}
```

#### await Kullanımı

```dart
void main() async {
  print("İstek başladı");

  // await: Sonuç gelene kadar bu satırda bekle (Thread bloklanmaz)
  String name = await getUserName();

  print("Kullanıcı: $name");
}
```

Önemli noktalar:
- `await` sadece `async` fonksiyonlarda kullanılabilir
- Thread’i kilitlemez, sadece akışı askıya alır

#### await Kullanılmazsa

```dart
void main() {
  Future<String> result = getUserName();
  print(result);
}
```

Çıktı:

```
Instance of 'Future<String>'
```

---

### 6.3. Birden Fazla Asenkron İşlem

```dart
Future<void> loadData() async {
  await fetchUser();
  await fetchOrders();
  await fetchSettings();
}
```

Paralel çalıştırma:

```dart
await Future.wait([
  fetchUser(),
  fetchOrders(),
  fetchSettings(),
]);
```

C# karşılığı: `Task.WhenAll(...)`

---

### 6.4. Asenkron Hata Yönetimi

```dart
Future<String> apiCagir() async {
  throw Exception("Sunucu hatası");
}

void main() async {
  try {
    final veri = await apiCagir();
    print(veri);
  } catch (e) {
    print("API hatası: $e");
  }
}
```

> `try / catch` bloğu `await` edilen çağrıyı sarmalıdır.

---

### 6.5. Stream

`Future` tek bir sonuç üretir.  
`Stream` ise **zaman içinde birden fazla veri** üretir.

Future tek bir pakettir; Stream ise bir su hortumu gibidir. Veri zaman içinde parça parça, sürekli akabilir. Bir Stream açıldığında, birden fazla olay (event) fırlatabilir.

Kullanım senaryoları:
- WebSocket
- Kullanıcı etkileşimleri
- Sayaç / timer
- İndirme ilerleme durumu

Stream'leri dinlemek için listen (callback mantığı) veya await for (döngü mantığı) kullanılır.

#### Stream Üreten Fonksiyon (async*)

```dart
// Saniyede bir sayı üreten fonksiyon (Generator)
// async* -> Stream döneceğini belirtir.
// yield -> Stream hattına bir veri bırakır.
Stream<int> countSeconds(int max) async* {
  for (int i = 1; i <= max; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}
```

#### await for Kullanımı

```dart
void main() async {
  print("Sayaç başlıyor...");

  await for (int number in countSeconds(3)) {
    print("Gelen sayı: $number");
  }

  print("Akış bitti.");
}
```

C# karşılığı: `await foreach`


Kendi Stream'inizi manuel yönetmek isterseniz (örneğin bir butona basınca veri akıtmak), StreamController kullanılır. Bu, C# 'taki Subject veya EventHandler yapısına benzer.

---

### 6.6. StreamController (Giriş)

Stream’i manuel olarak kontrol etmek için kullanılır.
C#’taki `Subject` veya `EventHandler` mantığına benzer.

```dart
import 'dart:async';

void main() {
  final controller = StreamController<int>();

  controller.stream.listen((data) {
    print("Gelen veri: $data");
  });

  controller.add(1);
  controller.add(2);
  controller.add(3);

  controller.close();
}
```

---

### 6.7. Future vs Stream (Özet Tablo)

| Özellik | Future | Stream |
|------|-------|--------|
| Veri sayısı | Tek | Çok |
| Süre | Kısa | Uzun / sürekli |
| Kullanım | API, DB | Event, Socket |
| await | Evet | await for |


</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)


## 7. Dart’ta Hata Yönetimi (Error Handling)

Gerçek dünya uygulamalarında hatalar **istisna değil**, normal bir durumdur.
Dosya okuma, ağ isteği (API), JSON parse veya kullanıcı girdisi gibi
işlemlerin tamamı hata üretme potansiyeline sahiptir.

Dart’ta hata yönetimi `try / catch / finally` yapıları ile gerçekleştirilir.

### 7.1. try / catch Temel Kullanım

```dart
void main() {
  try {
    int sonuc = 10 ~/ 0; // Hata üretir. (10 ~/ 0 ifadesi tamsayı bölme demektir)
    print(sonuc);
  } catch (e) {
    print("Bir hata oluştu: $e");
  }
}
```

Bu yapı sayesinde:
- Uygulama çökmez
- Hata kontrollü biçimde ele alınır
- Kullanıcıya anlamlı mesaj gösterilebilir

#### Belirli Hata Türlerini Yakalama

```dart
try {
  int sonuc = int.parse("abc");
  print(sonuc);
} on FormatException {
  print("Sayı formatı hatalı");
} catch (e) {
  print("Bilinmeyen hata: $e");
}
```

`on` anahtar kelimesi, **belirli hata tiplerini** yakalamak için kullanılır.

#### finally Bloğu

```dart
void veriGetir() {
  try {
    print("İşlem başladı");
  } catch (e) {
    print("Hata oluştu");
  } finally {
    print("Bu blok her durumda çalışır");
  }
}
```

`finally` bloğu:
- Hata olsa da olmasa da çalışır
- Kaynak kapatma (dosya, bağlantı) için idealdir

#### async / await ile Hata Yönetimi

```dart
Future<String> apiCagir() async {
  throw Exception("Sunucu hatası");
}

void main() async {
  try {
    final veri = await apiCagir();
    print(veri);
  } catch (e) {
    print("API hatası: $e");
  }
}
```

Asenkron işlemlerde try / catch mutlaka `await` edilen çağrıyı sarmalıdır.

#### Flutter Bağlamında Önemi

Flutter uygulamalarında hata yönetimi genellikle:
- API çağrıları
- Firebase işlemleri
- JSON dönüşümleri
- Form doğrulama

sırasında kullanılır.

Örneğin, bir API çağrısında hata oluştuğunda:
- `SnackBar`
- `Dialog`
- Hata ekranı

gösterilerek kullanıcı bilgilendirilir.

Bu nedenle `try / catch` yapısı, Dart ve Flutter geliştirmede
**olmazsa olmaz** bir konudur.


```dart
// Bir veriyi 2 saniye sonra getiren simülasyon
Future<String> fetchUser() async {
  await Future.delayed(Duration(seconds: 2));
  return "Ali Veli";
}

void main() async {
  print("İstek başlıyor...");
  String user = await fetchUser();
  print("Kullanıcı geldi: $user");
}
```


### 7.2. assert Anahtar Kelimesi

`assert`, **debug modda** çalışan, koşul sağlanmadığında uygulamayı durduran
bir doğrulama mekanizmasıdır. Release modda tamamen devre dışı bırakılır.

```dart
void createUser(String name) {
  assert(name.isNotEmpty, "İsim boş olamaz");
  print("Kullanıcı oluşturuldu: $name");
}
```

- Debug mod: kontrol yapılır
- Release mod: `assert` koddan çıkarılır

📌 Flutter’da widget constructor’larında çok sık kullanılır.

⚠️ Uyarı: assert içinde API çağrısı, state değişimi gibi
side-effect içeren kod yazılmamalıdır.


</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)


## 8. Koleksiyonlar ve Döngüler (Imperative Yaklaşım)

Generic yapılar Java/C# ile aynıdır.


```dart
// List (Array yerine geçer, boyutu dinamiktir)
List<String> names = ["Ali", "Veli"];
names.add("Ayşe");

// Map (Dictionary / HashMap karşılığı)
Map<String, int> scores = {
  "Ali": 90,
  "Veli": 80
};

// Spread Operator (...) - Bir listeyi diğerinin içine yayar
var moreNames = ["Zeynep", ...names];
```

`for, while, do-while` aynıdır. `foreach` yapısı biraz farklıdır.


```dart
// Standart for
for (var name in names) {
  print(name);
}

// Fonksiyonel yaklaşım (Lambda)
names.forEach((name) => print(name));
```

</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)


## 9. Koleksiyonlar ve Fonksiyonel Metotlar (LINQ Karşılıkları)

Dart'ta veri manipülasyonu Iterable sınıfı üzerinden yapılır. Listeler ve Setler birer Iterable'dır.


### 9.1. Karşılaştırma Tablosu (C# - Java - Dart)

Aşağıdaki tablo, en sık kullanılan işlemlerin diller arasındaki karşılığını gösterir.


| İşlem | C# (LINQ) | Java (Stream) | Dart (Iterable – kullanım) |
|------|-----------|---------------|------------------------------------|
| Filtreleme | `Where()` | `filter()` | `list.where((x) => x > 5)` |
| Dönüştürme | `Select()` | `map()` | `list.map((x) => x * 2)` |
| İlk eleman | `First()` | `findFirst()` | `list.first` |
| Koşul var mı | `Any()` | `anyMatch()` | `list.any((x) => x > 10)` |
| Tümü sağlıyor mu | `All()` | `allMatch()` | `list.every((x) => x > 0)` |
| Sayma | `Count()` | `count()` | `list.length` |
| Sıralama | `OrderBy()` | `sorted()` | `list.toList()..sort()` |
| Toplama / indirgeme | `Aggregate()` | `reduce()` | `list.reduce((a, b) => a + b)` |
| Alt küme alma | `Take()` | `limit()` | `list.take(3).toList()` |
| Atlama | `Skip()` | `skip()` | `list.skip(2).toList()` |


### 9.2. Detaylı Örnekler ve Kritik Farklar

Aşağıdaki örnekler için basit bir Product sınıfımız olduğunu varsayalım.


```dart
class Product {
  final String name;
  final double price;
  final bool inStock;

  Product(this.name, this.price, this.inStock);
}

final List<Product> products = [
  Product("Laptop", 25000, true),
  Product("Mouse", 500, true),
  Product("Klavye", 1200, false),
  Product("Monitör", 4500, true),
];
```


#### 9.2.A. Filtreleme (Where) ve Zincirleme (Chaining)

C# ve Java'daki gibi metotları art arda ekleyebilirsiniz (Fluent Interface).

Önemli Fark: Dart'ta `where` veya `map` kullandığınızda sonuç bir List değildir, bir Iterable'dır (Lazy evaluation). Sonucu tekrar List olarak kullanmak isteniyorsa mutlaka .toList() demelisiniz.


```dart
// Stokta olan ve fiyatı 1000'den büyük ürünlerin isimlerini getir.
List<String> expensiveInStockNames = products
    .where((p) => p.inStock)          // Filtre 1 (Stokta mı?)
    .where((p) => p.price > 1000)     // Filtre 2 (Pahalı mı?)
    .map((p) => p.name)               // Projeksiyon (Sadece ismini al)
    .toList();                        // <--- Iterable'ı List'e çevirir.

print(expensiveInStockNames); // [Laptop, Monitör]
```


#### 9.2.B. Tek Eleman Bulma (FirstOrDefault Sorunsalı)

C# geliştiricilerinin en çok takıldığı nokta burasıdır.

- Dart'taki .firstWhere metodu eleman bulamazsa Exception fırlatır.
- Null dönmesi veya varsayılan değer dönmesi için orElse parametresi kullanılmalıdır.


```dart
// C#: products.FirstOrDefault(p => p.Name == "Tablet");
// Dart:

// Yöntem 1: Bulamazsa varsayılan nesne döndür (orElse)
Product found = products.firstWhere(
  (p) => p.name == "Tablet",
  orElse: () => Product("Bulunamadı", 0, false),
);

// Yöntem 2: Nullable yapı (Dart Collection paketleri ile veya manuel)
// Standart Dart'ta try-catch kullanmak veya cast yapmak gerekebilir.
// Ancak 'collection' paketi ile '.firstWhereOrNull' uzantısı gelir (C# ile birebir aynı olur).
```


#### 9.2.C. Fold (Aggregate) Mantığı

Bir listeyi tek bir değere indirgemek (örneğin toplam fiyatı bulmak) için **reduce** veya **fold** kullanılır. **reduce** listenin kendi tipini döndürür, **fold** ise başlangıç değeri alır ve tipi değiştirebilir.


```dart
// C#: products.Sum(p => p.price);
// Dart (Fold ile):

// 0: Başlangıç değeri (Initial Value)
// total: Birikimli toplam
// current: O anki ürün
double totalPrice = products.fold(0, (total, current) => total + current.price);

print("Toplam Sepet Tutarı: $totalPrice");
```


### 9.3. Koleksiyonlar İçinde "For" ve "If" (Collection For & If)

Dart'ın C# ve Java'da olmayan çok güçlü bir sözdizimi özelliği vardır. Bir Listeyi veya Map'i oluştururken, listenin tanımı içinde if ve for kullanabilirsiniz.

Bu özellikle Flutter UI kodlarken hayat kurtarır.


```dart
bool isAdmin = true;
List<int> cartIds = [101, 102];

List<String> menuItems = [
  "Ana Sayfa",
  "Ürünler",
  
  // COLLECTION IF
  // Eğer isAdmin true ise bu elemanı listeye ekle, yoksa hiç ekleme.
  if (isAdmin) "Admin Paneli", 
  
  // COLLECTION FOR
  // Başka bir listedeki elemanları dönüştürerek buraya göm.
  for (var id in cartIds) "Sepet Ürünü #$id",
];

print(menuItems);
// Çıktı: [Ana Sayfa, Ürünler, Admin Paneli, Sepet Ürünü #101, Sepet Ürünü #102]
```

C# 'ta bunu yapmak için List.AddRange() veya karmaşık if/else blokları gerekirdi. Dart'ta bu declarative (bildirimsel) bir yapıdadır.


### 9.4. Spread Operator (...)

JavaScript/ES6'dan tanıdık gelebilir. Bir listenin elemanlarını başka bir listenin içine "yaymak" için kullanılır.


```dart
var listA = [1, 2];
var listB = [3, 4];

// C#: var combined = new List<int>(listA); combined.AddRange(listB);
var combined = [...listA, ...listB]; // [1, 2, 3, 4]

// Null-aware Spread (...?)
List<int>? listC; // Null olabilir
var combined2 = [...listA, ...?listC]; // Hata vermez, null ise atlar.
```

| Amaç / Durum                         | Kullanılan Yapı / Metot                |
|-------------------------------------|----------------------------------------|
| Veri dönüştürülüyorsa              | `.map()`                               |
| Veri eleniyorsa                    | `.where()`                             |
| Listeye çevriliyorsa              | `.toList()`                            |
| Tek değer aranıyorsa               | `.firstWhere(..., orElse: ...)`        |
| Liste oluştururken koşul gerekiyorsa| `Collection If`                        |


### 9.5. Iterable için Extension Metotlar

Extension’lar, koleksiyonları domain’e özgü biçimde genişletmek için idealdir.

```dart
extension IntIterableExtensions on Iterable<int> {
  int sum() => reduce((a, b) => a + b);
}

void main() {
  print([1, 2, 3, 4].sum()); // 10
}
```

Bu yaklaşım:
- C# LINQ extension metodlarına denktir
- Utility sınıfları gereksiz kılar


</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)


## 10. Dart Paket Yönetimi: Pub & pubspec.yaml

C# geliştiricileri NuGet (.csproj / packages.config), Java geliştiricileri ise Maven (pom.xml) veya Gradle (build.gradle) kullanmaya alışıktır.

Dart dünyasında bu işi Pub (paket yöneticisi) ve pubspec.yaml dosyası yapar.

Dart ekosistemindeki kütüphanelere "Package" (Paket) denir ve bunların barındırıldığı merkezi depo pub.dev adresidir.


### 10.1. pubspec.yaml Dosyası (Projenin Kalbi)

Bu dosya projenin kimliğidir. C# 'taki .csproj veya Java'daki pom.xml dosyasının karşılığıdır. Ancak YAML formatındadır.

⚠️ Önemli Uyarı: **YAML formatı boşluklara (indentation) çok duyarlıdır**. XML veya C# gibi değildir. Tab yerine 2 boşluk kullanmak standarttır. Yanlış hizalama hata verir.

Basit bir `pubspec.yaml` örneği:


```yaml
name: my_app
description: Yeni Dart projem.
version: 1.0.0
publish_to: 'none' # Bu paketi pub.dev'de yayınlamayacağımızı belirtir.

# SDK Sürüm Kısıtlaması
environment:
  sdk: '>=3.0.0 <4.0.0'

# 1. DEPENDENCIES (Projenin çalışması için gerekenler)
# C# -> References / NuGet Packages
dependencies:
  flutter:
    sdk: flutter
  
  # HTTP istekleri için paket
  http: ^1.1.0 
  
  # Google Fontları
  google_fonts: ^5.1.0

# 2. DEV DEPENDENCIES (Sadece geliştirme anında gerekenler)
# Test kütüphaneleri, kod üreticiler (Code Generators) vb.
dev_dependencies:
  flutter_test:
    sdk: flutter
  
  # Linter (Kod stili denetleyicisi)
  flutter_lints: ^2.0.0
```


## 10.2. Versiyonlama ve Caret (^) Sembolü

C# veya Java'da versiyonları genelde sabitleriz veya 1.0.* gibi wildcard kullanırız. Dart, semantik versiyonlama (semantic versioning) kullanır ve ^ (caret) işareti varsayılandır.

`http: ^1.1.0` şu anlama gelir:

- En az **1.1.0** sürümünü yükle
- **2.0.0** sürümüne kadar (2.0.0 hariç) güncellemeye izin ver

İzin verilen sürüm aralığı:

>= 1.1.0  
< 2.0.0  

`^` (caret) işareti, **major sürüm değişmediği sürece** geriye uyumlu
en güncel sürümün kullanılacağını ifade eder.


Dart, 2.0.0'ın "Breaking Change" (Kıran Değişiklik) içerdiğini varsayar. ^ işareti, "Geriye dönük uyumlu en güncel versiyonu al" demenin güvenli yoludur.


### 10.3. pubspec.lock (Gerçek Kayıt)

Siz pubspec.yaml dosyasına http: ^1.1.0 yazıp paketleri indirdiğinizde, Dart o anki en güncel uyumlu sürümü (örneğin 1.1.3) indirir.

Dart, tam olarak hangi sürümü indirdiğini pubspec.lock dosyasına yazar.

- Java/C# Benzerliği: Node.js'teki package-lock.json ile aynıdır. Bazı modern NuGet akışlarında da benzer kilit dosyaları vardır.
- Kural: Bu dosyayı Git'e commit etmelisiniz. Böylece takım arkadaşınız projeyi çektiğinde sizinle birebir aynı versiyonlarla çalışır.

Terminalde veya IDE terminalinde kullanacağınız temel komutlar:

Dart / Flutter:   `dart pub add [paket]`

Java (Maven): `mvn versions:display`

(Not: Eğer Flutter projesi yapılıyorsa komutların başına dart yerine flutter gelir: flutter pub get)

C# için nuget.org neyse, Dart için pub.dev odur.
Siteye girdiğinizde paketlerin yanında üç adet puan görürsünüz:

1. Likes: Geliştiricilerin beğenisi.
2. Pub Points: Kod kalitesi, dökümantasyon ve platform desteğine göre verilen otomatik puan (Max 140).
3. Popularity: Son 60 gündeki indirilme oranı.

İpucu: Paket seçerken "Pub Points" ve "Publisher" (Örn: publisher: dart.dev veya google.dev) güvenilirlik açısından önemlidir.


### Özet: C#/Java Geliştiricisi İçin Kontrol Listesi

1. Proje ayarların pubspec.yaml dosyasındadır.
2. Boşluklara (indentation) dikkat et, tab kullanma.
3. Uygulamanın çalışması için gerekenleri dependencies altına ekle.
4. Sadece kod yazarken/test ederken gerekenleri dev_dependencies altına ekle.
5. pubspec.lock dosyasını silme ve Git'e gönder.
6. VS Code kullanıyorsan, pubspec.yaml dosyasını her kaydettiğinde (Ctrl+S), arka planda otomatik pub get çalışır.


</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)


## 11. Dart/Flutter Proje Mimarisi ve Klasör Yapısı

C# ve Java'da proje yapısı genelde klasör isimlerine göre otomatik oluşan Namespace'ler (örn: MyApp.Services.Auth) üzerine kuruludur. Dart'ta ise Namespace kavramı yoktur. Bunun yerine dosya yolları (import paths) ve kütüphane (library) mantığı vardır.


### 11.1. Kök Dizin (Root Directory)

Bir Dart/Flutter projesi oluşturduğunuzda standart bir yapı gelir. C# 'taki Solution (.sln) klasörüne benzer.

- `lib/` : En önemli klasör. C# 'taki projenizin içindeki .cs dosyaları veya Java'daki src/main/java burasıdır. Tüm Dart kodlarınız burada durur.
- `test/` : Unit ve Widget testleri. (Java src/test/java).
- `android/ & ios/` : Platforma özel (Native) kodlar. (Sadece Flutter'da). C# geliştiricileri bunu Xamarin'den hatırlayacaktır.
- `pubspec.yaml` : Proje konfigürasyonu (NuGet / Maven).
- `analysis_options.yaml` : Linter kuralları. C# 'taki .editorconfig dosyasına benzer.


### 11.2. "Lib" Klasörünün İçi: Mimari Yaklaşımlar

Java ve C# 'ta genelde Layer-First (Katman Öncelikli) yapıya alışığızdır:

- Controllers/
- Models/
- Services/

Ancak Dart ve Flutter dünyasında, özellikle orta ve büyük ölçekli projelerde Feature-First (Özellik Öncelikli) yapı veya Clean Architecture standardı kabul görür.


#### Önerilen Yapı: Feature-First + Clean Architecture

Bu yapıda proje teknik katmanlara göre değil, uygulamanın özelliklerine (Login, Profile, Dashboard) göre bölünür.

Örnek bir lib/ ağacı:


```
lib/
├── main.dart                 # Giriş Noktası (Program.cs / Main.java)
├── core/                     # Tüm projede ortak kullanılanlar (Shared)
│   ├── constants/            # Sabitler (Renkler, API URL'leri)
│   ├── utils/                # Yardımcı fonksiyonlar (DateFormatter vb.)
│   ├── widgets/              # Ortak UI bileşenleri (CustomButton vb.)
│   └── network/              # HTTP istemcisi, API yönetimi
│
└── features/                 # Uygulamanın modülleri
    ├── auth/                 # Örnek: Kimlik Doğrulama Modülü
    │   ├── data/             # Veri Katmanı (Repository, DTO)
    │   │   ├── models/       # API'den gelen JSON modelleri
    │   │   └── repositories/ # Veri çekme iş mantığı
    │   ├── domain/           # İş Kuralları (Entity, Usecase) - Opsiyonel
    │   └── presentation/     # UI Katmanı (MVVM'in View ve ViewModel'i)
    │       ├── pages/        # Ekranlar (LoginPage.dart)
    │       ├── widgets/      # Bu ekrana özel parçalar
    │       └── state/        # State Management (Bloc, Provider vb.)
    │
    └── home/                 # Örnek: Ana Sayfa Modülü
        ├── data/
        └── presentation/
```


### 11.3. "Barrel File" Deseni

C# geliştiricileri using MyApp.Models; dediğinde o klasördeki her şeye erişir. Dart'ta ise her dosyayı tek tek import etmek gerekir:
import 'models/user.dart';
import 'models/product.dart';

`import 'models/user.dart';`

`import 'models/product.dart';`

Bunu C# namespace rahatlığına kavuşturmak için Barrel File (Fıçı Dosyası) deseni kullanılır.

Nasıl Yapılır?
Bir klasörün içine index.dart (veya klasör adıyla models.dart) adında bir dosya oluşturulur ve içindekiler dışarı aktarılır (export).

Örnek:
lib/features/auth/data/models/index.dart dosyası:

`lib/features/auth/data/models/index.dart`

```dart
export 'user_model.dart';
export 'token_model.dart';
export 'error_model.dart';
```

Kullanımı:
Artık başka bir yerde kullanırken 3 satır import yazmak yerine tek satır yazılır:


```dart
// Tek satırda tüm modellere erişim (C# Namespace gibi)
import 'package:my_app/features/auth/data/models/index.dart';
```


### 11.4. Import Yöntemleri: Relative vs Absolute

Dart'ta iki tür import vardır. Bir projede sadece biri standart olarak seçilebilir (Genelde Absolute önerilir).

1. Relative Import (Göreceli - Dosya konumuna göre)
Kendi klasörünün yanındakileri çağırırken kullanışlıdır ama dosya yeri değişirse hata verir.


```dart
import '../../core/utils/date_helper.dart'; // Okuması zordur
```

2. Absolute Import (Mutlak - Paket adına göre)
C# using mantığına daha yakındır. Dosya nereye taşınırsa taşınsın yol değişmez.


```dart
import 'package:my_app/core/utils/date_helper.dart'; // ÖNERİLEN
```

### 11.5. Private Dosyalar ve Kapsülleme

Daha önce _ (alt çizgi) ile başlayan değişkenlerin private olduğunu anlatılmıştı. Bu kural Dosya ve Klasör yapısında da geçerlidir, ancak biraz farklı çalışır.

Dart'ta `Library Private` kavramı vardır.

- Eğer bir class'ı _MyClass olarak tanımlanırsa, o class sadece o dosya içinde görünürdür.
- Ancak part ve part of anahtar kelimeleriyle büyük bir dosyayı parçalara ayırıp private elemanları paylaşılabilir (C# 'taki partial class mantığına benzer).


### Özet: Temiz Kod İçin İpuçları

1. main.dart'ı temiz tut: İçinde sadece uygulamanın başlatıcı kodları (Theme, Route vb.) olsun. İş mantığı yazma.
2. Klasörlerden korkma: features klasörü altında her özellik için ayrı klasör aç. Login, Register, Profile, Settings...
3. UI ve Logic'i ayır: Bir butonun onPressed olayının içine 50 satır kod yazma. O kodu state veya controller katmanına taşı.
4. Barrel File kullan: Import cehenneminden (Import Hell) kurtulmak için export kullan.


</br>

[⬆️ Başa dön](#top) · [📑 İçindekiler](#toc)


## 12. Örnek Proje: Kullanıcı Yönetim Simülasyonu

Kodu bir .dart dosyası olarak kaydedip çalıştırın veya DartPad.dev üzerinde doğrudan deneyin.


```dart
import 'dart:async'; // Future yapısı için (Genelde otomatik gelir ama açıkça ekledik)

// 1. MODEL SINIFI
class User {
  // 'final': Bu alanlar constructor'da set edildikten sonra değiştirilemez (Immutability).
  final int id;
  final String name;
  final String? email; // '?' -> Email null olabilir (Opsiyonel).

  // Private değişken (_ ile başlar). Sadece bu dosya içinden erişilebilir.
  List<String> _orders = [];

  // CONSTRUCTOR
  // {} süslü parantezler "Named Parameters" içindir.
  // 'required': Çağırırken mutlaka verilmelidir.
  User({
    required this.id, 
    required this.name, 
    this.email // required değil, demek ki opsiyonel.
  });

  // Getter (C# Property: public List<String> Orders => _orders;)
  List<String> get orders => _orders;

  // Metot
  void addOrder(String orderItem) {
    _orders.add(orderItem);
    print("'$orderItem' sipariş listesine eklendi.");
  }

  // Override (Java/C# ile aynı, @override annotasyonu opsiyonel ama önerilir)
  @override
  String toString() {
    // String Interpolation: $variable veya ${expression}
    return "Kullanıcı: $name (ID: $id) - Email: ${email ?? 'Belirtilmemiş'}";
  }
}

// 2. SERVİS SINIFI (Mock Database)
class UserRepository {
  
  // Asenkron Metot: C# 'taki 'async Task<User>' karşılığıdır.
  Future<User> fetchUserById(int id) async {
    print("⏳ Veritabanına bağlanılıyor...");
    
    // Ağ gecikmesi simülasyonu (2 saniye bekle)
    await Future.delayed(Duration(seconds: 2));

    if (id < 0) {
      // Hata fırlatma
      throw Exception("Geçersiz ID!"); 
    }

    print("✅ Kullanıcı bulundu!");
    
    // Mock data dönüşü
    return User(
      id: id, 
      name: "Ahmet Yılmaz", 
      email: "ahmet@ornek.com"
    );
  }
}

// 3. MAIN (Giriş Noktası)
void main() async {
  var repo = UserRepository();

  try {
    print("--- İşlem Başlıyor ---");

    // 'await' kullanmazsak Future nesnesi döner, sonuç dönmez.
    // Bekleme burada yapılır.
    User user = await repo.fetchUserById(101);

    // toString() metodunu otomatik çağırır.
    print(user); 

    // Null Safety Kontrolü
    if (user.email != null) {
      print("Email adresine doğrulama kodu gönderiliyor...");
    }

    // Listeye eleman ekleme
    user.addOrder("Laptop");
    user.addOrder("Kablosuz Mouse");

    print("Toplam Sipariş: ${user.orders.length}");

  } catch (e) {
    // Hata yakalama (C# ile birebir aynı)
    print("Bir hata oluştu: $e");
  } finally {
    print("--- İşlem Tamamlandı ---");
  }
}

***  KOD ÇIKTISI ***
--- İşlem Başlıyor ---
⏳ Veritabanına bağlanılıyor...
✅ Kullanıcı bulundu!
Kullanıcı: Ahmet Yılmaz (ID: 101) - Email: ahmet@ornek.com
Email adresine doğrulama kodu gönderiliyor...
'Laptop' sipariş listesine eklendi.
'Kablosuz Mouse' sipariş listesine eklendi.
Toplam Sipariş: 2
--- İşlem Tamamlandı ---
```


### C# Geliştiricisi Gözüyle Kod Analizi

1. User({required this.id...}): C# 'ta constructor içinde this.id = id; yazmaktan kurtulunur. Dart bunu otomatik eşler.

2. required anahtar kelimesi, C# 11 ile gelen required members özelliğine benzer. Bu parametreyi vermeden nesne oluşturulamaz.

3. String? email: Derleyiciye, bu değişkenin null olabileceği söylenir. Eğer String email yazılsaydı (soru işareti olmadan), null değer atamaya çalışıldığında kod daha derlenirken hata verirdi.

4. Future<User> ve await: C# 'taki Task<User> yapısının aynısıdır. Dart, JavaScript'in Event Loop mantığıyla çalıştığı için (Single Thread), asenkron işlemler UI (arayüz) donmalarını engellemek için hayati önem taşır. async / await kullanımı Dart’ta thread yönetimi anlamına gelmez.
Bu yapı yalnızca zamanlama (non-blocking execution) sağlar.
Gerçek paralellik için Isolate kullanılır.

5. _orders (Private): Dart'ta private anahtar kelimesi yoktur. Değişken adının önüne _ konduğunda o değişken private olur. Bu, kodu daha temiz (less verbose) hale getirir.
