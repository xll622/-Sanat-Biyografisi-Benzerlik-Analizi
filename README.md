# -Sanat-Biyografisi-Benzerlik-Analizi
Biyografi benzerliğine göre sanatçılar arasında bağlantılar kurmak.
Bu proje, doğal dil işleme (NLP) teknikleri kullanarak sanatçılarla ilgili metin verilerini analiz etmeyi amaçlamaktadır. Veri seti üzerinde çeşitli ön işleme adımları uygulanmış ve makine öğrenimi modelleriyle anlamlı çıkarımlar elde edilmeye çalışılmıştır.

📁 Proje İçeriği
Veri Seti: Sanatçılara ait biyografik metinler veya açıklamalar

Amaç: Sanatçıların ortak özelliklerini, temalarını ve yazı dilini analiz etmek
# 🧱 Gerekli Kütüphaneler
pip install pandas
pip install numpy
pip install nltk
pip install gensim
pip install scikit-learn
pip install matplotlib

# 📂 Veri Seti
Kullandığım veri seti sanatcilar_biyografi_lemmatized.csv adında, çeşitli sanatçılara ait biyografi metinlerinden oluşuyor. Proje boyunca bu metinler üzerinde çalışıldı. İçerik kısa, anlam yoğun ve kültürel bağlam barındırdığı için model değerlendirmesi açısından oldukça uygun.

# ⚙️ Uygulanan Yöntemler
1. Ön İşleme
Noktalama işaretleri ve gereksiz karakterler temizlendi.

Küçük harfe dönüştürme uygulandı.

nltk kullanılarak durdurma kelimeleri kaldırıldı.

Tokenizasyon, lemmatizasyon işlemleri zaten veri setine önceden uygulanmıştı (hazır lemmatized CSV üzerinden gidildi).

2. TF-IDF Vektörleştirme
TfidfVectorizer ile tüm metinler vektörleştirildi.

Ardından cosine similarity ile her bir metnin diğer tüm metinlere benzerlik skoru çıkarıldı.

Bu skorlar üzerinden her model için en benzer ilk 5 metin listelendi.

3. Word2Vec ile Anlamsal Temsil
gensim.models.Word2Vec kullanarak hem CBOW hem Skip-Gram yapılandırmaları denendi.

Parametreler:

vector_size=100

window=5

min_count=1

Her metin, içindeki kelimelerin ortalama Word2Vec vektörüyle temsil edildi.

Yine cosine similarity ile en benzer 5 metin hesaplandı.

4. Model Karşılaştırmaları
Her modelin verdiği ilk 5 sonuç karşılaştırıldı.

Jaccard Benzerliği kullanılarak her modelin birbirine olan benzerliği ölçüldü.

Burada 18x18'lik bir benzerlik matrisi hedeflendi, ancak kodlama kısmında bu matrisi oluştururken teknik zorluklar yaşandı (örneğin top5_per_model değişkeni tanımlanmadığı için NameError hatası alındı).

