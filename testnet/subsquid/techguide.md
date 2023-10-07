![alt text](https://i.hizliresim.com/ea13mj8.png)

Guide içinde hem `Github Codespace` hemde kendi sunucunuz üzerinden kurulum var. Kendi sunucunuz üzerinden kurulum yapacaksanız aşağıdaki `Sunucu Üzerinden Kurulum` yerinden başlayın.


# Github Codespace Üzerinden Kurulum

## Hatırlatma
İsterseniz `Github Codespaces` üzerinden kendi sunucunuzu kullanmadan görevleri yapabilirsiniz. Ücretsiz Kullanım detayları;


![alt text](https://i.hizliresim.com/6uw6f92.png)

Görevleri tamamladıktan sonra `delete` yapmayı unutmayın. (Github Codespace sitesindeki üç noktalı yerden)

![alt text](https://i.hizliresim.com/s0fav51.png)

<a href="https://github.com/codespaces">Github Codespace Sitesine Gidin</a>

Ekrandaki Blank kısmında `Use this template`'e tıklayın.

![alt text](https://i.hizliresim.com/cfgq9od.png)

Ayarlamalar bititğinde aşağıdaki gibi bir terminal çıktısı olacak. 

![alt text](https://i.hizliresim.com/ok517ng.png)

Bu çıktı üzerinde aşağıdaki kodları yazabilirsiniz.

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
sudo apt install npm
```

`single-proc squid` görevi için <a href="https://app.subsquid.io/quests">Subsquid Quest</a>  sitesindeki ilgili görevin get key'e basarak dosyasını indirin.

```python
npm install --global @subsquid/cli@latest
```

```python
sqd --version
```

Sorunsuz ise `@subsquid/cli/2.5.0 linux-x64 node-v20.5.1` çıktısını almalısınız.

```python
sqd init my-single-proc-squid -t https://github.com/subsquid-quests/single-chain-squid
```

```python
cd my-single-proc-squid
```


Bu aşamadan sonra aşağıdaki ssdeki gibi keys dosyası üzerinde sağ tıklayarak karşıdan yükleme diyerek single dosyasını seçin ve yükleyin.

![alt text](https://i.hizliresim.com/mxk80i0.png)

Yüklemeden sonra 

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
Her şey sorunsuz ise aşağıdaki gibi çıktı alacaksınız.

![alt text](https://i.hizliresim.com/se9p2x3.png)

```python
sqd run .
```
![alt text](https://i.hizliresim.com/mjaqwgp.png)

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

2. 3. ve 4. görevler için eğer yeni bir Github Codespace oluşturmayacak şu anki ile devam edecekseniz aşağıdaki yolu izleyin.
  
CRTL-C ile durdurun.

```python
sqd down
```
`my-single-proc-squid` dosyanının üzerinde sağ tık yaparak dosyayı silin. ( `kalıcı olarak sil` ) 
Ana dizine gelmek için `cd` yapın.

Terminalin sağındaki işeretli yerden terminali kapatın.

![alt text](https://i.hizliresim.com/1smtqu3.png)

Aşağıdaki gibi yeni bir terminal açın. 

![alt text](https://i.hizliresim.com/k0m53t4.png)


Bundan sonra hangi görevi yapacaksanız onun aşağıdaki gibi iki kodunu girin.

Örnek 2. görev için 

```python
sqd init my-double-proc-squid -t https://github.com/subsquid-quests/double-chain-squid
```

```python
cd my-double-proc-squid
```

Diğer kodlar yukarıdakilerin aynısı. (dosya yüklemeden sonraki kodlar `sqd up` ile başlayan)



# Sunucu Üzerinden Kurulum


Sunucu üzerinde bir çok hata çıkabiliyor. Aşağıdaki kodları kullanarak bir hata almadım.

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
sudo apt install npm
```

```python
mkdir ~/global-node-packages
```

```python
npm config set prefix ~/global-node-packages
```

```python
export PATH="${HOME}/global-node-packages/bin:$PATH"
```

```python
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
```

```python
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

```python
source ~/.profile
```

```python
nvm install node
```

```python
nvm use --delete-prefix v20.8.0
```

```python
npm install -g npm@10.2.0
```

Buradan sonrası yukarıdaki  `npm install --global @subsquid/cli@latest` kodu ve diğerleri ile aynı.

Kendi Sunucunuz üzerinde de hata alırsanız yukarıdaki durdurma başlatma kodlarını girebilirsiniz.

Hangi görevi yapacaksanız örnek `cd my-double-proc-squid` kodundan sonra `SFTP` bağlantısı ile (`putty-termius-winscp`) gerekli dosyayı aşağıdaki gibi keys dosyası içine yükleyin.

![alt text](https://i.hizliresim.com/fn92koo.png)


- **https://t.me/testnetrun**

- **https://link3.to/testnetrun**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**

- **https://twitter.com/testnetrun**






