![alt text](https://i.hizliresim.com/20m956g.png)


# Minimum Sistem Gereksinimleri

- **4 CPU**
- **8GB RAM**
- **160GB DISK**
- **Ubuntu 20.04+**

### Gerekli Güncellemeler

```python
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential pkg-config make libssl-dev git wget jq make gcc chrony -y
```


### Go Kurulum ve Versiyon Kontrolü

```python
ver="1.20.5" && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \
source $HOME/.bash_profile
```

### Go Versiyon Kontrolü

```python
go version
```

![alt text](https://i.hizliresim.com/833lfkg.png)

Version: 1.20.5 çıkmalı


```python
git clone https://github.com/dymensionxyz/dymension.git --branch v1.0.2-beta
cd dymension
make install
```

### Dymension Version Kontrol

```python
dymd version --long
```

![alt text](https://i.hizliresim.com/b4mz0a0.png)


- **Moniker yerine validatör isminizi girin**

```python
dymd init <moniker> --chain-id=froopyland_100-1
```


```python
sed -i.bak -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.25udym\"/;" ~/.dymension/config/app.toml
PEERS=e7857b8ed09bd0101af72e30425555efa8f4a242@148.251.177.108:20556
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" $HOME/.dymension/config/config.toml
external_address=$(wget -qO- eth0.me) 
sed -i.bak -e "s/^external_address *=.*/external_address = \"$external_address:26656\"/" $HOME/.dymension/config/config.toml
```

### Pruning ve Indexer Ayarları

```python
pruning="custom"
pruning_keep_recent="100"
pruning_keep_every="0"
pruning_interval="10"
sed -i -e "s/^pruning *=.*/pruning = \"$pruning\"/" $HOME/.dymension/config/app.toml
sed -i -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"$pruning_keep_recent\"/" $HOME/.dymension/config/app.toml
sed -i -e "s/^pruning-keep-every *=.*/pruning-keep-every = \"$pruning_keep_every\"/" $HOME/.dymension/config/app.toml
sed -i -e "s/^pruning-interval *=.*/pruning-interval = \"$pruning_interval\"/" $HOME/.dymension/config/app.toml
indexer="null" && \
sed -i -e "s/^indexer *=.*/indexer = \"$indexer\"/" $HOME/.dymension/config/config.toml
```

### Genesis Dosyası

```python
curl -s https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/dymension/genesis.json > $HOME/.dymension/config/genesis.json
```

### Addrbook Dosyası

```python
curl -s https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/dymension/addrbook.json > $HOME/.dymension/config/addrbook.json
```



### Servis

```python
sudo tee /etc/systemd/system/dymd.service > /dev/null <<EOF
[Unit]
Description=dymd
After=network-online.target

[Service]
User=$USER
ExecStart=$(which dymd) start
Restart=on-failure
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
```

```python
sudo systemctl daemon-reload
sudo systemctl enable dymd
sudo systemctl restart dymd
```


### Log Kontrol

```python
sudo journalctl -u dymd -f --no-hostname -o cat
```

![alt text](https://i.hizliresim.com/7kqpazr.png)


```python
dymd status 2>&1 | jq .SyncInfo
```

![alt text](https://i.hizliresim.com/5e175ph.png)


- **Çıktı false ise nodeunuz senkronizasyon olmuş demektir. Bundan sonra diğer adımlara geçin.**


### Cüzdan Oluşturma 

- **cüzdan ismi wallet olarak girilmiştir. Değiştirmek isterseniz wallet olan yeri değiştirin**

```python
dymd keys add wallet
```

- **Cüzdan import etmek isterseniz**

```python
dymd keys add wallet --recover
```
- **import etmek istediğiniz cüzdanın mnemoniclerini girin**

![alt text](https://i.hizliresim.com/m9phwsn.png)


### Faucet

- **Dymension Discord kanalındaki froopyland-faucet kanalından token isteyin.**

![alt text](https://i.hizliresim.com/sdiw956.png)

### Balance Kontrol

```python
dymd q bank balances $(dymd keys show wallet -a)
```

![alt text](https://i.hizliresim.com/scnbdj9.png)


- **İsterseniz Discord froopyland-faucet kanalında da kontrol edebilirsiniz.**

![alt text](https://i.hizliresim.com/1rxv7he.png)


### Validatör



```python
dymd tx staking create-validator \
--amount 100000000000udym \
--pubkey $(dymd tendermint show-validator) \
--moniker "moniker-isminiz" \
--details "" \
--identity= \
--website="" \
--security-contact="" \
--chain-id froopyland_100-1 \
--commission-rate 0.05 \
--commission-max-rate 0.20 \
--commission-max-change-rate 0.01 \
--min-self-delegation 1 \
--from wallet \
--gas-adjustment 1.4 \
--gas auto \
--gas-prices 0.25udym \
-y
```

- **amount, moniker, details, identity, website ve security-contact için kendi bilgilerinizi girebilirsiniz.**


![alt text](https://i.hizliresim.com/ezvx95d.png)

- **Explorer** **https://explorer.stavr.tech/dymension-testnet/staking**

- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**

- **https://twitter.com/testnetrun**

















