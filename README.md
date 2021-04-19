# Bootcamp Case-1 <h1>


## Case 1.1 Sanal makinada bir Centos kurup, güncellemelerinin yapılması <h2>

Bu islemde Oracle Virtual Box üzerinde bir sanal makine ayağa kaldıracağım.

### İzlenecek adım <h3>
    Yeni > Sanal Makine Oluştur > ad: centos-case dizin C:\Users\abdurmus\VirtualBox VMs Türü:Linux Sürüm Red Hat 64 Bit > İleri 

Makinemin özellikleri şu şekildedir.

    2048 MB RAM
    VDI Sabit Disk 16 GB

Ardından Başlat tuşuna basıyoruz.

>İmajımız seçilmesi bekleniyor. Centos.org'dan indirdiğimiz CentOS-7-x86_64-Minimal-2009 sürümünün iso dosyasını göstererek başlat diyoruz.
>Boot ekranından "Install Centos 7" ile devam ediyoruz

Welcoming ekranından English - EN US ile devam ediyoruz.

Installation kısmında 

    Date Time : Istanbul
    Keyboard :Turkish
    Language: EN US
    Installation source :  VDI Sabit Disk 16 GB daha önce oluşturup mount ettiğimiz alanı seçiyoruz

>Kalan ayarlara dokunmadan ilerleyerek kurulumu başlatıyoruz. 
>Root şifremizi bu adımda belirleyebiliriz.
>İstersek kullanıcıda oluşturabiliriz fakat bu adımı makinede elle yapacağız.

Ve kurulum işlemi tamamlandıktan sonra reboot komutu ile sunucumuzu yeniden başlatalım. Tebrikler Centos kurulumunu bitirdik!

Açılış sonra login : root ve password'e belirlediğimiz 

sonrasında ;

    sudo yum update

komutu ile gerekli güncelleştirmeler yapılır. -y parametresi sona eklendiğinde otomatik onaylayacaktır.


## Case 1.2 Kişisel bir user yaratılması (ad.soyad şeklinde) Not: aşağıdaki işlemler bu kullanıcı ile yapılacak <h2>

Aşağıdaki komutları sırasıyla ilerleyelim 

    adduser abdurmus
    passwd abdurmus
    usermod -aG wheel abdurmus
    su - abdurmus

>Açılan sayfadan parolamızı belirleyelim ardından user başarıyla oluşacaktır. 
>Wheel grubuna kullanıcıyı etkileyerek sudo erişimine açıyoruz.
>Son olarak abdurmus kullancısına geçiş yapıyoruz.

## Case 1.3 Sunucuya 2. disk olarak 10 GB disk eklenmesi ve "bootcamp" olarak mount edilmesi <h2>

>Disk ekleme işlemi yapılması için makineyi shutdown ediyoruz.
>Ardından Virtualboxda centos-case> ayarlar> Depolama > Denetleyici > Disk Oluştur
>Adımlarını izleyerek 10 GB ek VDI alanı ekliyoruz.
>Ardından makineyi tekrar başlatıyoruz.

Aşağıdaki komutları sırasıyla ilerleyelim 

    fdisk -l
    mkfs.ext3 /dev/sdb
    mkdir /bootcamp
    mount /dev/sdb /bootcamp

>İlk olarak diskimize bağlı mount alanlarını inceleyip sonrasında /dev/sdb altında yeni bağladığımız diski görelim.
>Sonrasında ilgili alanı formatlayalım.
>Ardından mount edeceğimiz bootcamp alanını oluşturalım
>Sonrasında ilgili alanı /dev/sdb ye mount etme işlemini yapalım.

Bu adımda ek olarak yapmamız gerekenler;

    nano /etc/rc.d/rc.local
    mount /dev/sdb /bootcamp


>ilgili dizin altında mountun kalıcı olabilmesi için nano ile giriş yapalım.
>Sonrasında aşağıdaki komutu dosyaya ekleyip kaydedelim.

## Case 1.4  /opt/bootcamp/ altında bootcamp.txt diye bir file yaratılıp, file'ın içerisine "merhaba trendyol"yazılması <h2>

Burada mkdir ve -p parametresini ve touch komutunu kullanarak tek satırda gerekli dosya yolunu yaratalım.

    sudo mkdir -p /opt/bootcamp/ && sudo touch /opt/bootcamp/bootcamp.txt


Sonrasında ilgili dosya içersine girerek merhaba trendyol yazdıralım

    sudo nano /opt/bootcamp/bootcamp.txt

_ Yazım sonrası CTRL+X kombinasyonuna Y ile kaydedip çıkabiliriz. _ 

## Case 1.5 Kişisel kullanıcının home dizininde tek bir komut kullanarak bootcamp.txt file'ını bulup, bootcamp diskine taşınması <h2>

Burada ise find komutu ile bulma işlemini mv komutu ilede taşıma işlemini yürütücez

    sudo find / -iname bootcamp.txt -exec mv {} /bootcamp/ \;
>Burada ilk olarak find komutu root dizini altında bootcamp.txt dosyasını buluyor ardıdan -exec parametresi ile mv komutu ise bulduğumuz dosyayı /bootcamp altına gönderiyor.
