# Linux-Kernel-Modul

Bu projede linux işletim sisteminin kernel modulünde değişiklikler yapacağız. Normalde işletim sistemine küçük bir kod parçası eklesek bile derlediğimizde saatlerimizi alacak bir işlem oluyor. Bu tarz sıkıntıları ortadan kaldırmak için LKM dediğimiz kod parçalarını kullanıyoruz. 

Projeyi yaparken https://sysprog21.github.io/lkmpg/ kaynağından çok faydalandım.

1- Öncelikle güncel sürümü kullandığımızdan emin olmamız gerekiyor. 

- ` $ sudo apt get update`
olmazsa
` $ sudo apt-get update`

- ` $ sudo apt dist-upgrade`

- ` $ sudo apt-get install linux-headers-$(uname -r)` header dosyalarını indiriyoruz.

> #### Kernel Modülü Nasıl Yazılır ?
 
 Terminale `$ vim modüladı.ko  ` yazıyoruz. Sonrasında örnekler bölümünde paylaştığım kodlardan istediğinizi  dosyaadi.c içerisine  yerleştiriyoruz.
 Sonrasında `$ vim Makefile  ` yazıp, paylaştığım makefile' ı ekliyoruz.
 
2- Sonrasında dosyaların bulunduğu dizine gidip ` $ make` komutunu çalıştırıyoruz.

Make komutu programların yeniden derlenme sürecini otomatik hale getirmek, sadece değişen kısımların yeniden derlenmesini sağlamak suretiyle zamandan kazanmak ve işlemleri her zaman otomatik olarak doğru sırada yapmak için tasarlanmıştır. Bunu da kaynak dosyaların son değiştirilme tarihlerine bakarak sadece derlenmesi gereken dosyaları derleyerek yapar.

3- Şimdi insmod komutunu çalıştırmadan önce bir işlem yapmamız gerekiyor.Bazı modüller diğer modüllerin yüklenmiş olmasına bağımlıdır ve bağımlı olunan modül yüklü değilse insmod komutu başarısız olur. Bu durumda önce bağımlı olunan modülleri tek tek yüklemeniz gerekir ya da modprobe kullanılabilir.

- ` $ insmod /Desktop/dosyaadi.ko `

içeri aktarmak için de
- ` $ sudo insmod modul.ko `


4- Modulün yüklenip yüklenmediğini anlamak için   ` $ lsmod | grep my_modul ` diyip   ` $ dmesg | tail ` ile de çıktısını görebiliriz.
