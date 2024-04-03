Tugas 1

Nama : Panca Aryodya Mulia

NIM : 1203210131

  1. Buat microservice 1
```bash
lxc-create --name microservice1 --template download -- --dist "ubuntu" --release "focal" --arch amd64 
```
![1](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/ec10aa3c-7d4b-42c9-9903-931c8f0fad08)

  2. Buat microservice 2
```bash
lxc-create --name microservice2 --template download -- --dist "ubuntu" --release "bionic" --arch amd64
```
![2](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/6096956f-99b6-45e0-b581-980a2beb5c3a)

  3. command # ip r -> untuk mengetahui ip dan subnet server dan microservice
```bash
ip r
```
![3](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/170003b8-a85e-4dee-a3d6-846ec478048b)
```bash
lxc-ls -f
```
![4](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/144b9c68-13ad-4b64-a45c-d59434f57659)

  4. masuk ke microservice1 dan microservice2 lalu install nginx dan network manager
```bash
lxc-attach -n microservice1
sudo apt install nginx nginx-extras
sudo apt install network-manager
```
![5](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/991266ec-dd35-4cd4-85b6-457f138f9c1b)
```bash
exit
lxc-attach -n microservice2
sudo apt install nginx nginx-extras
sudo apt install network-manager 
```
![6](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/11c67b65-a3bd-4957-8d5f-50975361c859)
```bash
exit
```
  5. setting static IP di microservice1
```bash
nano /etc/netplan/10-lxc.yaml
```
![7](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/3106090b-5bf9-4cdc-b57c-40cdae041277)
```bash
sudo netplan apply
ifconfig
```
![8](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/1ab8c104-4eb9-4f07-9805-9a77b37b2761)

  6. setting network interfaces
```bash
nano /etc/network/interfaces
```
![9](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/f90b69fd-c429-4345-95c7-b0e74a35eb5d)

  7. restart network manager
```bash
sudo systemctl restart NetworkManager
ifconfig
```
![10](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/295df8ef-5fa5-4163-b287-6164c3e50b67)

  8. Setting ngix
```bash
cd /etc/nginx/sites-available
touch microservice1.dev
nano microservice1.dev
```
![11](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/560a9c0f-b64e-4025-a7ae-b44fca6c8b16)
```bash
cd ../sites-enabled 
ln -s /etc/nginx/sites-available/microservice1.dev . 
nginx -t 
nginx -s reload 
nano /etc/hosts
```
![12](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/e8be4da3-baec-455c-83a6-c68469129bfd)
```bash
cd /var/www/html 
mkdir microservice1
cp index.nginx-debian.html microservice1/index.html 
cd microservice1
nano index.html
```
![13](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/6d14f2a5-0924-445a-853b-a6b6f167615e)

  9. Lakukan curl ke microservice1
```bash
curl -i http://microservice1.dev
```
![14](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/a5ba322d-102a-4810-a213-08e182960f4c)

  10. Setting Static IP microservice2
```bash
apt install nano net-tools curl 
sudo nano /etc/netplan/10-lxc.yaml 
```
![15](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/8f69a408-2d11-49c0-9aea-3614ce84e5d7)
```bash
sudo netplan apply 
ifconfig
```
![16](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/6f73e50c-d97f-4e90-ada2-f21f234dc3af)

setting network interfaces
```bash
nano /etc/network/interfaces
```
![17](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/6f67506d-8be6-4147-be34-5b35ea433da5)
```bash
sudo systemctl restart NetworkManager
ifconfig
```
![18](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/be9d23e8-6348-4b02-8bb0-8628db6038dc)

setting nginx
```bash
cd /etc/nginx/sites-available
touch microservice2.dev
nano microservice2.dev
```
![19](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/7c377999-40cd-421e-8a61-5fa091ae0b7a)
```bash
cd ../sites-enabled
ln -s /etc/nginx/sites-available/microservice2.dev
nginx -t
nginx -s reload
nano /etc/hosts
```
![20](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/d32ca1ef-3a4d-49ee-b6a8-1ecb70051db2)
```bash
cd /var/www/html 
mkdir microservice2 
cp index.nginx-debian.html microservice2/index.html 
cd microservice2
nano index.html
```
![21](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/6413d62e-473d-4487-b3e1-106e7dd3e4a2)
```bash
curl -i http://microservice2.dev
```
![22](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/5b4f3add-a3d8-4010-a00b-8680b706fe0a)

  11. Setting hosts di WSL
```bash
nano /etc/hosts
```
![23](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/9cfdbae2-2ea3-4776-aba5-bb0dca1caa8a)
```bash
cd /etc/nginx/sites-available
touch sister.local
nano sister.local
```
![24](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/a02f14d5-74b2-4f71-b11c-1a1b6cdf8ad1)
```bash
cd ../sites-enabled
sudo ln -s /etc/nginx/sites-available/sister.local .
sudo nginx -t
sudo nginx -s reload
```
cek route apakah sudah benar
```bash
curl -i http://sister.local
```
```bash
curl -i http://sister.local/blog
```
![26](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/dd9d1b2e-01c5-4cbd-b12e-7215552884b5)
```bash
curl -i http://sister.local/aboutus
```
![27](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/7eef3695-a777-4d17-975e-a6bb424ef99f)
