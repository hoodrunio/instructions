![alt text](https://i.hizliresim.com/fkj8pa5.png)



```python
sudo apt update && sudo apt upgrade -y
```

```python
sudo apt install nodejs && sudo apt install git
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

```python
sudo apt-get install -y nodejs
```

```python
sudo apt install npm
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
cd my-snapshot-squid
```

Subsquid Dashboard sitesinde `Get Key`'e tıklayınca inen snapshot dosyasını `gateway/key` klasörü içine SFTP bağlantısı ile aktarın.

```python
sqd up
```

```python
npm ci
sqd build
sqd migration:apply
```

```python
sqd run .
```


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


