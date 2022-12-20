# AlephZero-Testnet
## Gereksinimler ve ödül hakkında bilgilendirme
Teşvikli testnet 10 Kasımda başladı ama ödüllerle alakalı bilgiler ilerleyen zamanlarda belirtilecek. 
![aleph zero gereksinim](https://user-images.githubusercontent.com/101218992/200110712-e6810440-73d6-49fc-8297-b83d5a8427f1.jpeg)
 Ücretli sunucu kullanan arkadaşlar Contabo M paket (6cpu-16gb Ram- 400 gb ssd) ile denedim herhangi bir sorun olmadı node sağlıklı bir şekilde çalışıyor ancak ekibin minimum önerdiği hafıza 1 tb. Bu pakete kurmak isteyenlere hafızayı 600 ssd ye çıkarmasını tavsiye ederim. Testnet bitene kadar belki hafıza dolmaz veya en azından 600 gb dolana kadar node çalıştırmış olursunuz. 
 ### Takıldığınız yerler olursa buradan ulaşabilirsiniz. https://t.me/FortaDestek

## 1)Güncelleme yapıyoruz
```
sudo apt update && sudo apt upgrade -y
```
## 2)İlgili kurulumları yapıyoruz
```
sudo apt install git -y
```
```
sudo apt install screen -y
```
```
sudo apt-get install docker.io -y
```
## 3)Aleph Node Runner dosyasını klonluyoruz
```
git clone https://github.com/Cardinal-Cryptography/aleph-node-runner
cd aleph-node-runner
```
## 4)Screen açıp nodemizi çalıştırıyoruz( nodeismi yazan yere validator olarak görünmesini istediğiniz ismi yazın) bu yükleme biraz uzun sürecek o yüzden başında beklemeyin:) Screenden 'ctrl a d' tuşları ile çıkış yapalım. Daha sonra açtığımız screene girmemiz gerekirse screen -r aleph  ile giriş yapabilirsiniz.
```
screen -S aleph
```
```
./run_node.sh -n NODEİSMİ --ip SUNUCUIPADRESİ
```
Bu kısımda yükleme başladıysa ctrl a d ile screen den çıkın. Boş yere beklemeyin 4-5 saat sürüyor kurulum aşaması :D 
## Yüklemenin durumunu kontrol etmek için tekrar sunucuya bağlandığınız zaman şu komutları kullanabilirsiniz.
```
cd aleph-node-runner
screen -r aleph
```
Kurulum tamamlandıktan sonra 'Are you sure you want to skip the session keys check? [y/N]y' şeklinde bir soru soracak  Y' ya basıp enter diyelim. 
## Buradan sonraki kısımlar için screen içine girmenize gerek yok. Sunucuya bağlandığınızda aleph-node-runner klasörü içine girerek işlem yapmanız yeterli.
```
cd aleph-node-runner
```
## 5)Log görünteleme
```
docker logs --follow NODEİSMİ
```
## 6)Kurulum tamamlandıktan sonra validator onayı için gerekli bilgilerimizi alıyoruz. Çıktıyı mutlaka not alın!!!
```
./signer.sh
```
## 7) Cüzdan oluşturuyoruz. ( Cüzdanınız varsa eğer onu kullanabilirsiniz) İki tane cüzdan oluşturun ve ikisiyle de faucetten token alın. Sonra 2. cüzdandan aldığınız tokeni diğer cüzdana atıp silebilirsiniz.
https://test.azero.dev/#/accounts sayfasına gidiyoruz ve 'add account' diyerek cüzdan oluşturuyoruz. Cüzdanlardan birini silebilirsiniz onu token almak için kullandık validator için tek cüzdan yeterli.
### Faucet
https://faucet.test.azero.dev/ Günlük 25k token alabiliyorsunuz. Burada 2 cüzdanla token alıp fazladan aldığınız 25k tokeni validator oluşturacağınız cüzdanınıza göndermenizi tavsiye ederim.

## 8)Validator başvuru yapıyoruz
https://validators.alephzero.org/
Siteye gidiyoruz ve mail adresimizi yazıyoruz ve maile gelen kodu girerek oturum açıyoruz.  Validator adı ve  sosyal medya hesaplarımızı falan istiyor. Validator adı kısmına kısmına node kurarken kullandığımız ismi kullanalım ve discord bilgisini doğru girelim, onay verilen validatorlere testnet rolü verilecek. Diğer bilgileri istediğiniz gibi ayarlayın.Bu bilgileri aldıktan sonra ' Become a Validator' kısmında 'Apply' tuşuna basıyoruz.  6. adımda aldığımız çıktıdaki bilgileri burada kullanıyoruz. Stash account kısmına kullanacağınız cüzdan adresini yazın.
## 9)Doğrulama İşlemleri(bu doğrulamaları yapmazsanız başvurunuz reddedilir).
### Telemetry de Node ismin görünecek. (kurulum yaparken açık oluyor zaten kontrol edersiniz)
https://telemetry.azero.dev/#list/0x05d5279c52c484cc80396535a316add7d47b1c5b9e0398dd1f584149341460c5
### Kimlik Ayarı
https://test.azero.dev/#/accounts  Siteye gidiyoruz, cüzdanımızın sağ tarafındaki üç noktaya tıklayıp 'set on-chain identity' diyoruz. Display name kısmına node ismimizi yazmamız yeterli ancak fazla bilgi göz çıkarmaz, diğer seçenekleri de kendinize göre doldurmanızı tavsiye ederim.
![set on identity](https://user-images.githubusercontent.com/101218992/200088300-7e415edc-7871-4bc8-989f-8f304017ec3a.png)

### Stash ve Bond işlemi
https://test.azero.dev/#/staking/actions Açılan sayfada sağ tarafta ' Stash' tuşuna basıyoruz ve gelen ekranda en az 25k token seçerek bond diyoruz.
![Stash ve Bond](![aleph stash](https://user-images.githubusercontent.com/101218992/202739938-2c60919b-79ac-4ef3-b8ba-045f28d9ac90.png)
### Session Key oluşturuyoruz(Çıktıyı not almayı unutmayın!!!)
Sunucumuza bağlanıp aşağıdaki komutu giriyoruz.
```
curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "author_rotateKeys"}' http://127.0.0.1:9933
```

Aldığımız çıktı şu şekilde olacak;
{"jsonrpc":"2.0","result":"0xa8bccfe29da88f256545d2addc194b734f615cec70b99845d56384e0c0c2fe64de211d8dd724dece2b3bc26c3250c550b644fb586c0875693ee1099c13feb806

Çıktıyı not almayı unutmayın 0x le başlayan kısım bizim anahtarımız!!!
https://test.azero.dev/#/staking/actions   cüzdanımızın sağ tarafındaki 'set session key' tuşuna basarak sunucumuzdan aldığımız 0x li anahtarı giriyoruz ve onaylıyoruz.
İşlem onaylandıktan sonra yine aynı sayfada cüzdanımızın sağ tarafında olan 'validate' tuşuna basarak komisyon oranımızı belirliyoruz ve onaylıyoruz. 
Bu işlemlerin sonunda https://telemetry.azero.dev/#list/0x05d5279c52c484cc80396535a316add7d47b1c5b9e0398dd1f584149341460c5 sitesinde ve https://test.azero.dev/#/staking sitesinde waiting kısmında node isminizi  görüyor olmanız lazım.
#### Buraya kadar olan adımları doğru bir şekilde yaptıysanız 1 hafta içinde validator başvurunuz onaylanacaktır.

### Güncelleme komutu
```
docker stop NODEİSMİ 
cd aleph-node-runner
./run_node.sh -n NODEİSMİ --ip SUNUCUİPADRESİ 
```

## Validator onayı aldıktan sonra önemli olan şeyler
15 dakikalık süreçler şeklinde aktif sete 4 er kişi alınıyor ve 15 dakika sonunda sıradaki 4 kişi aktif sete giriyor. Bu işlem tamamen sırayla gidiyor herkese eşit oranda aktif set için şans veriliyor. 
https://test.azero.dev/#/staking Açılan sayfada validator stats a tıklıyoruz ve cüzdan adresimizi yazıp enter diyoruz. Performans bilgilerimizin yazdığı bir ekran açılıyor. 
Session kısmında aktif sette olduğumuz oturumları gösteriyor. 1 oturumda bizden 64-65 blok beklentisi var ve bizden minimum %80 verimlilik bekleniyor. %80 e ulaşamazsanız eğer 'Underperformed Session Count' kısmına başarısız olduğunuz oturum sayısı ekleniyor. 
![aleph validator stats](https://user-images.githubusercontent.com/101218992/202911878-c306520d-e9be-43f4-8b9a-b555d9830ec1.png)

