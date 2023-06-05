

![Postman logo](https://assets.getpostman.com/common-share/postman-github-logo.png "Postman logosu")

# Postman Öğrenme Merkezi

Postman, API geliştirmesi için işbirliği platformudur. [Postman Öğrenme Merkezi](https://learning.postman.com/), Postman ile hızlı bir şekilde başlamanızı ve becerilerinizi geliştirmenizi sağlayacak kaynaklara sahiptir. Postman, API test durumlarını istediğiniz herhangi bir formatta (JSON/XML/ve daha fazlası) yazmanıza ve API'nizi doğrulamak ve geçerliliğini kontrol etmek için çalıştırmanıza olanak sağlar. Ayrıca Postman, geliştiricinin iş akışını iyileştirebilen [koleksiyonlar](https://learning.postman.com/docs/getting-started/creating-the-first-collection/) sağlar. Ayrıca, API odaklı geliştirme için API şemaları yazma ve sunucu kodu oluşturma gibi güçlü araçlar mevcuttur. Postman, Windows, macOS ve Linux gibi birçok platformda kullanılabilir. Daha fazla bilgi için [Postman websitesini](https://www.postman.com/) ziyaret edebilirsiniz.

## Katkıda Bulunma Kılavuzları

Öğrenme Merkezi'ne katkıda bulunmanızı çok isteriz! Bu projeye katkıda bulunmak için lütfen aşağıdakileri okuyun:

* [Davranış Kuralları](https://www.postman.com/code-of-conduct)
* [Katkıda Bulunma Kılavuzları](CONTRIBUTING.md)
* [Belge Yazım Kılavuzu](DOCS_STYLE_GUIDE.md)

**NOT:** GitHub Actions ile yeni bir Markdown denetleyici ekledik. Bir "pull request" (çekme isteği) yaparken, bu denetleyiciye karşı çalıştırılacak. Değiştirilen dosyalarınızın denetlemeyi geçmesi, birleştirilmeden önce gereklidir. Daha fazla bilgi için [katkıda bulunma kılavuzunda](CONTRIBUTING.md) bulunan bilgilere bakabilirsiniz.

> Katkılarınız için teşekkür etmek için size özel Katkıda Bulunan ürünler göndermekten mutluluk duyarız. [Katkıda Bulunan Gönderim Formu](https://docs.google.com/forms/d/e/1FAIpQLSfbLAcxl-IOiv3NmgEaWw7FleOaXnIyIoIrY_zn6U4JvjQBGA/viewform?usp=send_form)'nu doldurun ve minnettarlığımızı göstermek için size bir jest gönderelim.

## Öğrenme Merkezini Yerel Olarak Oluşturma

```shell

   $ git clone https://github.com/postmanlabs/postman-docs.git
   $ cd postman-docs
   $ npm

 run nvmrc
   $ nvm use
   $ npm install
   $ npm install -g gatsby-cli
   $ npm run dev

```

**NOT:** Bu site Node.js v14.17.1 ile oluşturulmuştur. [nvm](https://github.com/nvm-sh/nvm) yüklemenizi ve Node.js sürümünü v14.17.1 olarak ayarlamanızı öneririz.

### Docker ile Oluşturma

Öğrenme Merkezini Docker içinde oluşturabilir ve çalıştırabilirsiniz. Bunun için bir `dockerfile` oluşturmanız gerekmektedir.

1. İlk olarak, depoyu klonlayarak başlayın:

   `git clone https://github.com/postmanlabs/postman-docs.git`

2. Aşağıdaki içeriklere sahip bir dosya oluşturun ve `dockerfile` olarak adlandırın:

    ```shell

    FROM node:14

    EXPOSE 8000

    # postman-docs proje dizinini kopyalayın
    COPY postman-docs /var/postman-docs

    WORKDIR "/var/postman-docs"

    RUN npm install -g gatsby-cli
    RUN npm install --force

    CMD ["yarn", "dev", "-H", "0.0.0.0" ]

    ```

    `dockerfile`, `postman-docs` dizininin olduğu dizinde bulunmalıdır.

    ```shell

    # örnek dizin yapısı
    |--[geçerli dizin]
       |--postman-docs
       |--dockerfile

    ```

3. Bu komutla Docker imajını oluşturun:

   `$ docker build --tag postman-docs:1.0 .`

4. İmajı kullanarak bir konteyner başlatın

   `$ docker run -p 8000:8000 -d postman-docs:1.0`

#### Docker Compose

Yukarıdaki `dockerfile` ve aşağıdaki `docker-compose.yaml` kullanılarak `docker-compose` komutu ile de oluşturabilirsiniz:

```yaml

version: '3'
services:
  node:
    build:
      context: ./
    ports:
      - "8000:8000"

```

`docker-compose.yaml` dosyası, `postman-docs` dizininin ve `dockerfile`'ın olduğu dizinde bulunmalıdır.

```shell

# örnek dizin yapısı
|--[geçerli dizin]
   |--postman-docs
   |--dockerfile
   |--docker-compose.yaml

```

Aşağıdaki komutla konteyneri başlatın:

`$ docker-compose up`

## Proje Yapısı

Oluşturulan site, en güncel belgeleri barındıracaktır. Tüm eski belgeler GitHub'da saklanır ve oluşturma işleminden hariç tutulur.

### Belgeleri güncelleme

* Gönderiler, `/src/pages/docs` klasörü altında tutulur.

* `/docs` klasörünün klasör yapısı URL yapısı için kullanılır. Örneğin, `/docs/postman/variables-and-environments/variables.md`, `https://learning.postman.com

/docs/postman/variables-and-environments/variables/` URL'siyle eşlenir.

* Belgelerdeki bağlantılar göreli olmalıdır. Örnek:

```shell

   [Newman](/docs/postman/collection-runs/command-line-integration-with-newman/)
```

## Kaynaklar

* [Postman'ı İndirin](https://www.postman.com/downloads/)
* [Postman Masaüstü Agent'ı İndirin](https://www.postman.com/downloads/postman-agent/)
* [Postman Sürüm Notları](https://www.postman.com/downloads/release-notes)
* [Postman Entegrasyonları](https://www.postman.com/integrations/)
* [Postman API'si](https://www.postman.com/postman/workspace/postman-public-workspace/documentation/12959542-c8142d51-e97c-46b6-bd77-52bb66712c9a/)
* [Postman Topluluğu](https://community.postman.com/) (Discourse)

## Lisans

[Apache License 2.0](LICENSE)