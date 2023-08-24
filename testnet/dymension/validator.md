![alt text](https://i.hizliresim.com/20m956g.png)

# Hatırlatma
- **Validatör teşviği şu an Froopyland Validators rolü olanlar için geçerli. Makalede bu sayının artırılacağı yazıyor.
Validatör ile Roller farklı. İkisini kurmak zorunda değilsiniz. Fakat Roller'i RollApp Fam rolünüz varsa kurun. Eğer rolünüz yoksa kurulum yaptıktan sonra Discord'daki #share-your-rollapp kanalına kanıt olarak gönderin. Makalenin en altında yazıyor.**

- **Makale** **https://medium.com/@dymension/froopyland-is-live-8bf21e9d7046**

# Minimum Sistem Gereksinimleri

- **4 CPU**
- **8GB RAM**
- **160GB DISK**
- **Ubuntu 20.04+**

### Gerekli Güncellemeler

```python
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential pkg-config libssl-dev git wget jq make gcc chrony -y
```


### Go Kurulumu

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
PEERS=94b63fddfc78230f51aeb7ac34b9fb86bd042a77@46.4.53.94:30585,e28bf506aaba23c890e9d6cd5cf64b8e627b7e12@80.240.29.76:26656,997a654595c4347a1fc5f35e35e3953f549cb91b@46.4.23.42:47656,690f91de88ecfa31dd7aee9beb5db27203da8fed@88.99.143.105:36656,29e66c8a25a17a380c9c31feb3d2c3c83376a04c@162.19.31.150:55696,319d2caf33917d96df33fab78aef0281bf61c13d@95.216.218.120:33656,3943ac701aed59f13ac2d65b80eaa6951b17bfcb@65.108.132.239:26656,c81b68472cad6ce835adf829134c0c4ee68fd962@65.109.106.214:17656,2f379938cccf2c14fe6eb255dd793433f39763d8@207.180.213.207:26656,5e4751f8f44dd86a1e10144822a8ca8cbb3caca5@65.109.65.163:21456,cb120ed9625771d57e06f8d449cb10ab99a58225@57.128.114.155:26656,ab32d488a060cbf8faa5fd104e63599c31340ace@138.68.159.100:26656,bebc199e07b42f9190486f6ea41a610b417a2215@178.62.64.153:26656,c1158e056f90b0ffeee942afad6e4cb052c54b75@176.9.48.38:26656,a12fc76e970e72d5b9468d05ce1c14308d39070b@57.128.192.23:26656,05d4f45e4f935ea2ad44c29b64c22a9337fa3192@65.108.206.118:60756,f6b1c4feeba48d9a87e75ab1df8b9cc6c6ec034e@185.242.112.130:26656,139340424dddf85e54e0a54179d06875013e1e39@161.97.74.88:56656,1e92b79a713b18dffd4e075ddfa1dab87dd215a9@70.34.197.147:26656,23a2d4a1caae25b881b4bf555b6a7217e47424e3@75.119.151.115:26656,6f05dde69ea20422a9f3deb3e367656d8e61a790@116.202.227.117:14656,4b6475a413379d086abf3cd27e06fd5fa4a51651@38.146.3.200:20556,fa21ae6d1a74e94b8088074210f7a2f5b22c000c@149.102.136.149:26656,0ab6d644be1b0ef088deec4664453c4f8431325d@148.113.17.55:26666,138009ae8a3435eab5df2d58844239077c83c92a@161.97.180.20:16656,83d1ef7c305c315211f7780a335f0076f17e0118@135.181.73.170:25156,81251f5685420786ee0af8230c8d46692dd80dfc@195.14.6.2:26656,5342f6f59c7b81b5ea3bef8cd9d6ad224b8eb473@95.217.176.55:26656,56bb29329b8f883804da3168d4f21cccf150a67d@217.160.39.214:26646,1dddd539399bbc4c1b6dd884aa8b70e05dc1d138@136.38.55.33:26656,83c14001596a0da606c7a1dbe174e57f510f2b67@62.171.176.118:26656,51b6427668eda91cb925f8402ced74e2403805f6@65.109.92.240:17086,d77dbfb784b123a6f45676d9ab21658c629d4a0f@109.123.245.118:26656,ab80b1f623c666134cfec3d48acb5e4b2f7680f9@142.132.146.185:26656,37823f1d24cf2375168c21214a6da1d2ba0b212f@135.181.180.230:36656,b523f13c6c86ca42b43f0dfde7db7ab41399b8b2@158.220.89.86:26666,83433e3a264a81b7e6c9ead46d259d0d861b3afa@135.181.165.80:26656,88fdaf5ff074dc2010ccb0416e421f3819201eb6@176.9.98.24:30586,f5af70911de80245df03eb93b671b7533e40dd8a@65.109.92.83:15656,07cf171497e6a9e4cdd8bfb5192ec273f84b39d3@167.235.56.214:26656,aeb87b9b1a351e1645671f664a18688ef52632cf@135.181.84.5:33656,7a08de51736a6b09d2844a1de61c247f8c956f54@5.188.158.110:26656,51fa766c4fc35016adfcac146131cacb37586a1c@95.216.145.120:26656,f59c1497f7271d599a08a4881374c211ee1d3df9@65.109.231.151:26656,81e20b5632114bd95460d188a30ddbcddf38fc4a@75.119.151.217:26656,134f6fdbfccb659e8626438b48e04f55cd271c0e@161.97.132.167:16656,a4767beb8c6f14711f05c6cd1b7fc0f5c37de792@78.46.103.246:56656,7803c814796b31c4c19ee3ecc510b9c7f9ceefdf@65.109.60.227:26656,e04d9bf3e8c4b4f2c04966ddfe8e1d2cbaded7d3@65.109.233.55:26656,2c767245f7cf9f09d5769801db52f26b602628f1@206.116.75.69:26656,935ae6c9589a1218f2661efc2b7a7bff6982ad18@65.21.254.222:26656,62a35fa4be132507ed313dceae077f8ad636bd9e@142.132.151.99:15658,324a73f4f3b3a54496ec570bc73245895a0aae80@185.193.67.136:16656,77bc6610dfba072e206ccbb3e30237b54dce89d7@65.109.63.176:36656,0b1cd2e2e8ca843c293afd2caeb456a345a54793@146.190.167.238:26656,5cb4e92c9e147408e3b02099bb0150c0ca368860@146.19.24.101:26646,9dfceb302e83eecd9b268e643ba8dcd89ff71e16@185.249.225.160:33656,1fda06f90e45c2cc99d97b47ee0dca52f01fb192@91.107.215.74:26656,d7feaab13c06e39c886035385e78c9a0b3f75605@88.99.56.200:16656,11e6eccbc081819d94676cce3d425d96ee68adf3@95.216.7.136:09656,484dad4e5c3c3f69493452bec901bb8fed68b3d5@149.102.149.186:26656,6d070ab7786130d310f0bdc6a64b986051a0e9ed@65.109.90.162:28656,9c8da76f66fbedc2267aa0d7e9bdcca51e010da4@207.180.250.156:14656,eb7a1722228f84163fba41cdb725fe3838dcc798@65.109.48.181:31656,236b71988898dff63cef139f83a64f5fbfd9d8d7@135.181.18.112:55696,e7857b8ed09bd0101af72e30425555efa8f4a242@148.251.177.108:20556,c6329371271c247d35454862014dfd6ff5e3b680@65.108.141.109:49656,27a9069a79833df98adc4d2407d1e676fadf5c36@195.3.220.169:23466,febc198f5086aed9bb578044c78cd9cfaf9023ac@65.108.229.93:29656,b5395de25e0a6c07e431dc0f4ea2088732e81e17@157.90.168.136:26656,fdcd8b1b4e55bdbb97d0fc57a65c24950bb26337@84.203.117.234:26656,8030a90d8633376422fe225d980854fb0127d2b7@5.75.160.247:26656,1b7620ee46f116bd311bc4295b29208e693d3861@5.75.183.248:26656,c882fff7cbd87e2e3296298bcb2e76e5fd0c5182@38.242.208.162:26656,53bce1af5605a40cb761409a8e78bc92533db4cf@135.181.46.127:26656,7d8b711e40074f724d794f7f1b356cbbd827bcde@81.0.218.193:33656,84f10cefebee4d2e9e2407223d62a9384cac7f47@65.108.248.89:26656,f09a1671de9abc28c0cc409491f0d1561d01641d@34.213.183.119:26656,5d19b0bbae885d10adc2db103ef4f56b28d8a0bb@65.108.73.124:29656,d5644f3c6c823c1339995959216ebb7a25d24498@45.14.194.130:33656,77d418674cb1cc7ae734ac8fbae0b5962649b502@209.38.248.95:26656,be981c8b28ee15090238d09e8841d3f728d7291a@159.69.13.145:26656,63dbf7cf2f801938f3b655295fd347409474a08a@5.180.186.25:26656,2171722b6bb83401a89a1918b8cf45b3b322ad98@128.140.123.93:16656,ca8544ad2738a0fa5a8e318b08b90216e7b80c9d@5.189.185.27:26656,dc088646e0ae9123c6e322412f0e883d42e04435@185.188.249.62:33656,a41e06d38266045c47667684abc8856ac137ac63@185.215.180.177:11656,d2daa5d7e755ca7a61f627e71e9897f6960f8a90@34.125.175.3:26656,4c0aa61fb83354fd504df5d8384e7f1eb5279e69@194.163.159.85:28656,9ff936fe58baf659f5cb600fcc94512d2b9f9088@195.3.223.182:17056,4fd873d15ae8450a46f8a6fea15d0bb699ce66c6@65.21.91.160:27655,804f4a3cb2005dac58c94d79002e10913477538b@37.27.0.249:26656,ce32755770a11ad39398ca40402437e2ce6d44df@95.217.23.37:33656,7bee70fa0e0cbf8e3ad795e92d24348433564ff8@143.198.229.74:26656,c8e27fdcd29c200b31574689a7c691b7ff8753cc@51.15.212.195:26656,0f9098bc829d53a71d82fc5037ed176adedb43b8@161.97.173.174:26656,32ed437d261d7b38ccf8494c9ac06f0588a9bfbe@207.180.199.130:36656,11c7c7b944cbaa8ba949a86de6ac9f61b14b4a2e@185.219.142.212:26656,99eb8168866a39de46aa27dabefb31b4f0342221@89.116.25.6:26656,f85a4dd43cc31b2ef7363667fcfcf2c5cd25ef04@88.99.164.158:17086,a71974c8f2527d497f967b38bf7927f38069df37@184.174.34.145:26656,fdc59183024985c6f3d3a8b0317c6f6f61c68037@84.54.23.111:26656,6496dac7244d12f697ee74688daf7e5b8dd2c869@144.91.65.13:26696,a9aa50bdc3fd71c6432a535e8416b53aa7feafc9@161.97.130.203:26656,c8c34a07ebe7b98b21fd74e4d31293e92afda119@109.123.229.180:26656,22579807ff06a1816630cc2319cc06a2b48e81a3@65.109.82.112:2446,b343fb4e18946152346d1849a4a45e8c25f1a006@65.108.250.185:26656,d4a1907c52392bbd93a74489fc949f46b1224ff4@45.88.188.251:26656,7eaeff8f270d4117ef299854792f3396b92b25c1@65.108.87.61:11656,997fc8f99400482a1e411da7c33d25148e5b6e31@168.119.114.206:26656,4a1a761465438e4a74c0dfd0aef2510fa0d66489@144.126.148.159:11656,60b254fbc8fb7f02cfdc1676b1624e14fbe31cb6@190.2.137.108:26666,e1b8927cf39b22a04d56084accdb8e6afad34d79@65.109.104.171:27656,aa755789a28dd8701ad1cd447866a2c029412199@144.76.18.199:26656,96408cb2426a8623391a9ea5a916c9e53f391394@81.0.248.235:26656,ca30e70ce5f4882273ca503a02ce828569747741@45.67.217.22:26656,479d7e039fa546a0c55da94246809049bf53c5e5@193.34.213.4:26656,2af89d272e29f7a3f64ad9db1a65791cedc6acc6@173.249.40.104:16656,5e23aeac8c562c814097a72246680370648a464c@38.242.232.231:26656,025ddeb235aef1e8ec4bbc4d5ef93a8103b1ff32@5.75.141.107:26656,e55fc80ff9337e478a65cfe48d3049a75ffbc7b0@65.108.81.196:11656,1006a349e9816d6bdc49deb5a2d87bc3eca0f209@194.163.130.254:11656,55730501bda0d20bd0e88163aa948c26a2806367@89.163.157.64:36656,253831e262a06baa21b857eac6439b691136be36@65.21.148.160:33656,da0d2e4a0b5983fb8c49270f36d2117d4c2869eb@164.90.192.111:26656
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

- **Eğer Validatör Node ve Roller'i aynı sunucuya kuracaksanız aşağıdaki port değiştirme kodunu girin. Eğer farklı sunucularda kuracaksanız girmenize gerek yok. Bir alttaki kodlardan devam edin.**

```python
sed -i.bak -e "s%^proxy_app = \"tcp://127.0.0.1:26658\"%proxy_app = \"tcp://127.0.0.1:28658\"%; s%^laddr = \"tcp://127.0.0.1:26657\"%laddr = \"tcp://127.0.0.1:28657\"%; s%^pprof_laddr = \"localhost:6060\"%pprof_laddr = \"localhost:6260\"%; s%^laddr = \"tcp://0.0.0.0:26656\"%laddr = \"tcp://0.0.0.0:28656\"%; s%^prometheus_listen_addr = \":26660\"%prometheus_listen_addr = \":28660\"%" $HOME/.dymension/config/config.toml && sed -i.bak -e "s%^address = \"0.0.0.0:9090\"%address = \"0.0.0.0:9290\"%; s%^address = \"0.0.0.0:9091\"%address = \"0.0.0.0:9291\"%; s%^address = \"tcp://0.0.0.0:1317\"%address = \"tcp://0.0.0.0:1517\"%; s%^address = \"0.0.0.0:8545\"%address = \"0.0.0.0:8745\"%; s%^ws-address = \"0.0.0.0:8546\"%ws-address = \"0.0.0.0:8746\"%; s%^address = \"127.0.0.1:8545\"%address = \"127.0.0.1:8745\"%; s%^ws-address = \"127.0.0.1:8546\"%ws-address = \"127.0.0.1:8746\"%" $HOME/.dymension/config/app.toml && sed -i.bak -e "s%^node = \"tcp://localhost:26657\"%node = \"tcp://localhost:28657\"%" $HOME/.dymension/config/client.toml 
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

















