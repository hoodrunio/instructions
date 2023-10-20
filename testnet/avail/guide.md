
![alt text](https://i.hizliresim.com/785b3ek.png)

# Minimum Sistem Gereksinimleri

- **2 CPU**
- **4GB RAM**
- **20-40GB DISK**
- **Ubuntu 20.04++**

# Önemli

**Form ve Detaylar:** **https://x.com/AvailProject/status/1715008696835600451?s=20**

**Telemetry:** **https://telemetry.avail.tools/**


```python
sudo apt update && sudo apt upgrade -y
```

```python
sudo apt install make clang pkg-config libssl-dev build-essential git screen protobuf-compiler -y
```

```python
curl https://sh.rustup.rs -sSf | sh
```

```python
source $HOME/.cargo/env
```

```python
rustup update nightly
```

```python
rustup target add wasm32-unknown-unknown --toolchain nightly
```

```python
git clone https://github.com/availproject/avail.git
```

```python
screen -S avail
```
```python
cd avail
```

```python
cargo build --release -p data-avail
```

```python
mkdir -p output
```

```python
cargo run --locked --release -- --chain kate -d ./output
```

```python
sudo touch /etc/systemd/system/availd.service
```

```python
sudo nano /etc/systemd/system/availd.service
```

Aşağıdaki kodda `monikeradiniz` olan yere validatör adınızı girin. Kodu yapıştırdıktan sonra `CTRL X-Y Enter` ile çıkın.

```python
[Unit]
Description=Avail Validator
After=network.target
StartLimitIntervalSec=0
[Service]
User=root
ExecStart= /root/avail/target/release/data-avail --base-path `pwd`/data --chain kate --name "monikeradiniz"
Restart=always
RestartSec=120
[Install]
WantedBy=multi-user.target
```

```python
sudo systemctl enable availd.service
```
![alt text](https://i.hizliresim.com/d1u63ux.png)


```python
sudo systemctl start availd.service
```

```python
sudo systemctl status availd.service
```
![alt text](https://i.hizliresim.com/ag4qsve.png)


```python
journalctl -f -u availd
```

![alt text](https://i.hizliresim.com/aqo67ho.png)


System Durdurma

```python
sudo systemctl stop availd.service
```


- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**

