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
![alt tag](https://cloudflare-ipfs.com/ipfs/QmRo5A8rY5n8DCtfTk32maAXTXUjhy3B29bYH8XvhZqDU6)
