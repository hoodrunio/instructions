## Opside PoS Guide
![alt text](https://i.hizliresim.com/8nzb9w2.jpeg)

# Donanım

- İşletim Sistemi: 64-bit Linux, Mac OS X 10.14+, Windows 10+ 64-bit (Ubuntu 20.04+)

- CPU: 4

- Ram: 16GB

- Disk: En az 500 GB boş alana sahip SSD (mainnette 2 TB önerilir)

## PoS Rewards

Opside, ETH 2.0'ın geliştirilmiş bir sürümüne dayalı bir PoS konsensüsü kullanır. Validatör olarak katılmak için, kullanıcıların belirli bir miktarda IDE'yi yatırma sözleşmesine yatırması ve üç ayrı yazılım çalıştırması gerekir: yürütme istemcisi, mutabakat istemcisi ve validatör. Validatörler, ağ üzerinden yayılan yeni blokların geçerliliğini doğrulamaktan ve zaman zaman kendileri yeni bloklar oluşturup yaymaktan sorumludur. Bir validatör dürüst olmayan veya ihmalkar davranırsa, stake edilen IDE kaybedilecektir.

PoS kapsamında, Opside sabit bir blok üretim hızına sahiptir ve süre yuvalara (12 saniye) ve dönemlere (32-zaman dilimleri) bölünmüştür. Her yuvada, rastgele seçilen bir validatör, yeni bloklar oluşturmaktan ve bunları ağdaki diğer nodelara göndermekten sorumlu blok savunucusu olarak hizmet eder. Ek olarak, her yuvada, oylarını kullanarak önerilen bloğun geçerliliğini belirlemek için validatörlerden oluşan bir komite rastgele seçilir. Kesin mekanizma için lütfen ETH PoS'a bakın.

Opside, Alpha test ağında EIP-4844'ü desteklemeyi planlıyor ve ZK-Rollup'ın yürütme sonrasında tek tek nodelara aşırı yük bindirmeden işlem verileri sağlamasını sağlamak için Veri Kullanılabilirliği Örneklemesini (DAS) kullanıyor. Validatörler, tüm verilerin mevcut olduğunu doğrulamak için blobtaki işlem verilerini rastgele örnekler. Bu teknik aynı zamanda blok üreticilerinin tüm verilerini güvenli hafif istemciler için kullanılabilir hale getirmesini sağlayabilir. Teklif Veren-Oluşturan Ayrımı (PBS) altında, yalnızca blok oluşturucunun tüm bloğu işlemesi gerekirken, diğer validatörler doğrulama için veri kullanılabilirliği örneklemesini kullanır.

Genel olarak staking, ağ korumasına katılımı basitleştirir ve ademi merkeziyetçiliği destekler. Validatör nodelar, standart dizüstü bilgisayarlarda çalıştırılabilir ve bazı proxy staking pooları, kullanıcıların yeterli bir IDE bakiyesi olmadan stake yapmasına bile izin verir.

NOT: Validatör olmak için, yatırma sözleşmesine 25000 IDE yatırmanız gerekir.

## Güncellemeler

```python
sudo apt-get update -y && sudo apt-get upgrade -y
```

```python
sudo apt install -y build-essential libssl-dev cmake screen git htop
```


## Kontrol Noktası Senkronizasyonu (önerilir)

Kontrol noktası senkronizasyonu yapılandırıldığında, beacon nodeunuz, genesis'ten senkronizasyon yapmak yerine yakın zamanda tamamlanmış bir kontrol noktasından senkronizasyona başlayacaktır. Bu, kurulumları, doğrulayıcı geçişlerini, kurtarmaları ve ağ dağıtımlarını çok daha hızlı hale getirebilir.

```python
wget -c https://pre-alpha-download.opside.network/testnet-auto-install-v2.tar.gz 
tar -C ./ -xzf testnet-auto-install-v2.tar.gz
chmod +x -R ./testnet-auto-install-v2
cd ./testnet-auto-install-v2
```
 
Eğer Kontrol Noktası Senkronizasyonundan Kurulum yapmak istemezseniz Genesis Sonkronizasyondan devam edin.


## Genesis Senkronizasyonu

Beacon nodeunuzun senkronizasyonunu başlangıçtan itibaren başlatın, saatler sürebilir.

```python
wget -c https://pre-alpha-download.opside.network/testnet-auto-install.tar.gz 
tar -C ./ -xzf testnet-auto-install.tar.gz
chmod +x -R ./testnet-auto-install
cd ./testnet-auto-install
```

## Validatör İstemcisi

```python
./install-ubuntu-en-1.0.sh
```

![alt text](https://i.hizliresim.com/qmc2vcs.png)


Token withdraw için metamask adresinizi girin. Adresi girdikten sonra sizden parola oluşturmanızı isteyecek.
Parolanızı oluşturduktan sonra yürütme adresi olarak tekrar metamask adresinizi girin. Tekrar şifrenizi girmenizi isteyecek.

Size mnemonic (seed phrase) kelimelerini verecek. Bunları bir yere kaydetmeyi unutmayın. 

![alt text](https://i.hizliresim.com/pyev1a6.png)


Sizden tekrar mnemonicleri girmenizi isteyecek. Burada kelimelerin ilk 4 harfini girin

![alt text](https://i.hizliresim.com/7jml3bo.png)

![alt text](https://i.hizliresim.com/lvjvwxy.png)

![alt text](https://i.hizliresim.com/bsxm3fd.png)


Böyle bir çıktı almalısınız. Herhangi bir tuşa basın.

## Log Kontrol

- Execution client logları

```python
opside-chain/show-geth-log.sh
```

- Consensus client logları

```python
opside-chain/show-beaconChain-log.sh
```

- Validatör logları

```python
opside-chain/show-validator-log.sh
```

## Validatör Oluşturma

NOT: Beacon kurulumundan sonra, staking depozitonuzu göndermeden önce tamamen senkronize olduğunuzdan emin olun. Bu işlem birkaç gün sürebilir. (resmi uyarı)


## Geth Logları

```python
opside-chain/show-geth-log.sh
```

- Örnek Çıktı

![alt text](https://i.hizliresim.com/bdr46ya.png)


NOT: Blok yüksekliğinin son block'a yakın olup olmadığını görmek için https://pre-alpha.opside.info 'yu kontrol edin. evet ise, IDE'nin yatırılma zamanı gelmiştir.


- Nodeunuz sync olduktan sonra Bu siteye gidin: https://opside.network/validator/deposit

- WinSCP veya benzeri uygulama ile nodeunuzun olduğu sunucuya bağlanıp istenilen klasörü bilgisayarınıza indirin. 

- Dosya Dizini: /root/testnet-auto-install-v2/validator_keys/deposit_data

- Sitede Upload Deposit Data'ya kadar ilerleyin. Buradan winSCP ile indirdiğiniz data klasörünü yükleyin.

![alt text](https://i.hizliresim.com/74p6s50.png)


## Stake İşlemi


![alt text](https://i.hizliresim.com/f9lwjrc.png)

Discord'dan token aldığınız metamask cüzdanınızı bağlayın.

![alt text](https://i.hizliresim.com/32jskiy.png)

Opside Testnet ağını Metamask'a ekleyin.

![alt text](https://i.hizliresim.com/h6jwupt.png)


25000 IDE'yı stake edin.

## Çıktılar


![alt text](https://i.hizliresim.com/fdrz31b.png)

![alt text](https://i.hizliresim.com/pq9kd95.png)


## Explorer: https://pre-alpha-beacon.opside.info/













































