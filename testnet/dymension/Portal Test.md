![alt text](https://i.hizliresim.com/ntf58cb.png)

## Faucet

DYM token fauceti için Discord froopyland-faucet (rollapp fam rollerine açık) kanalına aşağıdaki kodda dym cüzdan adresinizi yazarak faucet isteyin.

```python
$request cüzdan-adresiniz
```

![alt text](https://i.hizliresim.com/sukq0ev.png)

`TNR-NDST-CRN` tokenlar için aşağıdaki kodlarla kendi dym cüzdanınıza tokanları froopyland-faucet kanalından talep edin.

```python
$request  cüzdan-adresiniz mytestnetrunrollapp_3448-1
```

```python
$request  cüzdan-adresiniz corenode_1303285-1
```

```python
$request  cüzdan-adresiniz nodeist_6452664-1
```

![alt text](https://i.hizliresim.com/6nq1c2c.png)


## IBC Transfer

### Keplr -> Metamask İşlemleri

Keplr Cüzdanınızı Dymension Portal sitesine bağladıktan sonra IBC Transfer sekmesinde Destination Chain Metamask olarak `TestNetRun-Nodeist-CoreNode` chainlerini seçerek bu chainlere DYM token 
transferleri yapın. Transfer işlemini gerçekleştirmek için Keplr Wallet eklentisinden transfer onayını verin.

![alt text](https://i.hizliresim.com/tmpbkvg.png)

DYM token transfer işlemlerinden sonra Keplr cüzdanınızda bulunan `TNR-NDST-CRN` tokenları Metamasktaki `TestNetRun-Nodeist-CoreNode` chainlerine gönderin.

![alt text](https://i.hizliresim.com/dxeazxf.png)


### Metamask -> Keplr İşlemleri

Bu sefer işlemlerin tersini yapmak için Source chain -> Metemask, Destination Chain -> Keplr olarak seçin.
Bu işlemi yaparken `TestNetRun-Nodeist-CoreNode` chainlerinin her biri için metamask chain ekleme işlemini onaylayın.

![alt text](https://i.hizliresim.com/n9jdb1l.png)


### Metamask -> Metamask İşlemleri

Metamask `TestNetRun-Nodeist-CoreNode` chainlerinden birini seçtikten sonra Destination Chain -> Metemask olarak ayarlayıp burada RollApp olarak yine `TestNetRun-Nodeist-CoreNode` chainlerinden 
birini seçerek DYM token yada `TNR-NDST-CRN` tokenlarından chainler arası transfer yapabilirsiniz.


![alt text](https://i.hizliresim.com/s0tly3t.png)


## Stake

Stake işlemi için `TestNetRun-Nodeist-CoreNode` RollApp sayfalarındaki (linkler aşağıda) Staking bölümüne gelerek hub_sequencer'a her RollApp'in kendi tokeninden Delegate sekmesinden stake edin.

- **TestNetRun** **https://portal.dymension.xyz/rollapp/mytestnetrunrollapp_3448-1**

- **CoreNode** **https://portal.dymension.xyz/rollapp/corenode_1303285-1**

- **Nodeist** **https://portal.dymension.xyz/rollapp/nodeist_6452664-1**


![alt text](https://i.hizliresim.com/m4bv8ro.png)

