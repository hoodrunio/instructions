![alt text](https://i.hizliresim.com/9w1u7aw.png)



## Eski Sunucudan Veri Yedekleme

```python
sudo systemctl stop da-light-client
```

```python
sudo systemctl stop sequencer
```

```python
sudo systemctl stop relayer
```

```python
sudo systemctl disable da-light-client
sudo systemctl disable sequencer
sudo systemctl disable relayer
```

```python
cd $HOME
mkdir -p $HOME/_tar
tar cvf $HOME/_tar/roller_backup.tar ./.roller
```

```python
cd _tar
$(which python3) -m http.server 8150
```


![alt text](https://i.hizliresim.com/tbi26en.png)

CTRL-C vb. ile durdurmayın. Durdurursanız bağlantı kesilir. (Yeni sunucuya taşıma işlemi bitince durdurun.)


## Yeni Sunucuya Aktarım

Backup İndirme 

```python
cd $HOME
wget <eski-sunucunun-ipsi>:8150/roller_backup.tar
```

![alt text](https://i.hizliresim.com/ibqvjmi.png)



```python
tar xvf roller_backup.tar
```

Roller İkili Dosyaları

```python
curl -L https://dymensionxyz.github.io/roller/install.sh | bash
```

Service Oluşturma (eğer roller run ile kuracaksanız en aşağıya bakın)

```python
tee $HOME/da-light-client.service > /dev/null <<EOF
[Unit]
Description=da-light-client
After=network-online.target
[Service]
User=$USER
ExecStart=/usr/local/bin/roller da-light-client start
Restart=on-failure
RestartSec=10
LimitNOFILE=65535
[Install]
WantedBy=multi-user.target
EOF
```


```python
tee $HOME/sequencer.service > /dev/null <<EOF
[Unit]
Description=sequencer
After=network-online.target
[Service]
User=$USER
ExecStart=/usr/local/bin/roller sequencer start
Restart=on-failure
RestartSec=10
LimitNOFILE=65535
[Install]
WantedBy=multi-user.target
EOF
```


```python
tee $HOME/relayer.service > /dev/null <<EOF
[Unit]
Description=relayer
After=network-online.target
[Service]
User=$USER
ExecStart=/usr/local/bin/roller relayer start
Restart=on-failure
RestartSec=10
LimitNOFILE=65535
[Install]
WantedBy=multi-user.target
EOF
```

```python
sudo mv $HOME/da-light-client.service /etc/systemd/system/
sudo mv $HOME/sequencer.service /etc/systemd/system/
sudo mv $HOME/relayer.service /etc/systemd/system/
```

```python
sudo systemctl enable da-light-client
sudo systemctl enable sequencer
sudo systemctl enable relayer
```

```python
sudo systemctl daemon-reload
```

Sistem Başlatma

```python
sudo systemctl start da-light-client
sudo systemctl start sequencer
sudo systemctl start relayer
```

Kontrol

```python
sudo systemctl status da-light-client
sudo systemctl status sequencer
sudo systemctl status relayer
```


Hepsinin çıktısı `active (running)` olmalıdır.



Loglar

```python
tail -n 100 -f $HOME/.roller/da-light-node/light_client.log
```

```python
tail -n 100 -f $HOME/.roller/rollapp/rollapp.log
```

```python
tail -n 100 -f $HOME/.roller/relayer/relayer.log
```


## Roller Run

Taşıma işleminden sonra;

```python
curl -L https://dymensionxyz.github.io/roller/install.sh | bash
```

```python
roller migrate
```

```python
screen -S roller
```

```python
roller run
```

- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**





