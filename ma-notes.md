# Malware Analiz Notlarım

***************************

&nbsp;


## **Malware**

### Malware, **Malicious Sosftware"** kelimesinin kısaltışılıdır. Bir malware, kullanıcının haberi olmadan dosyalarına zarar vermek veya sisteme zarar vermek için tasarlanır. Bir Malware'in çok çalışma ve malware geliştiren kişinin başlıca birçok hedefi olabilir. Mesela parola çalmak, sistemi ele geçirmek veya dataları silmek gibi.


&nbsp;

&nbsp;

## **Popüler Malware Türleri**


### 1 - Virüsler: Programa veya uygulamaya eklenen kod parçalarıdır.

&nbsp;

### 2 - Truva Atları: Bu Malware ise normal uygulamaları taklit eder. Sıradan bir program gibi görünüp kurbanların indirmesi hedeflenir. Bu sayede malware sisteme bulaşır.  


&nbsp;

### 3 - Solucanlar: Bu Malware ise sistemin kusurlarından yararlanır. Bu sayede kendi aralarında çoğalarak diğer cihazlara yayılabilir. İşte burada sistem bilgisi ciddi anlamda artıyor. 
&nbsp;

### 4 - Botnetler: Kısaca internette gezinirler. Çeşitli cihazlar içerisinde güvenlik açıkları arayan bir Malware çeşididir.

&nbsp;

### 5 - Fidye Yazılımları: Eğer saldırgan yazılımı aktif hale getirirse tüm datalar şifrelenir ve istenmeyen bir  arayüze atar ve kilitlenir. Saldırganın hedeflediği ise eğer belirli bir fidye verilirse bu yazılımı siler ve dataların şifreleri kaldırarak kuruma veya kişiye verir. Aksi takdirde datalar ulaşılamaz hale gelir.

&nbsp;

### 6 - Casus Yazılımlar: Kullanıcının sistem içerisinde neler yaptığını izlemesine ve kaydetmesine olanak sağlayan bir malware türüdür. 

&nbsp;

### 7 - Rootkit'ler: Bu Malware ise kurbanın sistemine uzaktan bağlanmasına olanak sağlar.

&nbsp;

### 8 - Backdoor: Saldırganın sisteme tekrar tekrar erişmesi için bırakılan Backdoor'lardır. Genellikle bu malware crack dosyalarına yerleştirilir. 

&nbsp;

### 9 - Adware: Sistem içerisinde görüntülenmek ve arama geçmişini gibi amaçları olan bir malware türüdür.

&nbsp;

&nbsp;

## **Malware Analizi**

### Kısaca Malware Analizi, program içerisinde veya sistem içerisinde malware incelenmesine denir. Malware Analiz olmazsa incelenen virüsün ne gibi bir önlem alınacağı bilinmez. 

&nbsp;

### Malware Analizinde virüsün yaptığı işlemler, disk içerisinde bıraktığı dosyalar ve virüsün network trafiği incelenir. Bu sebeple **sistemin çalışma mantığı, network ve kriptoloji** bilgisi olması şart. 

&nbsp; 

&nbsp;

## **Analiz Adımları**

### **1 - Basic Statik Analizi:** Bu analizde program içerisindeki Assembly kodlarına bakılmadan önce yapılan analizdir. Virüstotal gibi yerlerde kontrol yapılır genellikle ve Malware Analizin ilk aşamasıdır. İleri Seviye Statik Analizi de yapılabilir. Ancak daha çok disassembler programları ile yapılmaktadır. Ancak Reverse'e hakim olmak gerekir.

&nbsp;

### **2 - Basic Dinamik Analiz:** Bu analizde ise zararlı yazılım çalıştırılır. Malware'in davranışları, network trafikleri, register'lara eklediği değerler, oluşturulan dosyalar ve nerelere dosya yazıyor bunlar gözlenmek için Malware aktif hale getirilir.

&nbsp;

&nbsp;

## **Portable Executable File Format (PE Dosya Yapısı)**

### Portable Executable file format, Windows'un çalıştırabilir dosya yapısıdır. Örnek gerekirse **dll, exe** gibi dosyalara örnek verilebilir. 

&nbsp;

### Windows, dosyaları sorunsuz çalıştırması için **öncelikli dosyalar**, **yürütülebilir dosyalarına** ve **program dosyalarına** ihtiyaç duyar. Yürütülebilir dosyalar **.exe** dosyalarıdır. 

&nbsp;

## DLL

### Dll, Windows İşletim Sistemine ait programlar için kütüphanedir. Programlar gerektiğinde bu kütüphaneyi kullanarak işlemleri sorunsuz şekilde tamamlarlar. Eğer program içerisinde dll dosyası yoksa ve bu program çalıştırıldığı zaman bir takım hatalar meydana gelir. Kısaca programlar dll kütüphanesi sayesinde işlemlerini yerine getirir. 