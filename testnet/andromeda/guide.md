

```python
sudo apt update && sudo apt upgrade -y
```

```python
sudo apt install curl tar wget clang pkg-config libssl-dev jq build-essential bsdmainutils git make ncdu gcc git jq chrony liblz4-tool -y
```


```python
ver="1.20.5" && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \
source $HOME/.bash_profile
```

Go Version Control

```python
go version
```


```python
cd $HOME
git clone https://github.com/andromedaprotocol/andromedad.git 
cd andromedad 
git checkout galileo-3-v1.1.0-beta1 
make install
```


```python
andromedad init MonikerName --chain-id galileo-3
andromedad config chain-id galileo-3
```


```python
wget -O $HOME/.andromedad/config/genesis.json "https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/andromeda/genesis.json"
```

```python
wget -O $HOME/.andromedad/config/addrbook.json "https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/andromeda/addrbook.json"
```

```python
peers="20248068f368f5d1eda74646d2bfd1fcdaffb3e1@89.58.59.75:60656,f81993a28a2cf0111dfa8b1943daba4691ef3825@45.142.214.163:26656,7ac17e470c16814be55aa02a1611b23a3fba3097@75.119.141.16:26656,064497a6f023caa1e5f1482425576540c22476fb@65.21.133.114:56656"
sed -i -e "s|^persistent_peers *=.*|persistent_peers = \"$peers\"|" $HOME/.andromedad/config/config.toml
```

```python
sed -i.bak -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.0025uandr\"/;" ~/.andromedad/config/app.toml
```

```python
sudo tee /etc/systemd/system/andromedad.service > /dev/null <<EOF
[Unit]
Description=andromedad
After=network-online.target

[Service]
User=$USER
ExecStart=$(which andromedad) start
Restart=on-failure
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
```

Pruning (optional)

```python
pruning="custom"
pruning_keep_recent="100"
pruning_keep_every="0"
pruning_interval="10"
sed -i -e "s/^pruning *=.*/pruning = \"$pruning\"/" $HOME/.andromedad/config/app.toml
sed -i -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"$pruning_keep_recent\"/" $HOME/.andromedad/config/app.toml
sed -i -e "s/^pruning-keep-every *=.*/pruning-keep-every = \"$pruning_keep_every\"/" $HOME/.andromedad/config/app.toml
sed -i -e "s/^pruning-interval *=.*/pruning-interval = \"$pruning_interval\"/" $HOME/.andromedad/config/app.toml
```


Indexer (optional)

```python
indexer="null" && \
sed -i -e "s/^indexer *=.*/indexer = \"$indexer\"/" $HOME/.andromedad/config/config.toml
```

andromedad keys add <walletname>
  OR
andromedad keys add <walletname> --recover


```python
sudo systemctl daemon-reload
sudo systemctl enable andromedad
sudo systemctl restart andromedad && sudo journalctl -u andromedad -f -o cat
```


```python
andromedad tx staking create-validator \
--moniker="MonikerName" \
--commission-rate 0.1 \
--commission-max-rate 1 \
--commission-max-change-rate 1 \
--min-self-delegation "1" \
--amount 1000000uandr \
--pubkey $(andromedad tendermint show-validator) \
--from wallet \
--chain-id galileo-3 \
--gas 350000 \
--identity="" \
--website="" \
--details="" -y 
  ```

  Sync Info

  ```python
  andromedad status 2>&1 | jq .SyncInfo
  ```


  Node Info
  ```python
  andromedad status 2>&1 | jq .NodeInfo
  ```


  Check Node Logs
  ```python
  sudo journalctl -u andromedad -f -o cat
  ```


  Check Balance
  ```python
  andromedad query bank balances wallet-address
  ```



  Delete node
  ```python
  sudo systemctl stop andromedad && \
  sudo systemctl disable andromedad && \
  rm /etc/systemd/system/andromedad.service && \
  sudo systemctl daemon-reload && \
  cd $HOME && \
  rm -rf andromedad && \
  rm -rf .andromedad && \
  rm -rf $(which andromedad)
```
