# Bootcamp Case-2 <h1>


## Case 2.1 DB kullanan bir uygulamayı dockerized edip, nginx üzerinden serve edilmesi //  DB kullanan bir uygulamanın ansible ile dockerize edilmesi // Docker kurulumu ve container ayaga kaldırma islemlerinin ansible ile yapılması <h2>

Öncelikle makinemize ansible kurulumunu gerçekleştiriyoruz.

Bunu için ilk olarak centos repolistin kurulumunu yapmamız gerekiyor.

    sudo yum install epel-release

Ardından Ansible için gerekli komutu yazıyoruz.

    sudo yum install ansible

Ansible kurulumu sonrası versiyon bilgisini şöyle görebiliriz.

    ansible --version

Evet Ansible başarıyla kuruldu bu aşamada artık playbookları oluşturmaya hazırız.
İlk olarak playbooks diye bir klasör oluşturalım.

    mkdir playbooks
    cd playbooks/

Sonrasında ise öncelikle Docker kurulumu için gerekli olan playbookumuzu yazalım.

    vim docker_kurulum.yaml
>Yaml dosyamız aşağıdaki şekilde yazılacaktır.
![alt tag](https://cloudflare-ipfs.com/ipfs/QmbmmP6scbuuSw4jKZQG2qBdNVogNKctoYvMSQJknXK1xq)


>Oluşturduğumuz dosyayı aşağıdaki komuyla çalıştıralım.

    ansible-playbook docker_kurulum.yaml
![alt tag](https://cloudflare-ipfs.com/ipfs/QmdQnxWiYG5i68xyhRVp4E2x5yG3LPRsajbaZiUyo9q2Yo)

Docker kurulumunu tamamladık şimdi kontrol amaçlı docker servisine bakalım.

    systemctl status docker

![alt tag](https://cloudflare-ipfs.com/ipfs/QmcvTaVMZXZdxmP4Usu2SE3J1uRfz4df6RdFbQRSDBkbKi)


Docker'ın sistemde doğru bir şekilde çalıştığına emin olduk artık diğer aşamalara geçebiliriz.

>İlk olarak örnek bir Wordpress uygulamasını dockerize etme işlemini gerçekleştirelim. Bunu için bir playbook file oluşturacağız.

    mkdir wordpressplaybook
    cd wordpressplaybook/
    vim playbook.yml

![alt tag](https://cloudflare-ipfs.com/ipfs/Qmekz24HKYKKDwh2DN8Bg9axxNC21vntoVvrFBbrgbtGuv)

>Ardından playbooku çalıştıralım.

    ansible-playbook playbook.yml

![alt tag](https://cloudflare-ipfs.com/ipfs/QmZhiDtCPbjgDfuTp6Ee65XULa1m3cU8UyjD5wY8wyNjV4)

> Görüldüğü gibi playbook başarıyla çalıştı local sunucu adresimize giderek çalıştığını teyit edelim.

![alt tag](https://cloudflare-ipfs.com/ipfs/QmZoQ212yWnEUcoVrWYwxHTs3YDLoqHMtmhTagh6BfzQ4M)
![alt tag](https://cloudflare-ipfs.com/ipfs/QmWKd2eTwiQqEti4Wfy9x8Sa48Nps5ErNVTT3wsMuwM4au)

> Harika! Bu aşamada uygulamayı başarılı bir şekilde Dockerize ettik. Bir sonraki aşamaya geçebiliriz.

## Case 2.2 İlk adımda dockerize edilen uygulamanın Nginx üzerinden serve edilmesi ve gelen request içerisinde bootcamp=devops header'ı varsa "Hoşgeldin Devops" statik sayfasına yönlenebilmesi // Nginx kurulumu ve konfigürasyonu ansible ile yapılması  // “Hosgeldin DevOps" adlı bir statik sayfa oluşturularak, gelen request içerisinde bootcamp=devops header'ı varsa bu sayfaya yönlendirilmesi  <h2>

> Bu aşamada Nginx kurulumu ve konfigürasyonu için gerekli ansible file'ı oluşturalım.

    mkdir nginx-kurulum
    cd nginx-kurulum/
    vim playbook.yml

![alt tag](https://cloudflare-ipfs.com/ipfs/QmX6NbpP3Tcyx33wxdovs69zpcGwxyeQGv7JU91iyferC4)

> Ardından basit bir index.html dosyası oluşturup içine "Hoşgeldin Devops" yazısı ekliyoruz.

    vim index.html

![alt tag](https://cloudflare-ipfs.com/ipfs/QmSAvDXV2su3jeyxE1JZw3fYGbz3bTKu9bcmjB2uxMVZ2Y)

> Son olarak playbooku çalıştıralım.
    ansible-playbook playbook.yml

![alt tag](https://cloudflare-ipfs.com/ipfs/QmZEmkUXE4zrSEsJzaYAztT3zLmZ2DDoLnk3rfuVasYJJd)

> Browserdan sayfayı kontrol edelim. 

![alt tag](https://cloudflare-ipfs.com/ipfs/QmRd9V7m5s8H2jeMcnucnVJEcNgGksQkbqQdYiD9BnCEdJ)

Sayfamız başarıyla geldi.

**Gelen request içerisinde bootcamp=devops header'ı varsa bu sayfaya yönlendirilmesi**
_Tamamlanamadı, tamamlanmalı, tamamlanacak..._
