# 20 kg Kapasiteli Hyperloop Manyetik Levitasyon ve İtki Motorları: 3B Simülasyon, RLC Devre Analizi, Malzeme Seçimi ve ANSYS Maxwell FEA Mühendislik Raporu

**Proje Klasörü:** `/home/evlb/Hyperloop_20kg_Levitasyon_Proje/`  
**Hedef Kaldırma Yükü:** $m = 20.0\text{ kg}$ ($F_g = 196.2\text{ N}$, Pik Kapasite: $42.0\text{ kg} / 412\text{ N}$)  
**Kapsam:** 3 Ayrı 3B Mühendislik Simülasyonu, 4 Farklı Hibrit Levitasyon Topolojisi, Dinamik RLC Eşdeğer Devre Analizi, Türkiye Manyetik/Nüve Malzeme Tedarik Rehberi ve ANSYS Maxwell (2D/3D) FEA Kurulumu.

---

## 1. Yönetici Özeti ve 3 Simülasyonun Mimarisi

Bu projede $20\text{ kg}$ kütleli bir Hyperloop kapsülünü veya test platformunu mekanik temas olmadan havada asılı tutmak (levitasyon) ve doğrusal eksende hareket ettirmek üzere **üç aşamalı 3 boyutlu gerçek zamanlı mühendislik simülasyonu** geliştirilmiştir:

1. **Simülasyon 1 (`Sim1_Tam_Hyperloop_Kapsul_ve_LIM_Motoru_3D`):**
   * **Odak:** Tam araç/kapsül seviyesi dinamik benzetim.
   * **Mimari:** 4 köşede bağımsız aktif U-nüve elektromıknatıs ($4 \times 5\text{ kg} = 20\text{ kg}$), merkezde çift taraflı 3 fazlı Doğrusal İndüksiyon Motoru (**LIM**, 12 oluklu U-V-W sargı + 6082-T6 alüminyum reaksiyon plakası), 4 adet yanal pasif **NdFeB N52 Halbach** merkezleme dizisi ve vakum tüpü aerodinamik basınç modeli ($100\text{ Pa} - 101.3\text{ kPa}$).
2. **Simülasyon 2 (`Sim2_Tek_Parca_Hibrit_U_Nuve_ve_RLC_3D`):**
   * **Odak:** Tek parça **Hibrit U-Nüveli (Hybrid U-Core HEMS)** motorun parametrik 3B CAD boyutlandırılması ve **RLC devre analizi**.
   * **Mimari:** $20\text{ kg}$ yükün tamamını tek başına kaldırabilen hibrit U-çekirdek; nüve boyutları ($W_p, D_c, H_{\text{leg}}, W_{\text{win}}, h_m$), sarım sayısı ($N$), tel çapı ($d_{\text{Cu}}$), seri/paralel sargı bağlantısı ve kapasitans ($C$) değiştikçe 3B CAD modeli, $L(g)$ endüktansı, $R(T)$ direnci, $\tau=L/R$ zaman sabiti, $f_0$ rezonans frekansı ve **B-H mıknatıslanma eğrisi** anlık olarak hesaplanır.
3. **Simülasyon 3 (`Sim3_Dort_Topoloji_ve_ANSYS_Maxwell_FEA_3D`):**
   * **Odak:** Farklı motor topolojilerinin kıyaslanması ve **ANSYS Maxwell (2D/3D)** sonlu elemanlar analizine (FEA) doğrudan veri/kod aktarımı.
   * **Mimari:**
     1. **Hibrit U-Nüve (U-Core HEMS)**
     2. **3-Bacaklı Hibrit E-Nüve (E-Core HEMS)**
     3. **Akı-Odaklamalı Çift-PM Nüve (Flux-Concentrating Dual-PM)**
     4. **Eksenel Simetrik Silindirik Pot-Nüve (Axisymmetric Cup-Core - 2D RZ)**
   * Üzerinde gerçek zamanlı **ANSYS gökkuşağı $|B|$ akı yoğunluğu konturu**, **üçgen FEA mesh ağı** ve tek tıkla **PyAEDT Python (`.py`) kurulum betiği** üreteci yer alır.

