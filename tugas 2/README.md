![9](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/bb5497bf-201c-465c-a8b8-d4f0f2b8be59)Nama : Panca Aryodya Mulia

NIM : 1203210131

1. Membuat microservice 3-5

   ```bash sudo lxc-create -n microservice3 -t download -- --dist "debian" --release "buster" –arch amd64 ```
   ```bash sudo lxc-create -n microservice4 -t download -- --dist "debian" --release "buster" –arch amd64 ```
   ```bash sudo lxc-create -n microservice5 -t download -- --dist "debian" --release "buster" –arch amd64 ```

   
![1](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/254c3039-5c8d-4a02-aee4-0fe5827f7526)
![2](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/220d96cd-9e19-43e6-a6c3-f616214250fc)
![3](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/337c95c1-8cd7-4b83-b176-e638f314f03e)

2. jalankan semua microservice yang sudah di buat
   
   ```bash lxc-start -n microservice3 ```
   ```bash lxc-start -n microservice4 ```
   ```bash lxc-start -n microservice5 ```

   ![4](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/4d9f655d-3c10-40a8-8645-e42c8aba6b94)

4. konfigurasi lakukan pada microservice 3-5
   
   ```bash lxc-attach microservice3 ```
   ```bash apt update ```
   ```bash apt install nginx nano ```
   ![5](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/212c1e86-5e7e-4321-885c-4b6f4e182098)
   ```bash nano /etc/hosts ```
   ![6](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/71de9315-3384-4b75-bd21-26a7da4bd201)


   ```bash lxc-attach microservice4 ```
   ```bash apt update ```
   ```bash apt install nginx nano ```
   ![7](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/8ac1828c-ee38-4463-9f20-ee2261ded0c5)
   ```bash nano /etc/hosts ```
   ![8](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/196032f4-e677-4361-9366-99e1ff419061)


   ```bash lxc-attach microservice5 ```
   ```bash apt update ```
   ```bash apt install nginx nano ```
   ![9](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/b5967e73-6d69-4412-b9ba-13e0a638d52e)
   ```bash nano /etc/hosts ```
   ![10](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/32b491c8-bcea-4b9b-9ede-b3e78ad5157b)

5. konfigurasi hosts wsl

   ```bash nano /etc/hosts ```
   ![11](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/e651ae5a-3d3f-4c01-a914-304fe94721fe)
   ```bash sudo nano /etc/nginx/sites-available/sister.local ```
   ![12](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/51958354-bba8-46d7-aafa-29ede8fde7de)
   ```bash nginx -t ```
   ```bash nginx -s reload ```
   ![13](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/26ca97ab-229f-4827-9820-8eca8845eb6f)
   ```bash curl -i app.sister.local ```
   ![14](https://github.com/panskeeh/Sistem-Terdistribusi/assets/95496180/140e9405-9ee1-4411-80ba-a9f26928fedc)
   ```bash tail -f /var/log/nginx/app.sister.local-access.log ```







   
   
