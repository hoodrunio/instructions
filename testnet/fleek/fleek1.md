
![alt text](https://i.hizliresim.com/d4bcrd1.png)

# Minimum Sistem Gereksinimleri

- **4 CPU**
- **32GB RAM**
- **20GB DISK**
- **Ubuntu 22.04+**


```python
sudo apt update && sudo apt upgrade -y
sudo apt install curl tar wget clang pkg-config libssl-dev jq build-essential bsdmainutils git make ncdu gcc git jq chrony liblz4-tool -y
```


```python
adduser lgtn
```

![alt text](https://i.hizliresim.com/pm59nrt.png)

Burada lgtn kullanıcısı için şifre belirleyin ve unutmayın.


```python
usermod -aG sudo lgtn
```


```python
su lgtn
```


```python
cd /home/lgtn
```

![alt text](https://i.hizliresim.com/3aet5uw.png)


```python
curl https://get.fleek.network | bash
```

Rust ile birlikte kurulum uzun sürebilir.

![alt text](https://i.hizliresim.com/rbc2oag.png)

Enter dedikten sonra Node Public Key Consensus Public Key'i kaydedin. SFTP bağlantısı ile consensus.pem dosyasını da bilgisayarınıza aktarın. (ne olur ne olmaz)

![alt text](https://i.hizliresim.com/tdgxv7a.png)

Kurulum bittikten sonra tekrar sistemi başlatın.

```python
sudo systemctl start lightning.service
```

# Mint

Metamask Eklentisine aşağıdaki Fleek ağını ekleyin.

```python
Network Name: Fleek Network
RPC URL: https://rpc.testnet.fleek.network/rpc/v0
Chain ID: 59330
Currency symbol: tFLK
```

- **Faucet:** **https://faucet.testnet.fleek.network/**

Faucet sitesine metamask ile bağlantıktan sonra tokenları mint edin.

![alt text](https://i.hizliresim.com/nhfpdvn.png)



# Stake

Stake için aynı sitede `Stake FLK` butonuna bastıktan sonra sunucu üzerinden aldığınız `Node Public Key` `Consensus Public Key` ve `Sunucu IP`'nizi girip Metamask üzerinden onay verin.

![alt text](https://i.hizliresim.com/8v6jeie.png)

İşlem başarılı ise,


![alt text](https://i.hizliresim.com/lkue9aq.png)


# Gerekli Kontroller

```python
curl https://get.fleek.network/node_details | bash
```

![alt text](https://i.hizliresim.com/b9lwp8l.png)

```python
curl https://get.fleek.network/healthcheck | bash
```

![alt text](https://i.hizliresim.com/qhuzpqm.png)


## Log Kontrol

```python
tail -f /var/log/lightning/output.log
```

```python
tail -f /var/log/lightning/diagnostic.log
```

- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**




