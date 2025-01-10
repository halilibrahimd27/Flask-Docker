# Python 3.9 imajını kullan
FROM python:3.9

# Çalışma dizini oluştur
WORKDIR /app

# Gerekli dosyaları kopyala
COPY requirements.txt .
COPY api.py .

# Gerekli Python paketlerini yükle
RUN pip install --no-cache-dir -r requirements.txt

# Uygulamanın portunu aç
EXPOSE 2700

# Uygulama başlatma komutu
CMD ["python", "api.py"]