---

## 2. Matematiksel Modelleme: Manyetik Relüktans Ağı, Kuvvet ve RLC Denklemleri

### 2.1. Hibrit Manyetik Devre ve Relüktans Denklemi
Sabit mıknatıs (PM) ve bakır bobin sargılarının birlikte yer aldığı hibrit levitasyon motorunda toplam manyetomotor kuvvet ($\mathcal{F}_{\text{toplam}}$):

$$\mathcal{F}_{\text{toplam}}(I) = \mathcal{F}_{\text{PM}} + \mathcal{F}_{\text{bobin}} = \frac{B_r}{\mu_0 \mu_{\text{rec}}} h_m + N_{\text{eff}} I$$

Manyetik devrenin toplam relüktansı ($\mathcal{R}_{\text{toplam}}$), iki kutuplu hava boşluğu relüktansı, sabit mıknatıs iç relüktansı ve doyuma bağlı doğrusal olmayan (nonlinear) demir nüve relüktansının toplamıdır:

$$\mathcal{R}_{\text{toplam}}(g, B) = \underbrace{\frac{2g}{\mu_0 A_{\text{eff}}(g)}}_{\mathcal{R}_{\text{boşluk}}} + \underbrace{\frac{h_m}{\mu_0 \mu_{\text{rec}} A_p}}_{\mathcal{R}_{\text{PM}}} + \underbrace{\frac{l_{\text{demir}}}{\mu_0 \mu_{\text{eff}}(B) A_p k_{\text{stack}}}}_{\mathcal{R}_{\text{demir}}}$$

Burada:
* $g$: Kutup yüzeyi ile üst çelik ray arasındaki anlık hava boşluğu ($\text{m}$)
* $A_p = W_p \cdot D_c$: Tek kutup geometrik kesit alanı ($\text{m}^2$)
* $A_{\text{eff}}(g) = A_p \left(1 + 0.85 \frac{g}{W_p} + 0.45 \frac{g}{D_c}\right)$: Kenar saçaklanma (*fringing flux*) düzeltmeli efektif hava boşluğu alanı
* $k_{\text{stack}}$: Lamine silisli sac paketleme faktörü ($0.95 - 0.97$)
* $\mu_{\text{eff}}(B)$: Nüve doyuma ($B_{\text{sat}}$) yaklaştıkça düşen bağıl geçirgenlik

### 2.2. Elektromanyetik Kaldırma Kuvveti ($F_{\text{mag}}$)
Maxwell gerilme tensöründen (veya sanal iş prensibinden $F = -\frac{\partial W_{\text{mag}}}{\partial g}$) iki kutuplu toplam çekme kuvveti:

$$F_{\text{mag}}(I, g) = \frac{B_g^2 \cdot A_{\text{eff}}(g)}{\mu_0} = \frac{\mu_0 A_{\text{eff}}(g)}{4} \left( \frac{\frac{B_r}{\mu_0 \mu_{\text{rec}}} h_m + N_{\text{eff}} I}{g + \frac{h_m}{2 \mu_{\text{rec}}} + \frac{l_{\text{demir}}}{2 \mu_{\text{eff}}(B) k_{\text{stack}}}} \right)^2$$

