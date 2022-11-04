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
