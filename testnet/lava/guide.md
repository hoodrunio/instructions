
![alt text](https://i.hizliresim.com/2gb6pg0.png)

# Minimum Sistem Gereksinimleri

- **4 CPU**
- **8GB RAM**
- **160GB DISK**
- **Ubuntu 20.04+**

## Gerekli Güncellemeler

```python
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential pkg-config libssl-dev git wget jq make gcc chrony -y
```

## Go Kurulum ve Versiyon Kontrolü

```python
ver="1.19" && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \
source $HOME/.bash_profile
```
-** Go Versiyon Kontrolü**

```python
go version
```
Version: 1.19 çıkmalı

![alt text](https://i.hizliresim.com/hi4747o.png)


## Yapılandırma

![alt text](https://i.hizliresim.com/ese71dl.png)


- **İlk Yapılandırma**

```python
git clone https://github.com/lavanet/lava
cd lava
git checkout v0.3.0 
make install
```

## Versiyon Güncelleme

```python
rm -rf lava
git clone https://github.com/lavanet/lava
cd lava
git checkout <versiyon-numarasını-girin> 
make install
```

- **Versiyon Kontrol**

```python
lavad version
```

## Moniker ve Chain Belirleme

```python
lavad init <moniker-adınız> --chain-id lava-testnet-1
lavad config chain-id lava-testnet-1
```
<moniker-adınız> yerine validatör isminizi girin

![alt text](https://i.hizliresim.com/qo7w6wh.png)

## Genesis Dosyası

```python
wget -O ~/.lava/config/genesis.json https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/lava/genesis.json
```

## Addrbook Dosyası

```python
wget -O $HOME/.lava/config/addrbook.json https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/lava/addrbook.json
```

## Servis Dosyası Düzenleme

```python
sudo tee /etc/systemd/system/lavad.service > /dev/null <<EOF
[Unit]
Description=lava
After=network-online.target

[Service]
User=$USER
ExecStart=$(which lavad) start
Restart=on-failure
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
```


## Peers Ayarlama

```python
PEERS="c8e034a7b1ae22e0a5aca0c85d0590c1e5da0dc3@3.65.2.114:26656,15480dd0fcccdf317d11993ff4c5d0098bc48a47@78.46.106.75:11656,a5e61061417d9d4b51bbfa2a66042cfce7047f5d@195.201.197.4:14656,31478ee0c0521c7cfb3312b86ef490936b5ceb80@65.109.92.240:197,6171a52cf0ffc1706409d2dcec56c1db81c86aae@176.103.222.17:26656,5e068fccd370b2f2e5ab4240a304323af6385f1f@172.93.110.154:27656,8c4a947fea73d844fcf573f749046817db2e7ed5@207.180.206.158:44656,2c2410774b668e4ff208cc37a4b229f27a494cb5@81.196.253.241:47656,dd7f68ed87765006fa50d45fb7514afc27a53b6b@65.108.152.37:26656,550d7467d6a442da11d9772b804252a8dfdca27e@91.107.243.149:26656,edac44f96d37591545db2ae04d19d61c1c64a9de@217.76.57.34:26656,ef1b3374ca00c338de50d51fc41ca317488156eb@207.244.245.41:26656,2c419186cd96b59fe8b3307c54c27d6805414aba@65.108.8.28:60756,9383be92dbd468a28955fff34753c1df6e0fa638@92.204.242.211:26656,80ab0928eca4cb414a78103a8ca011e6734e7064@194.163.162.12:26656,8b154033143fdedf4835dfc7b030c7d781bfd54e@195.201.219.227:26656,5017e35f6b9ad10b329d96bcbcac48bfdc0645e4@143.110.237.31:26656,f7c1a998b8ef7cae7e38b0eff64d96206924e957@45.84.138.167:26656,f441a05060e55323b3d6757e353eba149fd728d8@51.89.149.182:26656,5d24eb95fa5974af7bb03e370382537251ab6328@95.217.158.66:26656,9872ab6a76199fcbeca1f7f791755e726aa97686@116.202.165.116:11656,d87537a4c8bf2be6ebbd8c58987737f5840a3b0c@194.195.87.106:26656,34271a6f82d755777a3db02be39e575bf4ebd415@65.109.30.197:28656,e593c7a9ca61f5616119d6beb5bd8ef5dd28d62d@34.246.190.1:26656,13a9209a4d08803a3becac57de8eb02dd51f8f41@65.109.23.114:19956,f9190a58670c07f8202abfd9b5b14187b18d755b@144.76.97.251:27656,381c5e431a108fdee2ef35abca5d8ee6421bb898@65.109.104.118:61256,dfa93668152cb6b3a822c987f9c22110a1c2f314@178.18.255.221:26656,ed295c3ece2ded17ea4007a680154db83abeca13@95.217.114.220:13656,35f045092f9c51ab743eec194438b91ecf8ce69e@65.109.116.22:11134,c19965fe8a1ea3391d61d09cf589bca0781d29fd@162.19.217.52:26656,0561fed6e88f2167979e379436529861527d859d@65.109.92.148:61256,95a490b4cde4c5311f7d58c3e47ee41fa039ddf4@144.76.27.79:60756,b1ba2e79e71d351049d5f805b956726684308687@38.242.152.80:26656,d5f51ff7adf797e7e4be5f303e75686f6d277886@213.239.207.165:29556,1a18bdd0c259d604cda023a5e03eba2a25f5c045@94.19.249.187:27656,f642b376722d6ce104ffd4c204e78ffe811e16c3@5.75.230.221:26656,a0476bc75ad2ade9ce8a6b2cd41ef646d3a2e3ee@85.10.193.246:28656,24a2bb2d06343b0f74ed0a6dc1d409ce0d996451@188.40.98.169:27656,149f9f017344ce9cebb637baa7cab57a28f3a8c3@86.111.48.159:26656,4dbe5ebf1505f472d852cf7732343ceb899d51db@95.217.57.232:60656,6ba3b6ec03839afffa64c83e18ff80a681f4968d@65.108.194.40:21756,07c557b393b235a7b004a4a32831e54092dc24a0@91.107.147.250:26656,f22ea1e7b6d31966259e99177d714cffde27c4bf@152.32.211.182:26656,e4ebf07ed08ff8ee26a9a903d63ad34d1f59393e@95.217.35.186:56656,f0758765ef0350d5cbbdeebf0b8e84f76e21c46d@54.221.204.97:26656,3a445bfdbe2d0c8ee82461633aa3af31bc2b4dc0@3.252.219.158:26656,bbdb9ebdcc2ea89eca1091da8e54da0045373817@65.108.42.97:26656,35186117a37b22fa3b431c27566bc8bd44dcf6e3@89.116.29.11:26656"
sed -i 's|^persistent_peers *=.*|persistent_peers = "'$PEERS'"|' $HOME/.lava/config/config.toml
```


## Pruning (budama) isteğe bağlı

```python
pruning="custom" && \
pruning_keep_recent="100" && \
pruning_keep_every="0" && \
pruning_interval="10" && \
sed -i -e "s/^pruning *=.*/pruning = \"$pruning\"/" ~/.lava/config/app.toml && \
sed -i -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"$pruning_keep_recent\"/" ~/.lava/config/app.toml && \
sed -i -e "s/^pruning-keep-every *=.*/pruning-keep-every = \"$pruning_keep_every\"/" ~/.lava/config/app.toml && \
sed -i -e "s/^pruning-interval *=.*/pruning-interval = \"$pruning_interval\"/" ~/.lava/config/app.toml
```

## Indexer düzenleme (isteğe bağlı)

```python
indexer="null" && \
sed -i -e "s/^indexer *=.*/indexer = \"$indexer\"/" $HOME/.lava/config/config.toml
```


## Snapshot (isteğe bağlı)

```python
sudo systemctl stop lavad
cp $HOME/.lava/data/priv_validator_state.json $HOME/.lava/priv_validator_state.json.backup 
lavad tendermint unsafe-reset-all --home $HOME/.lava --keep-addr-book 
curl https://sync.stakerun.com/testnet/lava/lava-testnet-1_2023-04-19.tar | tar -xvf - -C $HOME/.lava/data
mv $HOME/.lava/priv_validator_state.json.backup $HOME/.lava/data/priv_validator_state.json 
```

## Node Başlatma

```python
sudo systemctl daemon-reload
sudo systemctl enable lavad
```

## Log Kontrolü

```python
sudo systemctl restart lavad && sudo journalctl -u lavad -f -o cat
```

## Senkronizasyon Kontrolü (çıktı false ise senkronizasyon olmuştur)

```python
lavad status 2>&1 | jq .SyncInfo
```

## Cüzdan Oluşturma veya İmport Etme

```python
lavad keys add wallet
```

- **Eğer kendi cüzdanınızı import etmek isterseniz**

```python
lavad keys add wallet --recover
```


## Cüzdan Listesi

```python
lavad  keys list
```


## Faucetten Token İsteme

#Lava Discord Faucet kanalından $request <cüzdan-adresiniz> ile token isteyin

**Lava Discord**  **https://discord.gg/fmAtVh5MJG**

## Bakiye Kontrolü

```python
lavad query bank balances cüzdanadresi
```



## Validatör Oluşturma

```python
lavad tx staking create-validator \
  --amount 1000000ulava \
  --from wallet \
  --commission-max-change-rate "0.1" \
  --commission-max-rate "0.2" \
  --commission-rate "0.1" \
  --min-self-delegation "1" \
  --pubkey  $(lavad tendermint show-validator) \
  --moniker <moniker-adınız> \
  --chain-id lava-testnet-1 \
  --identity="" \
  --details="" \
  --website="" -y
```

## Validatör Ödüllerini Çekme

```python
lavad tx distribution withdraw-rewards <valoper-adresiniz> --from $LAVA_WALLET --commission --chain-id $LAVA_CHAIN --gas auto --fees 4000ulava
```

## Başka Cüzdana Token Gönderme

```python
lavad tx bank send <cüzdan-adresiniz> <gönderilecek-cüzdan-adresi> 500000000ulava --chain-id $LAVA_CHAIN --gas auto --fees 4000ulava
```

## Sunucudan Lava'yı Silmek İçin

```python
sudo systemctl stop lavad
sudo systemctl disable lavad
sudo rm /etc/systemd/system/lava* -rf
sudo rm $(which lavad) -rf
sudo rm $HOME/.lavad* -rf
sudo rm $HOME/lavad -rf
sed -i '/LAVA_/d' ~/.bash_profile
rm -rf lava 
rm -rf .lava
```

## Keplr Wallet'a Lava Testnet Ağı Ekleme

- **https://docs.lavanet.xyz/wallet/** sitesinde ADD LAVA TO KEPLR butonuna basıp çıkan Pop-up'a Approve Diyerek Ekleyebilirsiniz

![alt text](https://i.hizliresim.com/dbe5a32.png)

- **Lava Cüzdan Mnemoniclerinizi Keplr Wallet'a İmport Ederek Cüzdanınızı Keplr Wallet'ta Görebilirsiniz**

![alt text](https://i.hizliresim.com/rxrgzjs.png)

- **Explorer** - **https://lava.explorers.guru/validators**