**$20\text{ kg}$ ($196.2\text{ N}$) Referans Tasarım Noktası (Simülasyon 2 & 3):**
* $W_p = 36\text{ mm}$, $D_c = 85\text{ mm} \implies A_p = 30.6\text{ cm}^2$ (Toplam 2 kutup alanı $= 61.2\text{ cm}^2$)
* $H_{\text{leg}} = 92\text{ mm}$, $W_{\text{win}} = 68\text{ mm}$, $h_m = 7.5\text{ mm}$ (**NdFeB N52**, $B_r = 1.45\text{ T}$)
* $N = 600\text{ sarım}$ ($1.60\text{ mm}$ bakır tel), Hedef boşluk $g = 6.50\text{ mm}$
* Denge akımı: **$I_{\text{eq}} \approx 3.85\text{ A}$** ($\text{MMK}_{\text{bobin}} = 2310\text{ A}\cdot\text{sarım}$), Bakır kaybı: **$P_{\text{Cu}} = 21.0\text{ W}$**, Nüve akı yoğunluğu: **$B_{\text{core}} = 0.82\text{ T}$** (M19 sacın $1.65\text{ T}$ doyum sınırının yarısında, güvenli doğrusal bölgede!).

### 2.3. Dinamik RLC Eşdeğer Devresi ve Elektriksel Tepki
Bobin endüktansı $L(g)$ hava boşluğunun ters fonksiyonudur:

$$L(g) = \frac{N_{\text{eff}}^2}{\mathcal{R}_{\text{toplam}}(g, B)}$$

Sürücü devresi $R$, $L(g)$ ve paralel/seri bara kondansatörü $C$ ile birlikte 2. mertebeden diferansiyel denklem oluşturur:

