# A/B Testing: Evaluasi Dampak Iklan Terhadap Perilaku Penggun

## 📋 Ringkasan Eksekutif
Analisis ini mengevaluasi efektivitas kampanye iklan dibandingkan iklan layanan masyarakat (PSA) menggunakan metode A/B Testing. Hasil utama menunjukkan:
- **Peningkatan 0.76% conversion rate** pada grup iklan (2.55% vs 1.79% PSA)
- Efektivitas iklan signifikan dipengaruhi **hari penayangan** (terbaik: Jumat/Senin/Sabtu)
- Frekuensi paparan iklan bukan faktor utama konversi (`Quality > Quantity`)

## 📌 Latar Belakang
- **Tujuan**: Mengukur efektivitas kampanye iklan pada periode/platform tertentu
- **Metrik Utama**: Conversion Rate (CR)
- **Batasan**: Data terbatas pada periode tertentu

## ⚙️ Metodologi
Langkah pengujian A/B:
1. Definisikan tujuan dan metrik utama (CR)
2. Formulasi hipotesis
3. Pengacakan grup (kontrol vs eksperimen)
4. Kontrol variabel pengganggu
5. Analisis statistik
6. Interpretasi hasil

## 📊 Deskripsi Data
**Sumber**: [Marketing A/B Testing Dataset](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing) (Kaggle)  
**Struktur Utama**:
- `test_group`: Ads vs PSA
- `converted`: Konversi pengguna (0/1)
- `total_ads`: Jumlah paparan iklan
- `day_of_week`: Hari penayangan

**Tren Kunci**:
1. Distribusi pengguna sangat miring:
   - Mayoritas pengguna paparan <500 iklan
   - Heavy users habiskan 23% budget tanpa konversi ekstra
2. CR tertinggi pada Senin (3.28%), terendah Sabtu (2.11%)

## 🔍 Analisis Statistik
### Uji T-Test (Perbedaan CR)
| Group      | Conversion Rate | P-Value       | Kesimpulan          |
|------------|-----------------|---------------|---------------------|
| **Ads**    | 2.5547%         | 5.11 × 10⁻¹⁸ | Perbedaan signifikan|
| **PSA**    | 1.7854%         |               |                     |

**Insight**: Perbedaan 0.76pp secara bisnis relevan karena skala besar

### Cohen's D (Effect Size)
| Metric           | Nilai | Interpretasi | Dampak Bisnis                  |
|------------------|-------|--------------|--------------------------------|
| Cohen's d        | 0.049 | Sangat kecil | Dampak signifikan di populasi besar |

### ANOVA (Pengaruh Hari)
| Interaksi        | P-Value  | Insight                                  |
|------------------|----------|------------------------------------------|
| Grup × Hari      | 0.0076   | Efektivitas iklan bergantung pada hari   |
| Grup × Jam       | 0.9833   | Jam tayang tidak signifikan              |

**Temuan Kritis**: 
- Kombinasi terbaik: Iklan di Jumat/Senin (CR tinggi)
- Hindari: Iklan di Selasa & PSA semua hari

### Uji Chi-Square
|          | Ads     | PSA     |
|----------|---------|---------|
| **No Conv** | 550,154 | 23,104  |
| **Converted**| 14,423  | 420     |

**Konfirmasi**: Jenis grup berpengaruh signifikan terhadap konversi (p=1.9990e⁻¹³)

## 💡 Insight & Rekomendasi
### Strategi Optimalisasi
1. **Aliokasi Anggaran**:
   - Fokuskan 80% budget pada grup **Ads**
   - Prioritaskan hari **Jumat, Senin, Sabtu**
2. **Segmentasi Audiens**:
   - Utamakan pengguna dengan paparan <500 iklan
   - Batasi alokasi untuk heavy users
3. **Personalisasi Konten**:
   - Kembangkan konten berbeda per hari
   - Eksperimen real-time penempatan iklan

### Rekomendasi Tindakan
```mermaid
graph TD
    A[Start] --> B[Fokus Kampanye di Hari High-Performance]
    B --> C[Optimasi Konten untuk Pengguna Low-Exposure]
    C --> D[Monitor Real-time Performance]
    D --> E[Iterasi Berdasarkan Data Terbaru]
