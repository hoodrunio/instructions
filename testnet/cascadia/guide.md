

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
git clone https://github.com/cascadiafoundation/cascadia && cd cascadia
git checkout v0.1.5
make install
```


```python
cascadiad init MonikerName --chain-id cascadia_6102-1
cascadiad config chain-id cascadia_6102-1
```


```python
wget -O $HOME/.cascadiad/config/genesis.json "https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/cascadia/genesis.json"
```

```python
wget -O $HOME/.cascadiad/config/addrbook.json "https://raw.githubusercontent.com/testnetrunn/instructions/main/testnet/cascadia/addrbook.json"
```

```python
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$(curl  https://raw.githubusercontent.com/CascadiaFoundation/chain-configuration/master/testnet/persistent_peers.txt)\"/" ~/.cascadiad/config/config.toml
```

```python
sed -i.bak -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.0025aCC\"/" ~/.cascadiad/config/app.toml
```

```python
sudo tee /etc/systemd/system/cascadiad.service > /dev/null <<EOF
[Unit]
Description=Cascadia Foundation
After=network-online.target

[Service]
User=$USER
ExecStart=$(which cascadiad) start
Restart=always
RestartSec=3
LimitNOFILE=4096

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
sed -i -e "s/^pruning *=.*/pruning = \"$pruning\"/" $HOME/.cascadiad/config/app.toml
sed -i -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"$pruning_keep_recent\"/" $HOME/.cascadiad/config/app.toml
sed -i -e "s/^pruning-keep-every *=.*/pruning-keep-every = \"$pruning_keep_every\"/" $HOME/.cascadiad/config/app.toml
sed -i -e "s/^pruning-interval *=.*/pruning-interval = \"$pruning_interval\"/" $HOME/.cascadiad/config/app.toml
```


Indexer (optional)

```python
indexer="null" && \
sed -i -e "s/^indexer *=.*/indexer = \"$indexer\"/" $HOME/.cascadiad/config/config.toml
```


```python
sudo systemctl daemon-reload
sudo systemctl enable cascadiad
sudo systemctl restart cascadiad && sudo journalctl -u cascadiad -f -o cat
```


```python
cascadiad tx staking create-validator \
  --amount "10000000000000000000"aCC \
  --from wallet \
  --commission-max-change-rate "0.2" \
  --commission-max-rate "0.5" \
  --commission-rate "0.1" \
  --min-self-delegation "1" \
  --pubkey  $(cascadiad tendermint show-validator) \
  --moniker "Moniker-Name" \
  --chain-id cascadia_6102-1 \
  --details="" \
  --identity="" \
  --gas-prices 7aCC \
  --gas 250000 \
  --website="" -y
  ```

  Sync Info

  ```python
  cascadiad status 2>&1 | jq .SyncInfo
  ```


  Node Info
  ```python
  cascadiad status 2>&1 | jq .NodeInfo
  ```


  Check Node Logs
  ```python
  sudo journalctl -u cascadiad -f -o cat
  ```


  Check Balance
  ```python
  cascadiad query bank balances wallet-address
  ```



  Delete node
  ```python
sudo systemctl stop cascadiad
sudo systemctl disable cascadiad
rm /etc/systemd/system/cascadiad.service
sudo systemctl daemon-reload
cd $HOME
rm -rf cascadia
rm -rf .cascadiad
rm -rf $(which cascadiad)
```







