$$V_{\text{sürücü}}(t) = I(t) R(T) + L(g) \frac{dI}{dt} + \underbrace{I(t) \frac{dL(g)}{dg} \frac{dg}{dt}}_{\text{Hareket Zıt-EMK'sı } e_{\text{mot}}}$$

* **Elektriksel Zaman Sabiti:** $\tau_e = \frac{L(g)}{R} \approx \frac{118.4\text{ mH}}{1.42\,\Omega} = 83.4\text{ ms}$ (H-köprü $48\text{ V}$ zorlamalı gerilim aşımı *voltage forcing* ile akım yükselme süresi $<6\text{ ms}$'ye düşürülür).
* **Rezonans Frekansı:** $f_0 = \frac{1}{2\pi\sqrt{L(g)C}} \approx 21.3\text{ Hz}$ ($C = 470\,\mu\text{F}$ için).
* **Sönüm Oranı:** $\zeta = \frac{R}{2}\sqrt{\frac{C}{L(g)}}$.

---

## 3. 4 Farklı Hibrit Levitasyon Motor Topolojisinin Kıyaslanması (ANSYS Maxwell İçin)

| Kriter | 1. Hibrit U-Nüve (U-Core) | 2. Hibrit E-Nüve (E-Core - Önerilen) | 3. Akı-Odaklamalı Çift-PM | 4. Silindirik Pot-Nüve (Cup-Core) |
| :--- | :--- | :--- | :--- | :--- |
| **Kutup Sayısı & Akı Yolu** | 2 Kutup, Tek Halka Akı Yolu | 3 Kutup (Merkez Ana + 2 Yan Dönüş) | 3 Kutup (Yatay $\rightarrow\leftarrow$ Çift PM Odaklamalı) | Eşmerkezli Silindirik Merkez + Dış Kovan |
| **Kaçak Akı Oranı (Leakage)** | Orta ($\sim \%12$ uç kaçağı) | **Çok Düşük ($\sim \%4$)** — Bobin pencerede kapalı | Düşük ($\sim \%8$) | **En Düşük ($\sim \%3$)** — Tam kapalı kovan |
| **20 kg İçin Motor Kütlesi** | $9.60\text{ kg}$ | **$8.49\text{ kg}$** | **$8.14\text{ kg}$** | $8.43\text{ kg}$ |
| **20 kg Denge Akımı (@6.5mm)** | $3.85\text{ A}$ ($21.0\text{ W}$) | **$3.10\text{ A}$ ($13.8\text{ W}$)** | **$2.35\text{ A}$ ($8.4\text{ W}$)** | $2.95\text{ A}$ ($12.1\text{ W}$) |
| **ANSYS Çözücü Modu** | `Maxwell 2D (XY)` veya `3D` | `Maxwell 2D (XY Yarım Simetri)` veya `3D` | `Maxwell 2D (XY)` veya `3D` | **`Maxwell 2D Axisymmetric (RZ)`** |
| **İmalat Kolaylığı** | Çok Kolay (Lazer Kesim U-Sac) | Kolay (Standart EI Trafo Sacı Kalıbı) | Orta (Çok Parçalı Kutup Montajı) | Kolay (CNC Torna + Tek Makara Bobin) |

> **Mühendislik Tavsiyesi:** Doğrusal bir ray boyunca hareket edecek Hyperloop kapsülü için **2. Topoloji (Hibrit E-Nüve)** veya **1. Topoloji (Hibrit U-Nüve)**; sabit test düzeneğinde $20\text{ kg}$ yük kaldırma deneyi ve en hızlı ANSYS doğrulaması için ise **4. Topoloji (Silindirik Pot-Nüve, 2D RZ)** veya **2. Topoloji (E-Nüve)** en üstün sonuçları verir.

---

## 4. Türkiye'deki Manyetik ve Nüve Malzeme Tedarikçileri ve Ortalama Fiyatlar (2026)

Detaylı Excel (`.xlsx`) ve LibreOffice Calc (`.ods`) tabloları `02_Malzeme_Tedarik_ve_Maliyet_Tablolari/` klasöründe yer almaktadır. Özet karşılaştırma tablosu:

### 4.1. Ferromanyetik Nüve Malzemeleri
| Malzeme | $B_{\text{sat}}$ | $\mu_r$ | Teknik Farkı | Türkiye Tedarikçileri | Ort. Fiyat (USD / TL) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **M19 / M270-35A Silisli Sac (0.35mm)** | $1.65\text{ T}$ | $4,000$ | Düşük eddy kaybı, hızlı PID tepkisi | Sarıtaş Çelik (Gebze), Bamesa (Kocaeli), Femsan/Temsan Kesim | `$2.90 - $3.80/kg` (`110 - 145 TL/kg`) |
| **M27 / M400-50A Silisli Sac (0.50mm)** | $1.60\text{ T}$ | $3,200$ | En ekonomik ve yaygın motor/trafo sacı | Sarıtaş Çelik, Posco Assan (Kocaeli), Tezcan, Bursa Sac Kesim | `$2.10 - $2.80/kg` (`80 - 108 TL/kg`) |
| **M4 / M5 Grain-Oriented Trafo Sacı** | $1.85\text{ T}$ | $15,000+$ | Hadde yönünde çok yüksek akı ve geçirgenlik | Sarıtaş Çelik, Sönmez Trafo Kesim, Balıkesir/Ankara Trafo Yan Sanayi | `$3.90 - $5.20/kg` (`150 - 200 TL/kg`) |
| **Hiperco 50 (Fe-49Co-2V Alaşımı)** | **$2.35\text{ T}$** | $6,500$ | En yüksek doyum, %35 daha hafif nüve | Voestalpine Böhler Türkiye (İstanbul), VAC Temsilcileri | `$145 - $210/kg` (`5,500 - 8,000 TL/kg`) |
| **SAE 1018 / St37 Karbon Çeliği** | $1.50\text{ T}$ | $1,500$ | Masif CNC işleme ve üst I-profil reaksiyon rayı | Erdemir, Yücel Boru/Profil, Kocaer Çelik, İmes Çelik Merkezleri | `$0.95 - $1.45/kg` (`36 - 55 TL/kg`) |
| **Saf Yumuşak Demir (ARMCO Iron)** | $2.14\text{ T}$ | $5,500$ | Yüksek DC doyum, Pot-Nüve ve kutup pabuçları | AKO Metal, Özel Çelik İthalatçıları (İstanbul) | `$8.50 - $14.00/kg` (`325 - 535 TL/kg`) |

### 4.2. Sabit Mıknatıs (PM) ve Bobin Malzemeleri
| Malzeme | Kritik Değerler | Teknik Farkı | Türkiye Tedarikçileri | Ort. Fiyat (USD / TL) |
| :--- | :--- | :--- | :--- | :--- |
| **Neodimyum NdFeB N52** | $B_r=1.45\text{ T}$, $80^\circ\text{C}$ | Oda sıcaklığında maksimum kuvvet yoğunluğu | Manyet Mıknatıs (İstanbul), Başaran / Miknatis.net, Magneteksan | `$75 - $115/kg` (`2,850 - 4,370 TL/kg`) |
| **Neodimyum NdFeB N42SH** | $B_r=1.32\text{ T}$, **$150^\circ\text{C}$** | Bobin ısınmasında demanyetizasyona tam direnç | Manyet Mıknatıs, Başaran Mıknatıs, Magneteksan | `$95 - $145/kg` (`3,600 - 5,500 TL/kg`) |
| **Samaryum-Kobalt SmCo28** | $B_r=1.08\text{ T}$, **$300^\circ\text{C}$** | Vakum içi yüksek sıcaklık kararlılığı | Manyet Mıknatıs, Magneteksan, Savunma Tedarikçileri | `$160 - $240/kg` (`6,100 - 9,100 TL/kg`) |
| **Sınıf H/C Emaye Bakır Tel (AWG 14)** | $d=1.60\text{ mm}$, $200^\circ\text{C}$ | Yüksek sıcaklık dayanımlı levitasyon sargısı | Emtel Emaye Tel (Kocaeli), Bemka/Prysmian (Bursa), Er-Bakır, Sarkuysan | `$13.50 - $16.80/kg` (`515 - 640 TL/kg`) |

---

## 5. ANSYS Maxwell (2D / 3D) Adım Adım Simülasyon Kurulum Rehberi

1. **Çözücü (Solver) Seçimi:**
   * İlk parametrik tarama için `Maxwell 2D -> Magnetostatic (XY Plane)` seçip Model Depth değerine **$D_c = 85\text{ mm}$** girin.
   * Uç etkilerini (*end-leakage*) görmek için `Maxwell 3D -> Magnetostatic`, dinamik PID + RLC darbe tepkisini görmek için `Maxwell 3D -> Transient` seçin.
2. **Malzeme Tanımlaması:**
   * Nüve için `M19_29G` (Stacking Factor $= 0.96$, Laminasyon yönü `V(3) / Z-axis`) atayın.
   * Sabit mıknatıs için `NdFe35` veya özel `NdFeB_N52` ($B_r = 1.45\text{ T}$, $H_c = -875000\text{ A/m}$) tanımlayıp koordinat sisteminde mıknatıslanma vektörünü U-nüve için `+X`, E-nüve için `+Y` yönüne hizalayın.
3. **Bobin Uyarımı (Excitation):**
   * Kesit yüzeyine (`Coil_Terminal`) `Excitation -> Current` atayın.
   * `Type = Stranded` (çok telli sarım) seçip toplam amper-sarımı **$N \cdot I = 600 \times 3.85 = 2310\text{ Ampere-Turns}$** olarak girin.
4. **Kuvvet ve Endüktans Çıkarımı:**
   * Nüve + Mıknatıs grubunu (veya üst rayı) seçip `Assign Parameters -> Force -> Virtual` tanımlayın.
   * `Assign Parameters -> Matrix` altında bobin akımını seçerek $L(g)$ diferansiyel ve akı bağlantılı (*flux-linkage*) endüktans değerini okutun.
5. **Hava Boşluğu Mesh İyileştirmesi (Kritik):**
   * Hava boşluğu ($g = 6.5\text{ mm}$) bölgesinde en az 8–10 eleman katmanı oluşması için kutup yüzeylerine `Mesh Operations -> Assign -> On Selection -> Length Based` ile **`Max Length = 0.60 mm`** tanımlayın.
