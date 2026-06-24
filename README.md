# IndoBERTweet — Infrastructure Complaint Classification
## Code-Mixed Sunda-Indonesia | Instagram Dataset

---

## 📌 Overview
Klasifikasi keluhan infrastruktur dari komentar Instagram berbahasa 
campuran Sunda-Indonesia menggunakan **IndoBERTweet** dengan karakterisasi 
ketimpangan kelas berbasis distribusi Bernoulli.

## 📊 Dataset
- **Sumber:** Instagram @donyahmad.munir (Bupati Sumedang)
- **Periode:** 20 Feb 2025 – 5 Mei 2026
- **Total:** 30.525 sampel (post-dedup)
- **Label:** Binary (1 = keluhan infrastruktur, 0 = bukan)
- **Imbalance Ratio:** ≈ 1:12.04
- **Kaggle:** [alifgumelarsm/labelling-akunpejabatpemerintahig](https://www.kaggle.com/datasets/alifgumelarsm/labelling-akunpejabatpemerintahig)

## 🛠️ Model Config
| Parameter | Value |
|---|---|
| Base model | indolem/indobertweet-base-uncased |
| MAX_LEN | 128 |
| Batch size | 16 (effective 64 w/ grad accum) |
| Learning rate | 2e-5 |
| Optimizer | AdamW (wd=0.01) |
| Max epoch | 10 (early stop patience=2) |

## 📈 Results
| Metric | Score |
|---|---|
| F1-Macro | **0.9527** |
| AUC-ROC | **0.9941** |
| Cohen's d | ≈ 4.04 |
| Mann-Whitney U p-value | 1.22×10⁻⁹⁵ |
| Optimal threshold τ* | 0.000426 |
| Wilson CI 95% | [0.0738 ; 0.0797] |

## 🔢 Mathematical Framework
1. Bernoulli characterization → Y ~ Bernoulli(p₁)
2. Wilson Score Confidence Interval
3. Binomial test (stratified split validation)
4. IndoBERTweet fine-tuning + softmax distribution analysis
5. Mann-Whitney U + Cohen's d separability
6. AUC = U/(n₊·n₋) probabilistic equivalence proof
7. Youden's J optimal threshold τ*

## 👤 Author
**Alif Gumelar Syah Moeslim**  
Universitas Sebelas April (UNSAP)  
📧 alifsyammm103@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/alif-gumelar-syah-moeslim-3a84b22a4)
