![alt text](https://i.hizliresim.com/fy7ssnq.png)


# HATIRLATMA

Yalnızca RollApp-fam Discord rolüne sahip olanlar RollApp'lerini portalda listeleme hakkına sahiptir.

## RollApp Ödülleri

### En İyi 10 RollApps

İlk 10 RollApp’e ödül havuzunun %10'u tahsis edilecektir. Hayal gücünüzü özgürce çalıştırın. RollApps ultra hızlı, IBC bağlantılı ve VM-agnostiktir.

Geliştiriciler, EVM akıllı sözleşmelerini RollApps’lerine kolayca dağıtabilirler. Mevcut uygulamaları konuşlandırılmış RollApp’lere taşımak sadece birkaç tıklama kadar kolay olabilir. Ek olarak, Cosmos SDK uygulamaları bir RollApp olarak çalışacak şekilde taşınabilir.

En İyi 10 RollApps için oylama, insanlara inşa etmek için yeterli zaman vermek amacıyla Teşvikli Testnet’in sonuna yakın bir zamanda özel bir şekilde yapılacaktır. Oylama dönemlerinin başlangıcı ve bitişi ve uygun oy verenler hakkında ihtiyacınız olan tüm bilgilerle sizi döngü içinde tutacağımıza söz veriyoruz. Üstüne üstlük, En İyi 10 RollApp için ödüller ve diğer tüm ödüller, herhangi bir kilitlenme süresi olmaksızın, oluşumdan sonra anında dağıtılacaktır!

## En İyi 10 Ödül Üç Grup Halinde Dağıtılacaktır:

1. Grup: En iyi 3 RollApp, her biri 200 bin DYM’lik eşit bir pay alacaktır.

2. Grup: 4, 5 ve 6. sıradaki RollApps’lerin her biri 100K DYM’den eşit pay alacaktır.

3. Grup: Son 4 yarışmacının her biri 25 bin DYM’den eşit pay alacaktır.


RollApp Dağıtıcıları, RollApp’ları sadece birkaç tıklama ile kolayca dağıtmak için Roller CLI kullanmalıdır. Daha önce Roller CLI yüklemiş olanlar için lütfen `roller migrate` kullanarak sürümü yükseltin.

Dağıtımcılar Portal üzerinde kendi RollApps kontrol panellerine sahip olacaklardır. Portalda ilk kez listelendiğinde, RollApp aktif olmayan bir ödül durumunda başlayacaktır.
Ödül akışına uygunluk sürecini tamamlamak için, RollApp dağıtıcıları Discord kanalına yönlendirilir ve burada RollApp yayınlama sürecini takip etmeleri istenir.
Onaylandıktan sonra RollApp ödülleri yayınlanmaya başlayacaktır. RollApp Dağıtıcıları tahmini ödüllerini RollApp kontrol panelleri üzerinden takip edebileceklerdir.

## Ödüllerin nasıl biriktirildiğine dair bir özet:

Uptime: Dymension Hub’daki durum güncellemeleri kontrol edilerek periyodik olarak ölçülecektir.
Aktif RPC: periyodik olarak kontrol edilecektir. RollApp RPC uç noktalarınızı açığa çıkarmak ve bunları listelemenizde sunmak ödülleri önemli ölçüde artıracaktır.
Traction Boost: RollApps’e, elde ettikleri topluluk katılımı düzeyine göre traction boost desteği verilecektir.
Bu puanlar, RollApps’in özel ödül havuzundaki emsallerine göre performansını ölçmek için kullanılacaktır.

- **Genel Makale** **https://medium.com/@dymension/froopyland-is-live-8bf21e9d7046**


# Portal Listeleme

1: Bir RollApp'i başarıyla dağıttığınızdan ve çalıştırdığınızdan emin olun. (roller run çıktısı active olmalı)

2.: Aşağıdaki gerekli portların açık olduğundan emin olun.

```python
RollApp RPC Endpoint (varsayılan 26657)
Rest Endpoint (varsayılan 1317)
JSON RPC Endpoint (varsayılan 8545. Yalnızca EVM RollApps ile ilgilidir)
```

3.: Faucet'i finanse edin ve RollApp jetonunuzun IBC transferini aşağıdaki komutla Dymension Hub musluğuna göndererek IBC bağlantısını test edin:

Dymension Hub faucet adresini aşağıdaki kodu kullanarak kendi tokeniniz ile finanse edin. 

```python
roller tx fund-faucet
```

![alt text](https://i.hizliresim.com/f1q6uuu.png)

Daha sonra Dymension Hub faucete RollApp tokeninizin ulaşmasını bekleyin. (tahmini 15-20dk) Sonra aşağıdaki kod ile discord froopyland-faucet kanalından işlemi kontrol edin.

```python
$balance dym1g8sf7w4cz5gtupa6y62h3q6a4gjv37pgefnpt5 <RollApp-ID>
```
RollApp ID yerine kendi rollappinizin ismini girin.

![alt text](https://i.hizliresim.com/jsxytka.png)


Sunucu üzerinden aşağıdaki kod ile alacağınız çıktıyı parantezler dahil koplayayıp bilgisayarda kendi RollApp ID'niz ile oluşturmuş olduğunuz json dosyasına yapıştırın.

![alt text](https://i.hizliresim.com/aovkbkh.png)

Yapıştırdığınız çıktıda değiştirecek olduğunuz yerler;

chainName yerindeki RollApp ID'niz yerine portalda gösterilmesini istediğiniz bir isim girebilirsiniz.

```python
"rpc": "http://sunucu-ipniz:26657"
"rest": "http://sunucu-ipniz:1317"
"rpc": "http://sunucu-ipniz.8545"
```
50kb'dan az boyuta sahip jpeg veya png logonuz için logo yerlerinde aşağıdaki ssdeki gibi RollApp ID'niz ve logo uzantınıza göre düzenleyin.

Örnek Görsel

![alt text](https://i.hizliresim.com/mlemveb.png)

Buraya kadar yapmışsanız Bilgisayarınızda RollApp ID'niz ile bir klasör oluşturun. İçinde aşağıdaki dizinlere dikkat ederek json dosyasını ve logonuzu ekleyin.

![alt text](https://i.hizliresim.com/qtqwpk4.png)

## Github İşlemleri

Dymension RollApp-registry reposunu forklayın.

- **Github Repo** **https://github.com/dymensionxyz/rollapp-registry**

![alt text](https://i.hizliresim.com/ftbz1ea.png)

Forkladığınız dizinde Upload files yapın.

![alt text](https://i.hizliresim.com/6ujdikt.png)

Bilgisayarınızda istenilen şekilde düzenlemiş olduğunuz RollApp ID isimli klasörünüzü yükleyin.

![alt text](https://i.hizliresim.com/4j1srgm.png)

Yüklemeden sonra dosyanızı pull request yapın

![alt text](https://i.hizliresim.com/ofoah6h.png)

Bu işlemden sonra Discord kanalındaki list-your-rollapp kanalına aşağıdaki yazıyı gönderin. 

```python
 $pair <RollApp-ID>
 ```

![alt text](https://i.hizliresim.com/5nsnw91.png)

Bu işlemden sonra yoğunluğa göre açmış olduğunuz kanaldan takım sizinle iletişime geçecek. İletişim zamanında sizden göndermiş olduğunuz PR'ın linkini isteyecekler.
Gerekli kontroller yapıldıktan sonra RollApp'iniz portal la listelenecek.


- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**
