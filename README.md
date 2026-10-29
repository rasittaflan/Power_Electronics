<div align="center">

<img src="./assets/banner.svg" alt="Power Electronics — 16 SMPS Topologies Design & Formula Suite Banner" width="100%" />

<br/>

[![Topologies](https://img.shields.io/badge/SMPS_Topologies-16_Converters-ef4444?style=for-the-badge&logo=texas-instruments&logoColor=white)](#)
[![Formulas](https://img.shields.io/badge/Live_Engineering_Formulas-400_Equations-f59e0b?style=for-the-badge)](#)
[![Web Studio](https://img.shields.io/badge/Offline_Web_Studio-HTML5_%7C_MathML_%7C_LaTeX-0284c7?style=for-the-badge)](#)
[![Spreadsheets](https://img.shields.io/badge/Spreadsheets-Excel_(.xlsx)_%7C_Calc_(.ods)-16a34a?style=for-the-badge)](#)

<br/>

[![Launch Live Calculator](https://img.shields.io/badge/🚀_CANLI_HESAPLAYICIYI_AÇ_(LIVE_STUDIO)-TI_16_Canli_Hesaplayici.html-2563eb?style=for-the-badge)](https://raw.githack.com/rasittaflan/Power_Electronics/main/TI_16_Canli_Hesaplayici.html)
[![Launch Interactive Table](https://img.shields.io/badge/⚡_İNTERAKTİF_TABLOYU_AÇ_(LIVE_TABLE)-LaTeX_Studio-7c3aed?style=for-the-badge)](https://raw.githack.com/rasittaflan/Power_Electronics/main/TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html)

<br/>

### 🌐 [**🇬🇧 English Documentation**](#english-documentation) &nbsp;&nbsp;|&nbsp;&nbsp; [**🇹🇷 Türkçe Dokümantasyon**](#turkce-dokumantasyon)

</div>

---

<a id="english-documentation"></a>

# 🇬🇧 Power Electronics — 16 SMPS Topologies Design & Live Formula Suite

> **An end-to-end interactive engineering design toolkit for 16 fundamental Switched-Mode Power Supply (SMPS) DC-DC topologies**, built upon the **Texas Instruments *Power Topologies Handbook* (SLYU036A)** and **TI *Power Topologies Quick Reference Guide* (SLYW038B)**.

---

## ✨ Key Highlights

| Feature | Description |
| :--- | :--- |
| 🖥️ **100% Offline Interactive Web Studios** | Zero dependencies or internet required. Modify any of the **14 input design parameters** and watch **400 engineering equations** update in real time across 16 topologies. |
| 📐 **Embedded Schematics & MathML/LaTeX** | Includes all 16 original TI SLYU036A converter schematics, the full SLYW038B comparison poster, rendered MathML equations, and one-click **LaTeX / Unicode** equation copying. |
| 📊 **Native Spreadsheet Engines (`.xlsx` & `.ods`)** | 16 dedicated topology worksheets containing 400 live spreadsheet formulas with automatic unit scaling, ready for Microsoft Excel and LibreOffice Calc. |
| 💾 **State Persistence & JSON Export** | Save custom converter designs per topology directly in browser `localStorage`, reset to reference defaults at any time, or export full input/output snapshots as `.json`. |
| ✅ **Cross-Verified Calculation Core** | Every JavaScript formula in the HTML calculators has been numerically verified 1-to-1 against the master Excel/ODS engineering workbooks. |

---

## 🧭 Topology Selection & Classification Architecture

```mermaid
flowchart TD
    ROOT["⚡ 16 DC-DC SMPS Topologies<br/>(TI SLYU036A & SLYW038B)"]
    ROOT --> NON_ISO["🔓 Non-Isolated Converters (01–06)"]
    ROOT --> ISO["🔒 Galvanically Isolated Converters (07–16)"]

    NON_ISO --> STEP_DOWN["Step-Down<br/>01. Buck"]
    NON_ISO --> STEP_UP["Step-Up<br/>02. Boost"]
    NON_ISO --> BUCK_BOOST["Step-Up / Step-Down<br/>03. Inverting Buck-Boost<br/>04. SEPIC<br/>05. Ćuk<br/>06. Zeta"]

    ISO --> SINGLE_END["Single-Ended / Flyback & Forward<br/>07. Flyback<br/>08. Two-Switch Flyback<br/>09. Active Clamp Forward<br/>10. Single-Switch Forward<br/>11. Two-Switch Forward"]
    ISO --> PUSH_PULL["Push-Pull Family<br/>12. Push-Pull<br/>13. Weinberg (Current-Fed)"]
    ISO --> BRIDGE["Bridge Converters (High Power)<br/>14. Half-Bridge<br/>15. Full-Bridge<br/>16. Phase-Shifted Full-Bridge (ZVS)"]
```

---

## 📁 Repository File Structure

| File | Format | Live Launch / Download | Purpose & Capabilities |
| :--- | :---: | :---: | :--- |
| **[`TI_16_Canli_Hesaplayici.html`](./TI_16_Canli_Hesaplayici.html)** | `HTML5 / JS` | [**🚀 Launch Live**](https://raw.githack.com/rasittaflan/Power_Electronics/main/TI_16_Canli_Hesaplayici.html) | **Flagship Interactive Design Studio:** Embedded TI schematics, high-res topology comparison poster, offline MathML formulas, `localStorage` persistence, and JSON export. |
| **[`TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html`](./TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html)** | `HTML5 / JS` | [**⚡ Launch Live**](https://raw.githack.com/rasittaflan/Power_Electronics/main/TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html) | **Fast Interactive Table & LaTeX Studio:** Lightweight calculator with instant one-click LaTeX & Unicode formula copy for papers and technical reports. |
| **[`TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx)** | `Excel (.xlsx)` | [**📥 View / Download**](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx) | **Master Engineering Workbook:** 16 topology tabs with 400 active Excel formulas, input cells (`B5:B18`), and automated stress/thermal calculations. |
| **[`TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods)** | `Calc (.ods)` | [**📥 View / Download**](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods) | **LibreOffice / OpenDocument Workbook:** Full open-source office suite compatibility with identical live formula structure. |
| **[`TI_16_HTML_Kontrol_Notlari.md`](./TI_16_HTML_Kontrol_Notlari.md)** | `Markdown` | [**📄 Read Notes**](./TI_16_HTML_Kontrol_Notlari.md) | **Verification & Engineering Notes:** Documents the 1-to-1 parity tests between the Excel workbook and JavaScript engine, plus modeling assumptions. |

---

## 🔌 Covered 16 SMPS Topologies

| # | Topology | Isolation | Conversion Type | Typical Power & Key Engineering Trait | TI Ref |
| :---: | :--- | :---: | :--- | :--- | :---: |
| **01** | **Buck Converter** | Non-Isolated | Step-Down ($V_{out} < V_{in}$) | Continuous output current, low output ripple, no RHPZ | Ch. 3 |
| **02** | **Boost Converter** | Non-Isolated | Step-Up ($V_{out} > V_{in}$) | Continuous input current, pulsating diode current, exhibits RHPZ | Ch. 4 |
| **03** | **Inverting Buck-Boost** | Non-Isolated | Step-Up/Down ($-V_{out}$) | Negative output polarity, single inductor, exhibits RHPZ | Ch. 5 |
| **04** | **SEPIC Converter** | Non-Isolated | Step-Up/Down ($+V_{out}$) | Non-inverting output, series coupling capacitor provides DC blocking | Ch. 6 |
| **05** | **Ćuk Converter** | Non-Isolated | Step-Up/Down ($-V_{out}$) | Continuous input & output currents, capacitive energy transfer | Ch. 7 |
| **06** | **Zeta Converter** | Non-Isolated | Step-Up/Down ($+V_{out}$) | Non-inverting buck-boost with continuous output current & **no RHPZ** | Ch. 8 |
| **07** | **Flyback Converter** | Isolated | Step-Up/Down | < 100 W; coupled inductor stores energy, minimal component count | Ch. 9 |
| **08** | **Two-Switch Flyback** | Isolated | Step-Up/Down | MOSFET voltage stress clamped to $V_{in,max}$; leakage energy recycled | Ch. 10 |
| **09** | **Active Clamp Forward** | Isolated | Step-Down Derived | Active reset allows $D > 0.5$, reduced switch voltage stress | Ch. 11 |
| **10** | **Single-Switch Forward** | Isolated | Step-Down Derived | 100–300 W; third reset winding limits duty cycle ($D_{max} < 0.5$) | Ch. 12 |
| **11** | **Two-Switch Forward** | Isolated | Step-Down Derived | Switches clamped to $V_{in,max}$, high reliability for industrial supplies | Ch. 13 |
| **12** | **Push-Pull Converter** | Isolated | Step-Down Derived | Bidirectional core excitation, low primary conduction loss | Ch. 14 |
| **13** | **Weinberg Converter** | Isolated | Current-Fed Push-Pull | Aerospace & satellite power buses; inherent overcurrent protection | Ch. 15 |
| **14** | **Half-Bridge Converter** | Isolated | Step-Down Derived | 200–500 W; switch voltage stress limited to $V_{in,max}$ | Ch. 16 |
| **15** | **Full-Bridge Converter** | Isolated | Step-Down Derived | > 500 W; maximum transformer utilization, low primary switch stress | Ch. 17 |
| **16** | **Phase-Shifted Full-Bridge (PSFB)** | Isolated | ZVS Full-Bridge | High-power (> 1 kW) Zero-Voltage Switching (ZVS) for high efficiency | Ch. 18 |

---

## 🧮 Mathematical & Engineering Calculation Matrix (14 Inputs → 25 Outputs)

For every topology, entering **14 standard design specifications** ($V_{in,nom}$, $V_{in,min}$, $V_{in,max}$, $V_{out}$, $I_{out}$, $f_{sw}$, $\Delta I_L\%$, $\Delta V_{out}\%$, $V_f$, $\eta$, turns ratio $n = N_p/N_s$, $R_{DS(on)}$, $B_{max}$, $J_{max}$) automatically computes **25 critical engineering outputs**:

1. **Operating Point & Duty Cycle:** Output/input power ($P_{out}, P_{in}$) and nominal/extreme duty ratios ($D_{nom}, D_{max}, D_{min}$).
2. **Magnetics Sizing:** Minimum inductance ($L_{min}$), magnetizing inductance ($L_m$), and CCM/DCM boundary critical inductance ($L_{crit}$).
3. **Semiconductor Stress Analysis:** Inductor, MOSFET, and diode peak ($I_{peak}$), average ($I_{avg}$), and RMS ($I_{rms}$) currents; maximum blocking voltages ($V_{DS,max}, V_{R,max}$).
4. **Capacitor Selection Criteria:** Minimum output/coupling capacitance ($C_{min}$), maximum allowable Equivalent Series Resistance ($ESR_{max}$), and capacitor RMS ripple current ($I_{C,rms}$).
5. **Core & Conductor Geometry:** Magnetic Core Area-Product ($A_p = A_e \cdot A_w$ in $\text{cm}^4$) and copper wire cross-sectional area ($A_{wire}$ in $\text{mm}^2$).
6. **Control Loop & Stability:** Output $LC$ filter resonant frequency ($f_{LC}$), Right-Half-Plane Zero frequency ($f_{RHPZ}$), and recommended maximum crossover bandwidth ($f_{c,max}$).
7. **Thermal & Loss Budget:** MOSFET conduction ($P_{cond}$) and switching ($P_{sw}$) losses, diode conduction loss ($P_D$), total power dissipation ($P_{loss}$), and estimated junction temperature rise ($\Delta T_J$).

---

## 🚀 Quick Start

```bash
# 1. Clone the repository
git clone git@github.com:rasittaflan/Power_Electronics.git
cd Power_Electronics

# 2. Launch the Interactive Design Studio in your default browser (Linux/macOS/Windows)
xdg-open TI_16_Canli_Hesaplayici.html
```

- **Zero Installation:** Simply double-click [`TI_16_Canli_Hesaplayici.html`](./TI_16_Canli_Hesaplayici.html) or [`TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html`](./TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html) to open in any modern web browser.
- **Spreadsheet Workflow:** Open the [`.xlsx`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx) or [`.ods`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods) file and edit the yellow input cells (`B5:B18`) on any topology sheet.

---
---

<a id="turkce-dokumantasyon"></a>

# 🇹🇷 Güç Elektroniği — 16 Anahtarlamalı Güç Kaynağı (SMPS) Topolojisi Tasarım ve Hesaplama Paketi

> **Texas Instruments (TI) *Power Topologies Handbook* (SLYU036A)** ve **TI *Power Topologies Quick Reference Guide* (SLYW038B)** referans dokümanları temel alınarak geliştirilmiş; **16 temel DC-DC anahtarlamalı güç kaynağı (SMPS) topolojisi** için uçtan uca devre elemanı boyutlandırma, stres analizi, manyetik nüve seçimi, kontrol döngüsü kararlılığı ve termal kayıp hesaplamalarını içeren interaktif mühendislik araç seti.

---

## ✨ Öne Çıkan Özellikler

| Özellik | Açıklama |
| :--- | :--- |
| 🖥️ **%100 Çevrimdışı Canlı Web Stüdyoları** | İnternet bağlantısı veya ek kurulum gerektirmez. **14 tasarım girdisinden** herhangi birini değiştirdiğinizde, 16 topolojideki **400 mühendislik denklemi** anında yeniden hesaplanır. |
| 📐 **Gömülü Şemalar & MathML/LaTeX Stüdyosu** | TI SLYU036A el kitabındaki 16 orijinal devre şemasını, SLYW038B karşılaştırma posterini, MathML matematiksel gösterimlerini ve tek tıkla **LaTeX / Unicode** formül kopyalama aracını içerir. |
| 📊 **Canlı Elektronik Tablolar (`.xlsx` & `.ods`)** | Her topolojinin ayrı sekmede yer aldığı, 400 aktif hücre formülüyle çalışan Microsoft Excel ve LibreOffice Calc mühendislik hesap tabloları. |
| 💾 **Tarayıcı Hafızası & JSON Dışa Aktarma** | Yaptığınız tasarımlar topoloji bazında tarayıcı hafızasında (`localStorage`) saklanır; tek tıkla varsayılan değerlere sıfırlanabilir veya `.json` formatında dışa aktarılabilir. |
| ✅ **Birebir Doğrulanmış Hesap Motoru** | Web arayüzündeki JavaScript hesap motoru ile Excel/ODS kaynak dosyalarındaki 400 formül sayısal olarak birebir doğrulanmıştır. |

---

## 📁 Depodaki Dosyalar ve İçerikleri

| Dosya Adı | Format | Canlı Bağlantı / İndir | Açıklama ve Kullanım Amacı |
| :--- | :---: | :---: | :--- |
| **[`TI_16_Canli_Hesaplayici.html`](./TI_16_Canli_Hesaplayici.html)** | `HTML5 / JS` | [**🚀 Canlı Aç**](https://raw.githack.com/rasittaflan/Power_Electronics/main/TI_16_Canli_Hesaplayici.html) | **Gelişmiş Canlı Tasarım Stüdyosu:** 16 topolojinin orijinal devre şemalarını, karşılaştırma posterini, MathML tabanlı matematiksel denklemleri, `localStorage` kaydını ve **JSON dışa aktarma** özelliklerini barındıran kapsamlı tek dosya uygulaması. |
| **[`TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html`](./TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html)** | `HTML5 / JS` | [**⚡ Canlı Aç**](https://raw.githack.com/rasittaflan/Power_Electronics/main/TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html) | **Hızlı İnteraktif Tablo & LaTeX Stüdyosu:** Hafif ve hızlı çalışan, tez ve raporlar için tek tıkla LaTeX/Unicode formül kopyalama özelliğine sahip canlı web tablosu. |
| **[`TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx)** | `Excel (.xlsx)` | [**📥 Görüntüle / İndir**](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx) | **Microsoft Excel Hesap Tablosu:** 16 topoloji sekmesi ve 400 aktif Excel formülü içeren ana mühendislik tablosu. |
| **[`TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods)** | `Calc (.ods)` | [**📥 Görüntüle / İndir**](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods) | **LibreOffice Calc Hesap Tablosu:** Açık kaynak ofis yazılımlarıyla tam uyumlu `.ods` formatındaki canlı formül tablosu. |
| **[`TI_16_HTML_Kontrol_Notlari.md`](./TI_16_HTML_Kontrol_Notlari.md)** | `Markdown` | [**📄 Notları Oku**](./TI_16_HTML_Kontrol_Notlari.md) | **Doğrulama ve Mühendislik Notları:** Excel ile JavaScript hesap motoru arasındaki 400 formülün birebir doğrulama testlerini ve kullanılan mühendislik varsayımlarını açıklayan teknik not. |

---

## 🔌 Kapsanan 16 Güç Kaynağı Topolojisi

| # | Topoloji Adı | İzolasyon | Dönüşüm Tipi | Tipik Güç & Mühendislik Karakteristiği | TI Referansı |
| :---: | :--- | :---: | :--- | :--- | :---: |
| **01** | **Buck Converter** | İzolesiz | Alçaltıcı ($V_{out} < V_{in}$) | Sürekli çıkış akımı, düşük çıkış ripple gerilimi, RHPZ içermez | Bölüm 3 |
| **02** | **Boost Converter** | İzolesiz | Yükseltici ($V_{out} > V_{in}$) | Sürekli giriş akımı, darbeli diyot akımı, kontrol döngüsünde RHPZ bulunur | Bölüm 4 |
| **03** | **Inverting Buck-Boost** | İzolesiz | Alçaltıcı/Yükseltici ($-V_{out}$) | Negatif polariteli çıkış, tek bobinli yapı, RHPZ içerir | Bölüm 5 |
| **04** | **SEPIC Converter** | İzolesiz | Alçaltıcı/Yükseltici ($+V_{out}$) | Pozitif çıkışlı, seri kuplaj kapasitörü ile giriş-çıkış DC izolasyonu | Bölüm 6 |
| **05** | **Ćuk Converter** | İzolesiz | Alçaltıcı/Yükseltici ($-V_{out}$) | Hem giriş hem çıkışta sürekli akım, kapasitif enerji aktarımı | Bölüm 7 |
| **06** | **Zeta Converter** | İzolesiz | Alçaltıcı/Yükseltici ($+V_{out}$) | Pozitif çıkışlı, sürekli çıkış akımlı ve **RHPZ içermeyen** buck-boost | Bölüm 8 |
| **07** | **Flyback Converter** | İzoleli | Alçaltıcı/Yükseltici | < 100 W; kuplajlı endüktör ile enerji depolama, düşük eleman sayısı | Bölüm 9 |
| **08** | **Two-Switch Flyback** | İzoleli | Alçaltıcı/Yükseltici | MOSFET gerilim stresi $V_{in,max}$ ile sınırlı, kaçak endüktans enerjisi geri kazanımlı | Bölüm 10 |
| **09** | **Active Clamp Forward** | İzoleli | Alçaltıcı Türevli | Aktif kenetleme ile $D > 0.5$ çalışma imkanı ve düşük anahtar stresi | Bölüm 11 |
| **10** | **Single-Switch Forward** | İzoleli | Alçaltıcı Türevli | 100–300 W; sıfırlama sargısı nedeniyle görev çevrimi $D_{max} < 0.5$ ile sınırlı | Bölüm 12 |
| **11** | **Two-Switch Forward** | İzoleli | Alçaltıcı Türevli | Anahtar gerilimleri $V_{in,max}$ ile kenetlenir, yüksek endüstriyel güvenilirlik | Bölüm 13 |
| **12** | **Push-Pull Converter** | İzoleli | Alçaltıcı Türevli | Çift yönlü nüve uyarımı, düşük primer iletim kaybı | Bölüm 14 |
| **13** | **Weinberg Converter** | İzoleli | Akım Beslemeli İt-Çek | Uzay ve uydu güç sistemleri; doğal aşırı akım korumalı mimari | Bölüm 15 |
| **14** | **Half-Bridge Converter** | İzoleli | Alçaltıcı Türevli | 200–500 W; anahtar gerilim stresi $V_{in,max}$ seviyesinde | Bölüm 16 |
| **15** | **Full-Bridge Converter** | İzoleli | Alçaltıcı Türevli | > 500 W; maksimum trafo kullanımı ve düşük primer akım/gerilim stresi | Bölüm 17 |
| **16** | **Phase-Shifted Full-Bridge (PSFB)** | İzoleli | ZVS Tam Köprü | Yüksek güçlü (> 1 kW) sistemlerde Sıfır Gerilimde Anahtarlama (ZVS) ile yüksek verim | Bölüm 18 |

---

## 🧮 Hesaplanan Parametreler ve Mühendislik Analizleri (14 Girdi → 25 Çıktı)

Her topoloji için **14 temel tasarım girdisi** ($V_{in,nom}$, $V_{in,min}$, $V_{in,max}$, $V_{out}$, $I_{out}$, $f_{sw}$, $\Delta I_L\%$, $\Delta V_{out}\%$, $V_f$, $\eta$, sarım oranı $n$, $R_{DS(on)}$, $B_{max}$, $J_{max}$) üzerinden **25 çıktı parametresi** otomatik hesaplanır:

1. **Çalışma Noktası & Görev Çevrimi:** Çıkış/giriş gücü ($P_{out}$, $P_{in}$) ve görev çevrimi sınırları ($D_{nom}$, $D_{max}$, $D_{min}$).
2. **Endüktör ve Trafo Boyutlandırma:** Minimum endüktans ($L_{min}$), kuplajlı/mıknatıslanma endüktansı ($L_m$), kritik CCM/DCM sınır endüktansı ($L_{crit}$).
3. **Akım ve Gerilim Stresleri:** Bobin, MOSFET ve diyotlar için tepe ($I_{peak}$), ortalama ($I_{avg}$), etkin ($I_{rms}$) akımlar ve maksimum dayanım gerilimleri ($V_{DS,max}$, $V_{R,max}$).
4. **Kapasitör Seçim Kriterleri:** Giriş/çıkış/seri kuplaj kapasitörleri için minimum kapasitans ($C_{min}$), maksimum eşdeğer seri direnç ($ESR_{max}$) ve RMS ripple akımları ($I_{C,rms}$).
5. **Manyetik ve İletken Tasarımı:** Nüve Alan-Çarpımı ($A_p = A_e \cdot A_w$ $\text{cm}^4$) ve önerilen bakır tel kesiti ($A_{wire}$ $\text{mm}^2$).
6. **Kontrol Döngüsü & Kararlılık:** $LC$ filtre köşe frekansı ($f_{LC}$), Sağ Yarı Düzlem Sıfırı ($f_{RHPZ}$) ve güvenli maksimum kontrol bant genişliği ($f_{c,max}$).
7. **Termal Kayıp Bütçesi:** MOSFET iletim ($P_{cond}$) ve anahtarlama ($P_{sw}$) kayıpları, doğrultucu diyot kayıpları ($P_D$), toplam ısıl kayıp ($P_{loss}$) ve tahmini jonksiyon sıcaklık artışı ($\Delta T_J$).

---

## 🚀 Nasıl Kullanılır?

```bash
# 1. Depoyu bilgisayarınıza klonlayın
git clone git@github.com:rasittaflan/Power_Electronics.git
cd Power_Electronics

# 2. Canlı Tasarım Stüdyosunu varsayılan tarayıcınızda açın
xdg-open TI_16_Canli_Hesaplayici.html
```

- **Web Arayüzü:** Herhangi bir kurulum veya sunucu gerekmez. [`TI_16_Canli_Hesaplayici.html`](./TI_16_Canli_Hesaplayici.html) veya [`TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html`](./TI_16_Guc_Kaynagi_Topolojisi_Interaktif_Tablo.html) dosyasına çift tıklayarak doğrudan tarayıcınızda çalıştırabilirsiniz.
- **Excel / LibreOffice:** [`.xlsx`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.xlsx) veya [`.ods`](./TI_16_Guc_Kaynagi_Topolojisi_Tasarim_ve_Formul_Hesaplayici.ods) dosyasını açıp sarı renkli giriş hücrelerini (`B5:B18`) kendi tasarım değerlerinizle değiştirmeniz yeterlidir.

---

## 📚 References / Referanslar

1. **Texas Instruments**, *Power Topologies Handbook*, Markus Zehendner & Matthias Ulmann, Literature Number: **SLYU036A**.
2. **Texas Instruments**, *Power Topologies Quick Reference Guide*, Literature Number: **SLYW038B**.

---

<div align="center">

**Designed for Power Electronics Engineers, Researchers & Students ⚡**  
**[⬆ Back to Top / Başa Dön](#english-documentation)**

</div>
