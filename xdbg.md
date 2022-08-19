# Kısa Notlar

------------------------------

&nbsp;

## **xdbg küçük menüler**

### **CPU:** Assembly kodu sıralar.

&nbsp;

### **GRAPH:** Fonksiyonun başka bir fonksiyon tarafından çağırıldığını görsel olarak gösterir.

&nbsp;

### **BREAKPOINT:** Program içerisinde belirli kesme noktaları koyarak programı analiz etmeyi sağlar.

&nbsp;

### **Memory Map:** Bellekte hangi dataların depolandığı ve bu dataların adreslerini gösterir. Ayrıca Memory map içerisinde olan protection sütününda o bellekteki alanın yazdırılabilir, çalıştırılabilir veya okunabilir (Kısaltılışları: E, R, W) izinlerini gösterir. 

&nbsp;

### **Call Stack:** Genellikle breakpoint kullanıldığı zaman çok kullanışlıdır. Örnek olarak programda CreateDirectoryW üzerinde bir breakpoint konulduğunu düşünün. Bu sayede malware, güvenliği ihlal ederek dizin oluşturmaya başladığında bu breakpoint sayesinde xdbg64 tam bu işlevde duracaktır. Call Stack kullanarak malware'in hangi kod ile yazıldığı görülebilir ve dizinin nerede oluşturulduğu görülebilir.

&nbsp;

&nbsp;

## **xdbg ana pencere**

&nbsp;

<div align="center">

<a href="https://ibb.co/f0KLxhX"><img src="https://i.ibb.co/zfLD4ym/xdbg-photo2.png" alt="xdbg-photo2" border="0"></a>

<div>

&nbsp;

### x64dbg ana pencere, seçilen sekmenin (bu sekme CPU'dur). CPU sekmesinde assembly kodların yer aldığını hatırlatayım.

&nbsp;

### İlk sütuna bakıldığında RIP görülebilir. Bu Instruction Pointer'dır. Bu ise bir sonraki çalıştırılacak kod parçasını işaret eder.

&nbsp;

### İkinci sütun, binary dosya içindeki adresler içerir. Yukarıdaki örneğe ele alırsak, RIP, '000000007FF77F9416F0' adresini işaret ettiği görülebilir.

&nbsp;

### Üçüncü sütun, 4. sütunun hexadecimal gösterimidir.

&nbsp;

### Dördüncü sütun ise assembly kodların bulunduğu yerdir. Yine yukarıdaki örneğe bakacak olursak, çalıştırılacak olan 'je debug.7FF77F9416F8' kodun RIP olduğunu gösterir.

&nbsp;

### Beşinci sütun, x64dbg tarafından doldurulan veriler veya kullanıcı tarafından yazılan notları içerir. Aşağıdaki örnekte x64dbg tarafından yazılmış bir veri gösterilmiştir:

&nbsp;

<div align="center">
<a href="https://imgbb.com/"><img src="https://i.ibb.co/k4VKwKW/xdbg-photo-3.png" alt="xdbg-photo-3" border="0"></a>

<div>

&nbsp;

### Yukarıdaki örnekte, ok ile gösterilen yerde 00007FF77F949000 adresin içerisinde "Hello World!\n" içerdiğini gösterir. 



&nbsp;

&nbsp;

## **Bazı genel Instruction'lar**

&nbsp;

* **PUSH:** Stack içerisine değer gönderir.
* **POP:** Stack içerisinden değeri çıkarır.
* **CALL:** Fonksiyon çağırır.
* **RET:** Çağırılan fonksiyon işlevini tamamladıktan sonra değerini döndürür.
* **JMP:** Adresin konumuna atlar
* **CMP:** İki değeri karşılaştırır.
* **MOV:** Veriyi bir konumdan diğer konuma taşır.
* **ADD:** 1 değer arttırır.
* **SUB:** 1 değer çıkartır.

&nbsp;

&nbsp;

## **Register ile ilişkili x64dbg Penceresi**

&nbsp;

<div align="center"><div>

<a href="https://imgbb.com/"><img src="https://i.ibb.co/pJMtqmR/xdbg-photo4.png" alt="xdbg-photo4" border="0"></a>

<div>
&nbsp;

### Bir sonraki pencere, registerlar ile ilgili bilgiler içerir. Registerlar, daha sonra kullanılmak maksadıyla, kolayca referans alınabilecek verileri depolamak için program tarafından kullanılır. Bazıların ise belirli kullanımı vardır. 

&nbsp;

* **RAX:** 4 işlem için ve dönüş değerleri için kullanılır.
* **RBX:** Çeşitli işlemler için kullanılan genel register.
* **RCX:** Sayaç olarak kullanılır.
* **RDX:** Çeşitli işlemler için kullanılan genel register.
* **RBP:** Argümanlara veya yerel değişkenlere referans için kullanılır.
* **RSP:** Stack içerisindeki son argümanı işaret eder.
* **RSI/RDI:** Bellek aktarımlarda kullanılır.

&nbsp;

### RIP ise bir register değildir. Sadece mevcut Instruction'a işaret eden Instruction Pointer'dır.

&nbsp;

&nbsp;

## **Stack Belleğiyle ilgili x64dbg Penceresi**

&nbsp;

<div align="center">

<a href="https://imgbb.com/"><img src="https://i.ibb.co/qJvB57C/xdbg-photo5.png" alt="xdbg-photo5" border="0"></a>

<div>

&nbsp;

### Üçüncü pencere, stack içerisine aktarılan parametreleri içerir. 

&nbsp;

&nbsp;

## **Stack ve Veri İçeren x64dbg Penceresi**

&nbsp;

<div align="center">

<a href="https://imgbb.com/"><img src="https://i.ibb.co/LCrs0V2/xdbg-photo6.png" alt="xdbg-photo6" border="0"></a>

<div>
&nbsp;

### Dördüncü pencere, stack içerisine aktarılan stack'i, verileri ve bunların bellek adreslerini gösterir.

&nbsp;

&nbsp;

## **Döküm Verileri İçeren x64dbg Penceresi**

&nbsp;

<div align="center">
<a href="https://imgbb.com/"><img src="https://i.ibb.co/tD2P2ch/xdbg-photo7.png" alt="xdbg-photo7" border="0"></a>

<div>

&nbsp;

### Altıncı ve son pencere ise döküm verileri içerir. 'Döküm' pencereleri, kullanıcının bir kayıt defterinde hangi verilerin saklandığını veya hangi verilerin belirli adreste bulunduğunu göstermesini sağlar.