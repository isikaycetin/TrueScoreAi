# TrueScoreAI: E-Ticaret Yorumları İçin NLP Tabanlı Şeffaf Puanlama Sistemi

E-ticaret platformlarındaki müşteri yorumlarını analiz ederek; kargo, lojistik veya satıcı kaynaklı sorunları filtreleyen ve sadece gerçek ürün kalitesini yansıtan şeffaf bir skor-puan üreten yapay zeka mimarisi.

## 🚨 Problem & 🛠️ Çözüm
**Problem:** Tüketiciler, e-ticaret platformlarında ürün araştırırken genellikle ürünün kendisiyle ilgisi olmayan (kargo gecikmesi, paketin ezilmesi ,satıcı kaynaklı sorunlar vb.) veya sahte olan yorumlar nedeniyle yanıltılmaktadır. Bu durum, kaliteli ürünlerin puanını haksız yere düşürmekte ve müşterinin doğru ürünü seçmesini zorlaştırmaktadır.

**Çözüm:** TrueScoreAI, doğal dil işleme (NLP) algoritmaları kullanarak yorumların bağlamını anlar. Yorumun ürünün fiziksel özellikleriyle mi yoksa dış faktörlerle mi (teslimat süreci gibi) ilgili olduğunu ayırt ederek, tüketiciye sadece ürün odağında temizlenmiş bir "Gerçek Skor" sunar.

## 📊 Veri Etiketleme & 🔮ML-TL Model Mimarisi
Projenin kalbini, özenle oluşturulmuş veri setimiz ve gelişmiş dil modelimiz oluşturmaktadır:

**Kural Tabanlı Veri Etiketleme:** Yüzlerce e-ticaret yorumu, katı sınıflandırma kurallarına göre analiz edilerek etiketlenmiştir. Geliştirdiğimiz sınıflandırma kriterleri gereği; lojistik, kargo gecikmeleri, paketleme kusurları veya kullanıcının ürünü ilgilendirmeyen(Ör:"Hiç kullanmadım çeyizime attım 1 puan")  gibi durumlar ürün kalitesiyle "alakasız" (irrelevant) olarak kategorize edilmiş ve modelin asıl puanlama hesaplamasından tamamen dışlanmıştır.

**Model Seçimi ve Transfer Learning:** Başlangıçta sınıflandırma görevini geleneksel makine öğrenmesi (ML) algoritmalarıyla (Random Forest, SVM vb.) eğittik; ancak bu modellerle ulaştığımız başarı oranı %90 seviyelerinde sınırlı kaldı. Dilin karmaşık yapısını ve bağlamını çok daha iyi yakalayabilmek için Transfer Learning (Transfer Öğrenme) yaklaşımına geçiş yaptık. Bu aşamada BERTurk, XLM-RoBERTa ve Electra gibi önceden eğitilmiş güçlü dil modellerini kıyasladık. Yapılan performans testleri sonucunda, e-ticaret terminolojisini anlamada %95 - %96 ile en yüksek doğruluk oranını ve kararlılığı sağlayan Electra mimarisinde karar kıldık. Bu geçiş sayesinde, kullanıcı niyetini doğru analiz etme başarımız maksimize edilmiştir.


## 🛠️ Teknolojiler ve Araçlar
**Yapay Zeka & NLP:** Electra Modeli, Transfer Learning

**Backend Altyapısı:** FastAPI, Uvicorn (Yerel sunucu yönetimi ve hızlı uç nokta yapılandırması)

**Veri Toplama/Scraping:** Selenium (Prototip eğitim veri setinin oluşturulması ve toplanması aşamasında)

**Frontend Arayüzü:** HTML / CSS

## ⚙️ Sistem Çalışma Mantığı ve API
TrueScoreAI, sadece teorik bir makine öğrenmesi modeli değil, uçtan uca çalışabilen bir web uygulamasıdır. Backend mimarisi FastAPI ile geliştirilmiş olup, lokal ortamda Uvicorn üzerinden hızlı ve kararlı bir şekilde hizmet vermektedir.

(Sistemin kurumsal standartlarda tasarlanmış API dokümantasyonu - Swagger UI)

## 📊 Model Performansı ve Metrikler
Uyguladığımız Transfer Learning ve titiz etiketleme süreçleri sonucunda modelimiz, ürünle ilgili gerçek yorumları ve alakasız kargo şikayetlerini yüksek doğrulukla ayırt etmektedir.

(Modelin kesinlik (precision), duyarlılık (recall) ve F1-Score metriklerini gösteren performans analizi)

## 💻 Kullanıcı Arayüzü (Demo)
Kullanıcılar, HTML arayüzümüz üzerinden analiz edilmesini istedikleri ürünün linkini girerek, arka planda çalışan FastAPI destekli NLP modeli analiz sonucunu anlık olarak döndürür.

## 🚀 Gelecek Adımlar ve Vizyon
Mevcut prototipte model eğitimi için gereken ham veriler web scraping (Selenium) yöntemleriyle toplanmış olsa da; projenin nihai hedefi büyük e-ticaret platformlarının doğrudan API'leri ile entegre çalışmaktır. Bu vizyonla sistemin; web scraping hantallığından kurtularak çok daha ölçeklenebilir, hızlı ve gerçek zamanlı bir e-ticaret karar destek mekanizmasına dönüşmesi hedeflenmektedir.
