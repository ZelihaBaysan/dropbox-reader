# 📦 Redis Chat Vector Indexing Pipeline

Bu proje, **Redis** üzerinde tutulan verileri alıp, gereksiz olanları regex filtrelerle eleyerek, anlamlı parçalara bölüp **vektörleştirir** ve ardından bu verileri **Chroma vektör veritabanı** içine kaydeder.

Bu sayede daha sonra bu verilere **semantic search** veya **LLM tabanlı bir chatbot** ile erişmek mümkün olur.

---

## 🚀 Amaç

- Redis'te depolanan verileri almak
- Filtreleme kurallarını uygulayarak gereksizleri ayıklamak
- Kalan verileri anlamlı parçalara bölmek
- HuggingFace embedding modeli ile vektörleştirmek
- ChromaDB içine kaydetmek

Böylece bu verilerle:
- Akıllı arama
- Chatbot eğitimi
- Benzer içerik bulma
- Bilgi tabanı oluşturma
gibi işlemler kolaylıkla yapılabilir.

---

## 🧰 Kullanılan Teknolojiler

| Teknoloji | Açıklama |
|----------|----------|
| **Redis** | Hızlı veri deposu (bu projede Upstash Redis üzerinden bağlanılıyor) |
| **Upstash Redis** | Cloud tabanlı Redis servisi |
| **llama-index** | LLM destekli arama ve veri yönetimi için kullanılır |
| **HuggingFace Transformers** | Metinleri vektörlere (embedding) çeviren model |
| **ChromaDB** | Vektör tabanlı veri tabanı |
| **dotenv** | Ortam değişkenlerini `.env` dosyasından okur |
| **re (Regex)** | Veri filtreleme kuralları için kullanılır |


## ⚙️ .env Dosyası Örneği

Projeyi çalıştırmadan önce proje klasöründe bir `.env` dosyası oluştur ve aşağıdaki değişkenleri ekle:

```env
# Upstash Redis Bağlantı Bilgileri
UPSTASH_REDIS_HOST=your-redis-host.upstash.io
UPSTASH_REDIS_PORT=6379
UPSTASH_REDIS_PASSWORD=your_redis_password

# Diğer ayarlar
DATA_SOURCE_ID=chat_data_v1
````

---

## 📦 Gereksinimler (req.txt)

Projede kullanılan Python paketleri `req.txt` dosyasına şu şekilde yazılmalıdır:

Kurmak için:

```bash
pip install -r req.txt
```

---

## 🛠️ Nasıl Çalışır?

### 1. Ortam Değişkenlerini Ayarla:

`.env` dosyasını oluştur ve Redis bağlantı bilgilerini gir.

### 2. Gerekli Kütüphaneleri Kur:

```bash
pip install -r req.txt
```

### 3. Ana Dosyayı Çalıştır:

```bash
python index.py
```

### Ne Olur?

1. Redis'e bağlanır
2. Tüm verileri alır
3. Regex filtrelerle gereksiz verileri çıkarır
4. Verileri parçalara böler
5. Her parçayı vektörleştirir (embedding)
6. ChromaDB içine kaydeder

---

## 🧪 Örnek Kullanım Senaryosu

* Redis’e kayıtlı geçmiş sohbet verilerini al
* Kullanıcının yazdığı bir mesajla benzer geçmiş konuşmaları bul
* Chatbot’un daha anlamlı ve bağlamsal cevaplar vermesini sağla

---

## 📝 Notlar

* `SentenceSplitter`, uzun metinleri 512 kelimelik parçalar hâlinde böler. Her parça arasında 20 kelime örtüşme (overlap) bırakılır.
* Proje, `sentence-transformers/all-MiniLM-L6-v2` modelini kullanır. Bu model küçük ve hızlıdır.
* ChromaDB verileri yerel olarak `./chroma_db/` klasöründe saklanır.

---

## ✅ Özet

Bu proje sayesinde Redis’te saklanan veriler artık yalnızca anahtar-değer yapısında değil; **anlamlı bir şekilde sorgulanabilir vektörlere** dönüştürülmüş olur. Bu, chatbot’lar, semantic search sistemleri, bilgi keşfi gibi birçok alanda kullanılabilir.

---

