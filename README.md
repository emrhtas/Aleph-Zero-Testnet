# Aleph-Zero-Testnet
## Güncelleme yapıyoruz
```
sudo apt update && sudo apt upgrade -y
```
## İlgili kurulumları yapıyoruz
```
sudo apt install wget git -y
sudo apt-get install docker.io -y
```
## Aleph Node Runner dosyasını klonluyoruz
```
git clone https://github.com/Cardinal-Cryptography/aleph-node-runner
```
## Nodemizi çalıştırıyoruz( nodeismi yazan yere validator olarak görünmesini istediğiniz isminizi yazın) 
```
cd aleph-node-runner
./run_node.sh -n nodeismi
```
