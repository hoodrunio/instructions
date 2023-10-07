![alt text](https://i.hizliresim.com/bw0rh5z.png)

# ÖNEMLİ
Subsquid görevleri içinde deploy etme yok. David bu konu hakkında aşağıdakileri yazdı. Şu an kurulum yapmanıza gerek yok.



![alt text](https://i.hizliresim.com/quvu9w7.jpeg)



Tech Görevlerini yapabilirsiniz: https://github.com/testnetrunn/instructions/blob/main/testnet/subsquid/techguide.md

# Genel Bakış


<a href="https://medium.com/testnet-run/d8285a043223">Kapsamlı Ödül Dağılımı ve Genel Bilgiler</a>
- **Program: Subsquid Genel Testnet ( Phase 1 ve 2 )** 
- **Katılım Kriterleri: Aşağıdaki Uygunluk bölümüne tabidir** 
- **Katılım Sınırı: Node Runners: Uygulama yoluyla seçilen en fazla `500` katılımcı; `en üst sıradaki 133 node` ödüller için uygun olacaktır.** 

- **Diğer Testnet Katılımcıları: Sınırsız; üst sıralarda yer alan `4.000` ödül için uygun olacak** 
- **Kayıt Son Tarihine Giriş:	Son tarih yok; Düğüm koşucusu başvuruları sürekli olarak gözden geçirilecektir - güncellemeler için Subsquid Discord'u kontrol edin** 
- **Zaman çizelgesi:	Genel testnet programının ~ 4 ay sürmesi beklenirken, Aşama 1 ve 2'nin sırasıyla ~ 60 gün sürmesi beklenmektedir. Zaman çizelgesi yalnızca Subsquid'in takdirine bağlı olarak değişebilir.** 
- **Tahsis Edilen Ödüller: 	Toplam token arzının ~% 2'sini temsil eden `26.600.000 SQD`**

- **Önemli: Bu node kurulumu ve form ilk aşamada başvuru içindir. Seçim yapıldığında size token gönderilecek.**





<a href="https://coinlist.co/subsquid-testnet">Coinlist</a>

İlk formu doldurmalısınız. (Varsa Coinlist hesabınızın bağlı olduğu mail ile formu doldurun.)

<a href="https://subsquid.deform.cc/testnetnodeapplication/">Başvuru Formu</a>

<a href="https://app.subsquid.io/squids/">Dashboard</a>


# Minimum Sistem Gereksinimleri

- **4 CPU**
- **8GB RAM**
- **1TB DISK**
- **Ubuntu 20.04+**

160GB Disk'te yeterli olacaktır.

```python
sudo apt update -y && sudo apt upgrade -y
```

```python
apt install npm
```

```python
sudo npm install -g npm@10.1.0
```

```python
curl -sL https://deb.nodesource.com/setup_20.x | sudo -E bash -
```

![alt text](https://i.hizliresim.com/6mn2dae.png)

60sn bekleyin sonra kurulum devam edecek.

```python
sudo apt-get install -y nodejs
```

Bundan sonraki kodları <a href="https://app.subsquid.io/squids/">Dashboard</a> giriş yaptığınızda verecek. Squid Name yerine bir isim verin. (küçük harf kullanın)

Aşağıdaki çıktılar sizin dashboardda giridğiniz kodlardan sonra alacağınız çıktılardır.

![alt text](https://i.hizliresim.com/1pmes4t.png)


![alt text](https://i.hizliresim.com/bv7w4pg.png)


![alt text](https://i.hizliresim.com/9p6sbk5.png)


![alt text](https://i.hizliresim.com/j6g9jf5.png)


Her şey doğru ise aşağıdaki gibi çıktı görmelisiniz.


![alt text](https://i.hizliresim.com/qgfokeg.png)


<a href="https://app.subsquid.io/squids/">Dashboard</a> üzerinden baktığınızda ilk senkronizasyon olacak.

![alt text](https://i.hizliresim.com/hb1u9iq.png)

![alt text](https://i.hizliresim.com/e58bcgy.png)

Eğer stuck durumuna düşerseniz genellikle portlar ile alakalıdır. (sıfır hetzner sunucu da stuck verdi)

`ufw disable`  yaptıktan sonra restart atın.

Restart yerinde dashboardda gördüğünüz isim@v.. nameinizi de girerek aşağıdaki kodu kullanın. Örn:

```python
sqd restart isim@v..
```


# Görevler

Node kurulumunun yanında görevleri de yapabilirsiniz.

Bunun için <a href="https://app.subsquid.io/squids/">Dashboard</a> üzerinde sağ üstten Switch the Network yaparak metamask'a Arbitrum Goerli ağını ekleyin.

![alt text](https://i.hizliresim.com/2cb9nuv.png)

Buradaki görevleri yapın. Karşılığında metamask adresinize $tSQD gelecek ve lider tablosunda ilerleyeceksiniz. (Sıralamada ilk 4000 ödül alacak)

![alt text](https://i.hizliresim.com/j0xh36b.png)


- **Zealy** **https://zealy.io/c/subsquid/invite/xo5zbBWhIyiAASUZkrxNt**

- **Galxe** **https://galxe.com/subsquid/**

# Hatalar (stuck, error, RPC)


Alchemy yada Infura üzerinden RPC eklemek için siteye kayıt olduktan sonra aşağıdaki gibi RPC oluşturun.

![alt text](https://i.hizliresim.com/10ivlse.png)



`API key`'e bastığınızda karşınıza çıkan yerden https olanı kullanacaksınız.

![alt text](https://i.hizliresim.com/cpgb3a0.png)




Buradaki linki ister sftp bağlantısı ile isterseniz sunucu üzerinden gerekli dosya içerisine ekleyin. 

Sunucu üzerinden `nano /root/adınız/src/processor.ts` 

adınız yazan yere dashboardda belirlediğiniz squidname'inizi girin.

Aşağıdaki chain yerine Alchemy yada Infuradan aldığınız https olan link ile değiştirdikten sonrs CTRL-X+Y yapın.

![alt text](https://i.hizliresim.com/kx45h4u.png)


`SFTP` bağlantısı ile yapacaksanız winscp vb. ile bağlandıktan sonra `/root/adınız/src/processor.ts` dizininde yukarıdaki ss'deki gibi chain
yerini değiştirin.

![alt text](https://i.hizliresim.com/rm0gqd4.png)


Bundan sonra tekrar deploy etmeniz gerekiyor

```python
sqd deploy --org adınız ./adınız
```

Loglara bakmak için

```python
sqd logs adınız@v1
```

Explorer

```python
sqd explorer
```








