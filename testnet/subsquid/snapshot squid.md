![alt text](https://i.hizliresim.com/fkj8pa5.png)


# Hatırlatma

Eğer `Codespaces` üzerinden görevi tamamlamak isterseniz; **https://github.com/testnetrunn/instructions/blob/main/testnet/subsquid/techguide.md** guide'inda 
`sqd init my-single-proc-squid -t https://github.com/subsquid-quests/single-chain-squid` koduna kadar ilerledikten sonra bu guide'daki
`sqd init my-snapshot-squid -t https://github.com/subsquid-quests/snapshot-squid` kodunu girerek devam edebilirsiniz.

```python
sudo apt update && sudo apt upgrade -y && sudo apt install nodejs && sudo apt install git
```

```python
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

```python
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```python
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```

```python
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

```python
curl -sL https://deb.nodesource.com/setup_20.x | sudo -E bash -
```
60sn bekleyin.

```python
sudo apt-get install -y nodejs
```

```python
sudo npm install -g npm@10.1.0
```

```python
npm install --global @subsquid/cli@latest
```

```python
sqd --version
```

Sorunsuz ise `@subsquid/cli/2.5.0 linux-x64 node-v20.5.1` çıktısını almalısınız.

## Run The Squid

```python
sqd init my-snapshot-squid -t https://github.com/subsquid-quests/snapshot-squid
```

```python
screen -S subsquid
```

```python
cd my-snapshot-squid
```

Subsquid Dashboard sitesinde `Get Key`'e tıklayınca inen `snapshot.key` dosyasını `my-snapshot-squid/query-gateway/keys` klasörü içine SFTP bağlantısı ile aktarın.

```python
sqd up
```

```python
npm ci
sqd build
sqd migration:apply
```
![alt text](https://i.hizliresim.com/ezytgp1.png)


```python
sqd run .
```
![alt text](https://i.hizliresim.com/22oggzg.png)

![alt text](https://i.hizliresim.com/5l2wd3z.png)


## Önemli
Eğer arada hata verirse yada sitede görev yüzdeliği ilerlememeye başlarsa aşağıdaki kodları girin.

CRTL-C ile durdurun.

```python
sqd down
```

```python
sqd up
```

```python
npm ci
```

```python
sqd build
```

```python
sqd migration:apply
```

```python
sqd run .
```

Görev tamamlandıktan sonra siteden claim yapın.


