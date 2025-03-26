PERTEMUAN KE XI

TUGAS VIDEO (26 MARET 2025):
https://drive.google.com/drive/folders/10kDR46ULZNoApP0VCN5-jor64Exuf6lp

## Menjalankan kubectl get pods dan Mengelola Microservices

## 1. Persiapan Kubernetes di Docker Desktop
1. **Buka Docker Desktop**.
2. **Pergi ke Settings** (Pengaturan).
3. **Aktifkan Kubernetes** dengan mencentang "Enable Kubernetes".
4. Klik **Apply & Restart**.
5. Tunggu proses **starting** Kubernetes hingga selesai.

## 2. Struktur Folder Microservices

Saya memiliki layanan Microservice berikut:
- `customer`
- `order`
- `produk`
- `eureka`
- `api-gateway`
- `mysql`
- `rabbitmq`
- `payment`

## 3. Deploy Microservices ke Kubernetes
1. Masuk ke folder `k8s`:
   cd k8s
   
2. Jalankan perintah berikut untuk menerapkan konfigurasi masing-masing layanan:
  
   kubectl apply -f customer-service-deployment.yml
   kubectl apply -f customer-service-service.yml
   
   kubectl apply -f order-service-deployment.yml
   kubectl apply -f order-service-service.yml
   
   kubectl apply -f produk-service-deployment.yml
   kubectl apply -f produk-service-service.yml
   
   kubectl apply -f eureka-service-deployment.yml
   kubectl apply -f eureka-service-service.yml
   
   kubectl apply -f api-gateway-deployment.yml
   kubectl apply -f api-gateway-service.yml
   
   kubectl apply -f mysql-deployment.yml
   kubectl apply -f mysql-service.yml
   
   kubectl apply -f rabbitmq-deployment.yml
   kubectl apply -f rabbitmq-service.yml
   
   kubectl apply -f payment-service-deployment.yml
   kubectl apply -f payment-service-service.yml
   ```

## 4. Mengecek Status Pods
Setelah semua layanan diterapkan, jalankan perintah berikut untuk mengecek statusnya:
```sh
kubectl get pods
```
Jika ada beberapa pods yang **Running**, tetapi yang lain **Error**, kemungkinan ada kesalahan seperti **typo** pada nama atau konfigurasi dalam file YAML.

## 5. Memperbaiki Error pada Pods
1. Periksa kembali isi file YAML di dalam folder `k8s`.
2. Jika ada kesalahan, perbaiki file yang bermasalah.
3. Hapus deployment yang bermasalah, misalnya untuk `produk-service`:
   
   kubectl delete deployment produk-service
   
4. Terapkan ulang konfigurasi:
   
   kubectl apply -f produk-service-deployment.yml
   kubectl apply -f produk-service-service.yml
   
5. Jalankan kembali:
   
   kubectl get pods
   
   Jika berhasil, statusnya akan berubah menjadi **Running**.

## 6. Pengujian API Menggunakan Postman
Setelah semua layanan berjalan, lakukan pengujian menggunakan **Postman** dengan port `8080`.

