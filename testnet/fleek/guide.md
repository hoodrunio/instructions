![alt text](https://i.hizliresim.com/6980i8v.png)

# Hatırlatma

İlk ağ oluşumuna, node kurulum testine ve protokol performans ölçümüne odaklanan 1 haftalık bir early alfa test ağı aşaması yürütecekler.
12 Eylül'den önce her zaman kurabilirsiniz. Form gönderim ve onaylama olduğundan erken kurmakta fayda olacaktır.

- **5 Eylül 2023: Testnet Başlangıcı** 
- **8 Eylül 23:00: Node Community Call**
- **12 Eylül: Testnet Optimizasyonunun Kapatılması**
- **14 Eylül:Geri bildirim, veri sonuçlarını ve kalıcı testnet spin-up tahminleri.**

# Roadmap

- **Phase 0 ila 5
Fleek Network, mainnetin kullanıma sunulması için çok aşamalı bir yaklaşım kullanacaktır. Aşağıda belirtilen mevcut yüksek düzeyli plan, çeşitli faktörlere bağlıdır ve farklı aşamalar boyunca toplanan geliştirme zaman çizelgelerine ve/veya veri/geri beslemeye yanıt olarak değişebilir.**

- **Phase 0 ( 5 Eylül ): Node Çıkışı
İlk ağ ve node testi ( performans, donanım özellikleri, kümeleme, maliyetler, metrikler vb.)**

- **Phase 1 ( Eylül ortası ): SDK / Hizmet Sunumu
SDK'yı tanıtın ve ağdaki hizmetlerin inşasını ve kullanımını ve ayrıca Phase 0'a dayalı bazı optimizasyonları test edin.**

- **Phase 2 ( Ekim ): İlk Ekonomi Sunumu
Test ( değersiz ) tokenları ve Phase 1'e dayalı bazı optimizasyonlar kullanarak stake, fiyatlandırma ve diğer unsurlar/durumlar dahil olmak üzere ekonomik algoritmanın daha somut bir versiyonunu tanıtın ve test edin.**

- **Phase 3 ( Kasım ): Layer 2 Sözleşmelerinin Sunulması
Protokolün bir Ethereum L2 ( stake, depozito ve token sözleşmeleri, L2 / FN arasındaki iletişim vb. ) üzerinde yaşayacak yönlerinin bir test sürümünü tanıtın.**

- **Phase 4 ( Aralık ): Son Sunum
Tüm aşamalardaki tüm veri / geri bildirim ve optimizasyonlara dayanarak ağın ilk neslinin son formunu tanıtın ve gerçekçi bir ana ağ ortamının nasıl olacağını test etmeyi sağlayın.**

- **Phase 5 ( Q1 2024 ): Mainnet Lansmanı**

# Minimum Sistem Gereksinimleri

- **4 CPU**
- **32GB RAM**
- **20GB DISK**
- **Ubuntu 22.04+**

16GB Ram'de hata verecek ama yine devam edebiliyorsunuz. 



```python
sudo apt update && sudo apt upgrade -y
```

```python
sudo apt install curl tar wget clang pkg-config libssl-dev jq build-essential bsdmainutils git make ncdu gcc git jq chrony liblz4-tool -y
```

```python
curl https://get.fleek.network | bash
```

Eğer 16GB RAM kullanırsanız aşağıdaki gibi bir hata alacaksınız. Enter yaparak devam edebilirsiniz.

![alt text](https://i.hizliresim.com/ad5gmgq.png)

Eğer 32GB RAM kullanıyorsanız hata vermeyecek.


Eğer aşagıdaki gibi ROOT  hatası alırsanız lgtn adında bir user oluşturun ve tekrar yukarıdaki fleek.network kodunu girin.

![alt text](https://i.hizliresim.com/kly3wwh.png)

```python
adduser lgtn
```

```python
usermod -aG sudo lgtn
```

```python
su lgtn
```

![alt text](https://i.hizliresim.com/tqz27hc.png)

Kurulum biraz uzun sürebilir. Kurulum bittikten sonra firewall hatası alırsanız aşağıdaki gibi bir çıktı göreceksiniz.

![alt text](https://i.hizliresim.com/ol7tdnc.png)

Bu durumda tekrar sunucuya bağlanıp aşağıdaki kodu girin ve sonra diğer sunucu bağlantınızda Enter yapın.

```python
ufw disable
```

![alt text](https://i.hizliresim.com/d1rozv4.png)

Yukarıdaki çıktı da Node Public Key ve Consensus Public Key çıktılarını kaydedin. 

/root/.lightning/keystore dizinindeki keystore dosyasını sftp bağlantısı ile bilgisayarınıza indirin.

![alt text](https://i.hizliresim.com/m7k1ro4.png)



Çıktıdaki gibi uyarı alacaksınız. Node'unuzu gerekli bilgileri girerek form ile göndermeniz gerekiyor. 

![alt text](https://i.hizliresim.com/eg3om5z.png)

Form için Fleek Discord'unda access-form kanalında aşağıda gösterildiği gibi bilgilerinizi girin. 


![alt text](https://i.hizliresim.com/7rehvjp.png)

![alt text](https://i.hizliresim.com/p2ywll6.png)

Ağ başlatma

```python
systemctl start lightning
```

Durdurma veya restart

```python
systemctl stop lightning
systemctl restart lightning
```

Status çıktısı

```python
systemctl status lightning
```

![alt text](https://i.hizliresim.com/697uy7s.png)

Node çıkışı 

```python
tail -f /var/log/lightning/output.log
```

Diagnostics

```python
tail -f /var/log/lightning/diagnostic.log
```

Node Public Key ve Consensus Public Key çıktısı

```python
lgtn keys show
```

# Güncelleme 

```python
curl -sS https://get.fleek.network/update | bash
```

# Whitelist Kontrolü

Eğer discord kanalında WL için etiketlenmişseniz aşağıdaki kodu girerek kontrol edin. Eğer hala WL değilsiniz derse yukarıdaki update kodunu girin restart atın ve tekrar deneyin.

```python
curl -sS https://get.fleek.network/whitelist | bash
```

![alt text](https://i.hizliresim.com/6gqc6z5.png)


Health Check

Eğer WL almışsanız aşağıdaki kodlar ile kontrol edin.

```python
curl -w "\p" localhost:4069/health
```


Çıktı: OK olmalıdır. 

![alt text](https://i.hizliresim.com/iw85h50.png)

```python
curl -X POST -H "Content-Type: application/json" -d '{
      "jsonrpc": "2.0",
      "method": "flk_ping",
      "params": [],
      "id": 1
    }' http://127.0.0.1:4069/rpc/v0
```

![alt text](https://i.hizliresim.com/q3iv3rf.png)


- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**

- **https://twitter.com/testnetrun**





