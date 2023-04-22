# Cosmos Projelerinde Kullanılan Genel Kodlar

- **Cosmos tabanlı projelerin node testnetlerinde node kurarken, validatör oluştururken yada diğer işlemler için kullanılan kodlar aynıdır.**
- **Kodlarda değişen yerler, proje ismi ve projenin tokenidir.**

- **Buna aşağıdaki görselden bakalım. Kodlarda sadece proje ismi değişmektedir. Nadir olarak bazı projelerde örnek olarak Dymension projesinde 
kullanılan kodlarda dymensiond yerine dymd kullanılır. 
Tokenlerde ise daha fazla değişkenlikler gösterebilir. Kyve da iki tane olmasının nedeni biri kaon ağında diğeri mainnet ağında kullanılan token adlarıdır.**

![alt text](https://i.hizliresim.com/hz9px1d.png)

# Yukarıdaki bilgilere göre genel kullanılan kodlar;
## (kodlar kujira projesi üzerinden yazılmıştır)

- **Cüzdan isminizi değiştirmek isterseniz wallet olan yerleri kendi cüzdan isminiz ile değiştirebilirsiniz.**

##Yeni Cüzdan 

```
kujirad keys add wallet
```

## Kullanmak istediğiniz cüzdan (cüzdan mnemoniclerinizi import etmek için)

```
kujirad keys add wallet --recover
```
## Cüzdanları isimleri ve adresleri ile listeleme

```
kujirad keys list
```

## Validatör Oluşturma

```
kujirad tx staking create-validator \
--amount=1000000ukuji \
--pubkey=$(kujirad tendermint show-validator) \
--moniker="Monikeradınız" \
--identity=id \
--details="detaylar" \
--website="sitelinki" \
--chain-id=kaiyo-1 \
--commission-rate=0.10 \
--commission-max-rate=0.20 \
--commission-max-change-rate=0.01 \
--min-self-delegation=1 \
--from=wallet \
--gas-prices=0.1ukuji \
--gas-adjustment=1.5 \
--gas=auto \
-y
```
Validatör oluşturma kodunda değiştirecek olduğunuz yerler; kujirad, 1000000 (token adedi), ukuji , monikeradınız, id, detaylar, ve eğer değiştirmişseniz cüzdan isminiz (wallet)


- **--amount= delege etmek istediğiniz token miktarı**
- **--moniker="Monikeradınız" = Validatör isminiz (monikeradınız yerine yazılacak)**
- **--identity=id https://keybase.io/ sitesine kayıt olup profil resmi yükledikten sonra profilinizde gözüken id numarasını id yerine boşluksuz şekilde yazarsanız explorer üzerinde validatörünüzün resmi gözükür.**

![alt text](https://i.hizliresim.com/ss2q435.png)

- **--details= Validatörünüz hakkındaki bilgiler. (detaylar yerine yazılacak)**
- --website=sitenizin linki
- **--chain-id= projenin ağ ismi**
- **--commission-rate= validatörünüze stake edilen tokenlerden alacak olduğunuz komisyon oranı (0.10=%10)**
- **--commission-max-rate= maximum yapabileceğiniz komisyon oranı**
- **--commission-max-change-rate= komisyon düzeltmede yapabileceğiniz max komisyon değiştirme oranı**
- **--min-self-delegation= kendinize delege edeceğiniz minimum token miktarı**
- **--from= cüzdan isminiz**
- **--gas-prices= gas fiyatı (projeden projeye değişebilir)**
- **--gas-adjustment= gas ayarı**

## Oluşturmuş olduğunuz validatörde moniker, id, komisyon vb. değişikliği yapma

```
kujirad tx staking edit-validator \
--new-moniker="Monikeradınız" \
--identity=id \
--details="detaylar" \
--website="sitelinki" \
--chain-id=kaiyo-1 \
--commission-rate=0.1 \
--from=wallet \
--gas-prices=0.1ukuji \
--gas-adjustment=1.5 \
--gas=auto \
-y
```

## Jailed durumundan kurtulmak için

```
kujirad tx slashing unjail --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```


## Validatör detayını görme

```
kujirad q staking validator $(kujirad keys show wallet --bech val -a)
```

## Validatörünüzde biriken ödülleri çekme

```
kujirad tx distribution withdraw-all-rewards --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```

## Validatörünüzde biriken ödül ve komisyonları çekme

```
kujirad tx distribution withdraw-rewards $(kujirad keys show wallet --bech val -a) --commission --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```

## Kendi Validatörünüze token delege etme

```
kujirad tx staking delegate $(kujirad keys show wallet --bech val -a) 1000000ukuji --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```

## Başka Validatöre token delege etme

```
kujirad tx staking delegate YOUR_TO_VALOPER_ADDRESS 1000000ukuji --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```


## Burada gördüklerimizi görsel üzerinden görmek istersek;

![alt text](https://i.hizliresim.com/lidocpk.png)


## Redelegate: Stake ettiğiniz tokenleri başka validaötüre delege etme

```
kujirad tx staking redelegate $(kujirad keys show wallet --bech val -a) valoperadresi 1000000ukuji --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```

## Unbond: Stake ettiğiniz tokenleri unstake etme (testnet ve mainnet ağlarında unstake süresi genellikle 14-21gündür.)

```
kujirad tx staking unbond $(kujirad keys show wallet --bech val -a) 1000000ukuji --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y 
```

## Send: Token gönderme

```
kujirad tx bank send wallet cüzdanadresi 1000000ukuji --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y 
```

cüzdanadresi=gönderecek olduğunuz cüzdan adresi


## Aktif olan proposal/oylamaları görme

```
kujirad query gov proposals
```

EVET oyu

```
kujirad tx gov vote 1 yes --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```

HAYIR oyu

```
kujirad tx gov vote 1 no --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```

ÇEKİMSER oyu

```
kujirad tx gov vote 1 abstain --from wallet --chain-id kaiyo-1 --gas-prices 0.1ukuji --gas-adjustment 1.5 --gas auto -y
```

## Indexer Güncelleme

Buradaki kodda kv=dizinleri tutar
null=dizinleri tutmaz. (sunucuda fazla yer kaplamaz)

```
sed -i 's|^indexer *=.*|indexer = "kv"|' $HOME/.kujira/config/config.toml
```

Koddaki kv yerini null yapabilirsiniz. .kujira klasörü başka projede örnek olarak Kyve'da .kyve'dır.


## Pruning (Budama)

Bu kod ile projenin bütün block datalarını sunucunuzda tutmazsınız. Örnek koddaki gibi en sonki 100 block sadece sunucunuzda tutulur.
Testnet projeleri için uygundur. Mainnet Validatörleri için tercih edilmez.


```
sed -i.bak -e 's|^pruning *=.*|pruning = "custom"|; s|^pruning-keep-recent *=.*|pruning-keep-recent = "100"|; s|^pruning-keep-every *=.*|pruning-keep-every = "0"|; s|^pruning-interval *=.*|pruning-interval = "17"|' $HOME/.kujira/config/app.toml
```
Koddaki .kujira klasörünü değiştirin.

## Peer ekleme

```
PEERS="peerleriburayaekleyin"
sed -i 's|^persistent_peers *=.*|persistent_peers = "'$PEERS'"|' $HOME/.kujira/config/config.toml
```
Eğer Node'unuz ağa bağlanmazsa peer eklemeniz gerekebilir. Güncel peerleri discord veya telegram kanallarından bulup koddaki ilgili yere girmeniz gerek. 
Örnek olarak;

```
PEERS="d6f2eee997d108d4fde5683e31d678427376dfce@77.68.27.75:26656,1a781f294b8c30ab0b4e54494359263e9b389ebb@141.94.219.133:11756,ff7a1787ea93a49ece2ee92f601a4c52951278c4@185.119.118.112:2000,09076c7908db88316498cf4cd4702a8d269e0da9@15.235.114.85:26656"
sed -i 's|^persistent_peers *=.*|persistent_peers = "'$PEERS'"|' $HOME/.kujira/config/config.toml
```














