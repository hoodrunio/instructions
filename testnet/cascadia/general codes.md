### Key

Add New Key

```python
cascadiad keys add wallet
```


Recover Key

```python
cascadiad keys add wallet --recover
```


List All Keys

```python
cascadiad keys list
```

Delete Key

```python
cascadiad keys delete wallet
```

Wallet Balance

```python
cascadiad q bank balances $(cascadiad keys show wallet -a)
```

### Validator

Edit Validator

```python
cascadiad tx staking edit-validator \
--new-moniker="Moniker-Name" \
--identity= \
--details="" \
--chain-id=cascadia_6102-1 \
--commission-rate=0.1 \
--from=wallet \
--gas-prices=7aCC \
--gas-adjustment=1.5 \
--gas=auto \
-y
```

Unjail Validator

```python
cascadiad tx slashing unjail --from wallet --chain-id cascadia_6102-1 --gas-prices 7aCC --gas-adjustment 1.5 --gas auto -y
```


Withdraw Commission And Rewards From Your Validator

```python
cascadiad tx distribution withdraw-rewards $(cascadiad keys show wallet --bech val -a) --commission --from wallet --chain-id cascadia_6102-1 --gas-prices 7aCC --gas-adjustment 1.5 --gas auto -y
```

Delegate to Yourself

```python
cascadiad tx staking delegate $(cascadiad keys show wallet --bech val -a) 1000000aCC --from wallet --chain-id cascadia_6102-1 --gas-prices 7aCC --gas-adjustment 1.5 --gas auto -y
```

Delegate

```python
cascadiad tx staking delegate YOUR_TO_VALOPER_ADDRESS 1000000aCC --from wallet --chain-id cascadia_6102-1 --gas-prices 7aCC --gas-adjustment 1.5 --gas auto -y
```


Redelegate

```python
cascadiad tx staking redelegate $(cascadiad keys show wallet --bech val -a) YOUR_TO_VALOPER_ADDRESS 1000000aCC --from wallet --chain-id cascadia_6102-1 --gas-prices 7aCC --gas-adjustment 1.5 --gas auto -y
```


Unbond

```python
cascadiad tx staking unbond $(cascadiad keys show wallet --bech val -a) 1000000aCC --from wallet --chain-id cascadia_6102-1 --gas-prices 7aCC --gas-adjustment 1.5 --gas auto -y
```

Send

```python
cascadiad tx bank send wallet YOUR_TO_WALLET_ADDRESS 1000000aCC --from wallet --chain-id cascadia_6102-1 --gas-prices 7aCC --gas-adjustment 1.5 --gas auto -y
```


### Service Management

Reload Services

```python
sudo systemctl daemon-reload
```

Enable Service

```python
sudo systemctl enable cascadiad
```

Disable Service

```python
sudo systemctl disable cascadiad
```

Run Service

```python
sudo systemctl start cascadiad
```

Stop Service

```python
sudo systemctl stop cascadiad
```

Restart Service

```python
sudo systemctl restart cascadiad
```

Check Service Status

```python
sudo systemctl status cascadiad
```

Check Service Logs

```python
sudo journalctl -u cascadiad -f --no-hostname -o cat
```































