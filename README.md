# Air Quality Prediction with Machine Learning

Bu proje, **India Air Quality Data** veri seti kullanılarak hava kalitesinin
makine öğrenmesi yöntemleri ile modellenmesini amaçlamaktadır.
Çalışma kapsamında hem **regresyon** hem de **ikili sınıflandırma**
problemleri ele alınmış; **SO₂** ve **NO₂** gibi temel hava kirleticileri üzerinden
tahmin ve sınıflandırma analizleri gerçekleştirilmiştir.

## Proje Kapsamı
- Hava kirliliği verilerinin keşifsel analizi
- Veri temizleme ve ön işleme adımları
- Regresyon ve sınıflandırma modellerinin eğitilmesi
- Farklı model ailelerinin performanslarının karşılaştırılması
- Sonuçların literatür ile ilişkilendirilerek yorumlanması

## Veri Seti
- **Kaynak:** Kaggle – *India Air Quality Data*
- **İçerik:**
  - Tarih bilgisi (date)
  - SO₂ ve NO₂ konsantrasyonları
  - Bölge tipi (Residential, Industrial vb.)
  - İstasyon / şehir bilgileri
- Yüksek oranda eksik değer içeren **RSPM, SPM ve PM2.5** sütunları
  temel modelleme aşamasında kapsam dışı bırakılmıştır.

## Ön İşleme Adımları
- Eksik değerlerin **medyan ile doldurulması**
- Tarih bilgisinden **year** ve **month** değişkenlerinin türetilmesi
- Kategorik değişkenlerin kodlanması
- KNN, SVM ve lineer modeller için **StandardScaler** ile normalizasyon
- Sınıflandırma probleminde sınıf dengesizliği için
  **class_weight="balanced"** yaklaşımının kullanılması

## Problem Tanımları
### Regresyon
- **Hedef:** NO₂ (alternatif olarak SO₂) konsantrasyonunun sayısal tahmini
- **Metrikler:** RMSE, MAE, R²

### Sınıflandırma
- **Hedef:**
  - `1` → NO₂ ≥ 40 (kötü hava kalitesi)
  - `0` → Aksi halde
- **Metrikler:** Accuracy, Precision, Recall, F1-score

## Kullanılan Modeller
### Regresyon
- Linear Regression (Normal Denklem & Gradient Descent)
- KNN Regressor
- Linear SVR
- Random Forest Regressor

### Sınıflandırma
- Logistic Regression
- Logistic Regression (balanced)
- KNN Classifier
- Linear SVC
- Random Forest (balanced)
- HistGradientBoostingClassifier
- AdaBoost

## Sonuçlar (Özet)
- **Regresyon:**  
  - RMSE ve R² açısından en iyi performans **Random Forest** modeliyle elde edilmiştir.
  - MAE metriğinde **Linear SVR** en düşük hatayı üretmiştir.
- **Sınıflandırma:**  
  - Accuracy değeri yüksek olsa da sınıf dengesizliği nedeniyle tek başına yeterli değildir.
  - **Logistic Regression (balanced)** ve **Linear SVC**, pozitif sınıf için en yüksek
    **recall** ve **F1-score** değerlerini üretmiştir.

## Klasör Yapısı
- `notebooks/` → Tüm Jupyter Notebook dosyaları
- `data/` → Veri seti ve ön işlenmiş veriler
- `results/` → Grafikler ve performans tabloları
- `report/` → Final proje raporu (PDF)

## Çalıştırma
```bash
pip install -r requirements.txt
jupyter notebook
