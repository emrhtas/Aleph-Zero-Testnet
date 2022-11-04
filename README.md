# Aleph-Zero-Testnet
## 1)Güncelleme yapıyoruz
```
sudo apt update && sudo apt upgrade -y
```
## 2)İlgili kurulumları yapıyoruz
```
sudo apt install wget git -y
sudo apt-get install docker.io -y
```
## 3)Aleph Node Runner dosyasını klonluyoruz
```
git clone https://github.com/Cardinal-Cryptography/aleph-node-runner
```
## 4)Nodemizi çalıştırıyoruz( nodeismi yazan yere validator olarak görünmesini istediğiniz ismi yazın) bu yükleme biraz uzun sürebilir. 
```
cd aleph-node-runner
./run_node.sh -n NODEİSMİ --ip SUNUCUIPADRESİ
```
# 5)Validator için gerekli bilgilerimizi alıyoruz. Çıktıyı mutlaka not alın!!!
```
./signer.sh
```
## 6)Log görünteleme
```
docker logs --follow NODEİSMİ
```
## 7) Cüzdan oluşturuyoruz. ( Cüzdanınız varsa eğer onu kullanabilirsiniz) 
(https://test.azero.dev/#/accounts) sayfasına gidiyoruz ve 'add account' diyerek cüzdan oluşturuyoruz. 
## 8)Validator başvuru yapıyoruz
(https://validators.alephzero.org/)
Siteye gidiyoruz ve mail adresimizi yazıyoruz ve maile gelen kodu girerek oturum açıyoruz.  Validator adı ve  sosyal medya hesaplarımızı falan istiyor. Validator adı kısmına kısmına node kurarken kullandığımız ismi kullanalım. Diğer bilgileri istediğiniz gibi ayarlayın.Bu bilgileri aldıktan sonra ' Become a Validator' kısmında 'Apply' tuşuna basıyoruz.  5. adımda aldığımız çıktıdaki bilgileri burada kullanıyoruz. Stash account kısmına kullanacağınız cüzdan adresini yazın.
## Doğrulama İşlemleri(bu doğrulamaları yapmazsanız başvurunuz reddedilir).
### Telemetry de Node ismin görünecek. (kurulum yaparken açık oluyor zaten kontrol edersiniz)
(https://telemetry.azero.dev/#list/0x05d5279c52c484cc80396535a316add7d47b1c5b9e0398dd1f584149341460c5) 
### Kimlik Ayarı
(https://test.azero.dev/#/accounts)  Siteye gidiyoruz, cüzdanımızın sağ tarafındaki üç noktaya tıklayıp 'set on-chain identity' diyoruz. Display name kısmına node ismimizi yazmamız yeterli ancak fazla bilgi göz çıkarmaz, diğer seçenekleri de kendinize göre doldurmanızı tavsiye ederim.
![set on identity](https://user-images.githubusercontent.com/101218992/200088300-7e415edc-7871-4bc8-989f-8f304017ec3a.png)
### Faucet
(https://faucet.test.azero.dev/) Günlük 25k token alabiliyorsunuz. Burada 2 cüzdanla token alıp fazladan aldığınız 25k tokeni validator oluşturacağınız cüzdanınıza göndermenizi tavsiye ederim.
### Stash ve Bond işlemi
(https://test.azero.dev/#/staking/actions) Açılan sayfada sağ tarafta ' Stash' tuşuna basıyoruz ve en az 25k token seçerek bond diyoruz.
### Oturum anahtarı oluşturuyoruz
Sunucumuza bağlanıp aşağıdaki komutu giriyoruz ve çıktıyı kaydediyoruz.
```
curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "author_rotateKeys"}' http://127.0.0.1:9933
```
