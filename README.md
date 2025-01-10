# Flask API Docker Uygulaması

Bu proje, Flask tabanlı bir RESTful API'nin Docker imajı kullanılarak container içinde çalıştırılmasını sağlar. Uygulama, `GET` ve `POST` istekleriyle temel işlemler yapan bir API sunar.

---

## 🚀 Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki araçlara ihtiyacınız vardır:
- **Docker Desktop** (Windows/macOS için): [Docker Desktop İndirme Linki](https://www.docker.com/products/docker-desktop/)
- **Linux kullanıcıları için:** `docker` ve `docker-compose` paketlerinin yüklü olması gerekmektedir.

---

## 📁 Proje Dosya Yapısı

```plaintext
/flask-docker-app
├── api.py                 # Flask API kodu
├── requirements.txt        # Gerekli Python bağımlılıkları
├── Dockerfile              # Docker imajı oluşturma talimatları
├── docker-compose.yaml     # docker-compose yapılandırma dosyası
└── README.md               # Proje rehberi


---

## 🛠️ Kurulum Adımları

### 1. Docker İmajını Build Etme

Terminal veya PowerShell'de proje dizinine giderek aşağıdaki komutu çalıştırın:
```bash
docker build -t flask-docker-api .
```

---

### 2. Docker Container Çalıştırma

Docker imajından container oluşturup çalıştırmak için:
```bash
docker run -p 2700:2700 flask-docker-api
```
Bu komut `localhost:2700` üzerinde API'yi başlatır.

---

### 3. docker-compose ile Çalıştırma

`docker-compose.yaml` dosyasını kullanarak uygulamayı çalıştırmak için:
```bash
docker-compose up --build
```

---

## 🌐 API Kullanımı

### **GET `/`**
- **Açıklama:** Basit bir `Hello, World!` mesajı döner.
- **Örnek Yanıt:**
  ```json
  {
    "message": "Hello, World!"
  }
  ```

### **GET `/add?num1=<int>&num2=<int>`**
- **Açıklama:** `num1` ve `num2` parametrelerini toplayarak sonucu döner.
- **Örnek URL:**
  ```
  http://localhost:2700/add?num1=5&num2=7
  ```
- **Örnek Yanıt:**
  ```json
  {
    "result": 12
  }
  ```

### **POST `/multiply`**
- **Açıklama:** Gönderilen iki sayıyı çarpar ve sonucu döner.
- **Gönderim (JSON):**
  ```json
  {
    "num1": 4,
    "num2": 6
  }
  ```
- **Örnek Yanıt:**
  ```json
  {
    "result": 24
  }
  ```

---

## ✅ Uygulamanın Çalıştığını Kontrol Etme

1. Tarayıcı veya Postman'de şu URL'yi açın:
   ```
   http://localhost:2700/
   ```
   **Yanıt:**
   ```json
   {
     "message": "Hello, World!"
   }
   ```

2. Diğer endpointleri test etmek için yukarıdaki URL'leri kullanabilirsiniz.

---

## ⚠️ Olası Sorunlar ve Çözümler

### 1. **"Cannot connect to the Docker daemon" Hatası**
**Çözüm:** Docker Desktop'un çalıştığından emin olun.

### 2. **"ModuleNotFoundError: No module named 'flask'" Hatası**
**Çözüm:** `requirements.txt` içeriği doğruysa ve `pip install -r requirements.txt` başarılı çalıştıysa, sorunun olmaması gerekir. Sorun devam ederse:
```bash
docker-compose down && docker-compose up --build
```

---

## 📚 Ek Bilgiler

- Proje geliştirme sırasında `Flask-RESTful` modülü ile temel `GET` ve `POST` işlemleri kullanılmıştır.
- **Flask API Port Numarası:** `2700`
