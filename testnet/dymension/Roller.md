
![alt text](https://i.hizliresim.com/9w1u7aw.png)


```python
curl -L https://dymensionxyz.github.io/roller/install.sh | bash
```

![alt text](https://i.hizliresim.com/cu4uhb7.png)


```python
roller version
```

![alt text](https://i.hizliresim.com/ke5ezi9.png)



```python
roller config init --interactive
```
Ağ olarak froopyland'ı seçin

![alt text](https://i.hizliresim.com/9f9688f.png)


RollApp ID için istenilen tarzda ID belirleyin. örn: mytestnetrunrollapp_3448-1

Enter your RollApp ID: örn:mytestnetrunrollapp_3448-1
Specify your RollApp denom: örn:TNR
How many TNR tokens do you wish to mint for Genesis? Token adedini belirleyin örn: 10000000000
Diğer soruda celestia seçtim.

![alt text](https://i.hizliresim.com/nl536xo.png)



Burada verilen 3 cüzdana da Discord kanalından token isteyin.

Dym adresleri için froopyland-faucet
Celestia adresi için celestia-faucet

![alt text](https://i.hizliresim.com/tauygsy.png)
![alt text](https://i.hizliresim.com/d6r186r.png)
![alt text](https://i.hizliresim.com/qhqmawp.png)


```python
roller register
```

![alt text](https://i.hizliresim.com/q0wmyxb.png)


Çalıştırmadan önce screen sayfası açın 

```python
screen -S Roller
```

```python
roller run
```



Bu panelde DA Light Client, Relayer ve Squencer Active olarak çalışması gerek. Channel oluşturma ve ID bulması uzun sürebilir. 

![alt text](https://i.hizliresim.com/iki0ca0.png)


Channel ID bulduktan sonra şöyle görünecek

![alt text](https://i.hizliresim.com/34hzrrr.png)

### IBC transferi

Dymension Hub faucet adresi: dym1g8sf7w4cz5gtupa6y62h3q6a4gjv37pgefnpt5

- **RollApp kaynak kanalı**

```python
roller relayer channel show
```

💈 Relayer Channels: src, channel-0 <-> channel-1, dst 
Bu çıktı paneldeki Relayer çıktısı ile aynıdır.
Buradaki channel-0 yerine sizde ne yazıyorsa o sizin kaynak kanalınızdır.

```python
rollapp_evm tx ibc-transfer transfer transfer <src-channel> dym1g8sf7w4cz5gtupa6y62h3q6a4gjv37pgefnpt5 5000000000000000000000000<base-denom> --from rollapp_sequencer --keyring-backend test --home ~/.roller/rollapp --broadcast-mode block
```

koddaki <src-channel> : channel-0 (sizin relayer çıktısındaki kaynak kanalı)

base-denom: buraya oluşturmuş olduğunuz tokenin adını girin. Örnek olarak TNR ise uTNR olarak girin

```python
Örnek kod: 
rollapp_evm tx ibc-transfer transfer transfer channel-2 dym1g8sf7w4cz5gtupa6y62h3q6a4gjv37pgefnpt5 5000000000000000000000000uTNR --from rollapp_sequencer --keyring-backend test --home ~/.roller/rollapp --broadcast-mode block
```

Bundan sonra 5-10 dk bekleyin. Discord froopyland-faucet kanalında balances kontrolü yapın.

```python
$balances dym1g8sf7w4cz5gtupa6y62h3q6a4gjv37pgefnpt5 <rollapp-id>
```

Buradaki rollapp-id sizin id ilk başta belirlediğiniz id'niz. örnek: mytestnetrunrollapp_3448-1

Bot Dymension Hub adresinde sizin token adetini gösterdikten sonra kendi tokeninizi talep edin

```python
$request <user-address> <rollapp-id>
```

user-address: dym adresiniz

NOT: channel aktif olduktan sonra burayı ss ler ile güncelleyeceğiz.


- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**

- **https://twitter.com/testnetrun**
