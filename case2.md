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

>İlk olarak örnek bir Wordpress uygulamasını dockerize etme işlemini gerçekleştirelim. Bu aşamada işlemlerimizi Ansible Roles yapısı üzerinde yapacağız. 

İşe Ansible galaxy proje yapımızı oluşturarak başlayalım.

    ansible-galaxy init wordpress-nginx

Bu bize aşağıdaki yapıyı oluşturacaktır.

![alt tag](https://cloudflare-ipfs.com/ipfs/QmT2jxjqBdEjLMscSuecRZrGVDfTJFTncfFUUmqPnZ5LbG)




