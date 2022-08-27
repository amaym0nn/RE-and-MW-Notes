<div align="center">


# RedXen's C File CrackMe Çözümü

&nbsp;

Merhabalar RedXen's C file CrackMe çözümünü anlatacağım. Ctf linkine aşağıdan ulaşabilirsiniz:


<b> https://crackmes.one/crackme/62de952533c5d44a934e997b </b>

&nbsp;

Çözüm için sadece 2 yöntem göstereceğim. Çözümlere başlamadan önce zip dosya içeriğine bir göz atalım:

<img src="https://i.ibb.co/DG8tqJV/Screenshot-from-2022-08-27-23-19-19.png" alt="Screenshot-from-2022-08-27-23-19-19" border="0">
<b> Photo 1: Dosya içeriği </b>

&nbsp;

Göründüğü gibi dosya içerisinde <b> password.bin </b> ve <b> C File CrackMe </b> dosyaları yer alıyor. bin dosyasını gördüğünüz anda çözümün zaten basit olduğunu anlayabilirsiniz. 

Öncelikle exe dosyasını bir çalıştıralım ve programın çalışma mantığına bir göz atalım:

&nbsp;

<img src="https://i.ibb.co/1RL9Mnt/Screenshot-from-2022-08-27-23-27-28.png" alt="Screenshot-from-2022-08-27-23-27-28" border="0">

<b> Photo 2: Hata Mesajı</b>

&nbsp;

Göründüğü gibi exe dosyası çalıştırıldığı anda direkt bu mesajı kullanıcıya gösteriyor. Demek ki arka planda bir kimlik doğrulaması yapıyor ve doğrulama başaralı olmadığı için <b> Incorrect! Try Again</b> çıktısını veriyor. 

Şimdi çözüm için iki yöntemi anlatmaya başlayım.

&nbsp;

&nbsp;

## <b> 1. Yöntem </b>

&nbsp;

Öncelikle dosyayı x32dbg ile açalım. Daha sonra öncelikle stringlere bir göz atalım. xdbg aracı bu imkanı bize sunuyor. CPU sekmesinden herhangi bir yere sağ tıklayıp <b> Search For > All Modules > String References </b> sekmesine tıklayalım. Karşımıza şu ekran çıkacaktır:

<img src="https://i.ibb.co/yBRhgVr/Screenshot-from-2022-08-27-23-26-16.png" alt="Screenshot-from-2022-08-27-23-26-16" border="0">
<b> Photo 3: String Reference Sekmesi</b>

&nbsp;

Yukarıda görmüş olduğumuz gibi mesajda Incorrect! Try Again mesajı veriyordu. Fitre kısmına Incorrect yazıp sonuca bakalım:

<img src="https://i.ibb.co/XtKc7B0/Screenshot-from-2022-08-27-23-33-09.png" alt="Screenshot-from-2022-08-27-23-33-09" border="0">

<b> Photo 4</b>
&nbsp;

Stringlere bakıldığında Incorrect! Try Again adında bir string'e denk geliyoruz. Bu string'e iki kez tıklayalım:

<img src="https://i.ibb.co/VmnXbnR/Screenshot-from-2022-08-27-23-35-35.png" alt="Screenshot-from-2022-08-27-23-35-35" border="0">
<b> Photo 5</b>

&nbsp;

String'e iki kez tıkladığımızda hata ve doğrulama mesajını görebiliyoruz. Ve hemen üst tarafta ok ile gösterilen seri numarasına denk geliyoruz. Aslında çözümü bulmuş olduk. Fakat işimiz daha bitmedi. bu seri numarayı alıp <b> password.bin </b> dosyasına yapıştırdığımız da çözümü bulmuş oluyoruz. Program direkt çalıştığında bin dosyasını kontrol ediyor ve seri numarayı okuduğunda doğrulama cevabına denk geleceğiz:

<img src="https://i.ibb.co/4pd3JJY/Screenshot-from-2022-08-27-23-41-56.png" alt="Screenshot-from-2022-08-27-23-41-56" border="0">

<b> Photo 6 </b>

&nbsp;

Eğer linux tabanlı bir sistem kullanıyorsanız direkt echo ile yazdırabilirsiniz:

```bash
echo "W269N-WFGWX-YVC9B-4J6C9-T83GX" > password.bin
```

&nbsp;

VEEEE çözümü bulmuş olduk. Şimdi ise 2. çözüme geçelim..

&nbsp;

&nbsp;

## <b> 2. Yöntem </b>

&nbsp;

Aynı şekilde x32dbg ile exe dosyasını açalım. Photo 5'e kadar işlemleri yapalım. Eğer program doğrulamayı yapamazsa Incorrect hatası verdiğini görmüştük. Şimdi yapmak istediğimiz şey ise hata mesajına geldiğinde doğrulama mesajına atlayıp doğrulama mesajını göstermeye çalışacağız. Biraz kafa karıştırıcı olmuş olabilir resim üzerinden anlatalım:

<img src="https://i.ibb.co/nwj30m0/Screenshot-from-2022-08-27-23-59-00.png" alt="Screenshot-from-2022-08-27-23-59-00" border="0">

&nbsp;

Şimdi program kimlik doğrulamasını başarısız olarak sonuçlandıracağı için <b> Incorrect! Try Again </b> mesajını bize ekrana bastıracak. 
Bizde, hata mesajı bastıran komutun adresini, 2. kısımda gösterilen komutun adresi ile değiştireceğiz. Böylece program, MOV DWORD PTR SS:[ESP] kısmına geldiğinde direkt olarak 2. kısma atlayacak ve program oradan devam edecek ve 3 yazan yerde doğrulama mesajını ekrana bastıracak.

Şimdi ise fotoğrafta gösterilen 2 yazan komutun adresini kopyalayalım. Bunun için JNE c file crackme.401586  komuta sağ tıklayalım ve <b> Copy > Address </b> ile komut adresini kopyalayalım. Daha sonra hata mesajını ekrana bastıran komuta (yani fotoğraftaki 1 yazan yer) sağ tıklayalım ve <b> Assemble </b> kısmına tıklayalım.daha sonra ekranda çıkan textbox'a şunu yazalım:

```asm
jmp <address>
```
<b> jmp komutu direkt olarak belirtilen adrese atlar ve programı oradan devam eder. </b>

&nbsp;

Artık her şey tamam. Aslında göründüğünden daha basit. Sadece program hata mesajı kısmına geldiğinde direkt olarak jmp ile belirtilen adrese atlayacak ve program belirtilen adresten devam ederek doğrulama mesajını gösterecek. Dilerseniz bir kontrol edelim:

<img src="https://i.ibb.co/fH3pWdp/Screenshot-from-2022-08-28-00-16-47.png" alt="Screenshot-from-2022-08-28-00-16-47" border="0">

&nbsp;

Göründüğü gibi direkt olarak doğrulama mesajını ekrana bastırıyor. Arka planda gözüken ok işaretine bakıldığında şema ile de yaptığı işlem gözüküyor. Program, **00401586** adresine geldiğinde direkt olarak kopyalamış olduğumuz adrese atlayarak işlemleri oradan devam ediyor ve doğrulama mesajını ekrana bastırıyor. 


&nbsp;

&nbsp;

## Umarım açıklayıcı bir anlatım olmuştur. İyi çalışmalar dilerim.
</div>