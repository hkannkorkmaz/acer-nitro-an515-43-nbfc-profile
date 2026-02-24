# Acer Nitro 5 AN515-43 – Balanced Silent NBFC Thermal Profile

**Model:** Acer Nitro 5 AN515-43
**CPU:** AMD Ryzen 5 3550H
**GPU:** AMD Radeon RX 560X
**Author:** Zion

---

## 📌 Purpose of This Project

This configuration exists because stock laptop fan curves are **not designed for thermal stability, VRM safety, or acoustic balance** – they are designed for warranty safety margins and generic usage scenarios.

This profile was created after **hours of real stress testing, thermal observation, EC behavior analysis, and acoustic tuning**.

It is not a “silent at all costs” profile.
It is not a “max cooling at all costs” profile.

It is a:

> **Thermally stable, VRM-safe, acoustically smooth, hardware-respecting balanced profile.**

---

## 🧠 Design Philosophy

### Why fans never fully stop

Many users aim for "0 RPM below 40°C" for absolute silence.

That logic is **dangerous in laptops**.

Because:

* VRMs (Voltage Regulator Modules) have **no sensors**
* Heatpipes store thermal energy
* Copper pipes re-radiate heat even after CPU cools
* Laptop airflow is **shared cooling**, not isolated cooling

So even if:

* CPU = 38–40°C

VRMs can still be:

* 55–60°C silently

Fan stop = heat soak trap.

This profile enforces:

> **Minimum continuous airflow** to prevent VRM heat accumulation.

That’s why fans never go to 0 RPM.
That’s intentional.
That’s protection, not inefficiency.

---

## ⚙️ Control Logic

The curve is built on:

* Gradual ramp-up
* No aggressive jumps
* No hysteresis oscillation
* No sudden acoustic spikes

### Key principles:

* Linear thermal response
* Smooth acoustic transitions
* EC-friendly step changes
* Shared CPU/GPU airflow balance

There is a special **smoothing zone** between:

> 65°C → 75°C

This prevents:

* sudden fan ramp noise
* oscillation loops
* EC overcorrection

---

## 🔥 Temperature Behavior Ranges

| Temp Range | Behavior                     |
| ---------- | ---------------------------- |
| 0–45°C     | Idle airflow, VRM protection |
| 45–60°C    | Silent cooling zone          |
| 60–70°C    | Balanced ramp                |
| 70–75°C    | Load stabilization           |
| 75–80°C    | Performance cooling          |
| 80–85°C    | Aggressive cooling           |
| 85°C+      | Full protection mode         |

---

## 🧩 Software Requirement

This config **requires NBFC (Notebook FanControl)**.

### Install NBFC

### Arch / Manjaro / EndeavourOS:

```bash
yay -S nbfc-linux
```

or

```bash
paru -S nbfc-linux
```

### Ubuntu / Debian:

```bash
sudo apt install nbfc
```

---

## 📂 Config File Placement

NBFC config directories differ by install method:

### AUR Install (yay / paru):

```bash
/opt/nbfc/configs/
```

### Pacman / System Package:

```bash
/etc/nbfc/configs/
```

---

## 🧪 Usage

1. Copy the config file into NBFC configs folder
2. Load profile:

```bash
sudo nbfc config --set "Acer Nitro 5 AN515-43 Balanced Silent"
```

3. Enable service:

```bash
sudo nbfc start
```

4. Check status:

```bash
nbfc status --all
```

---

## 🛡️ Safety

Critical temperature limit:

```
90°C
```

Manual EC unlock registers are included for:

* CPU fan
* GPU fan

So NBFC has **real hardware control**, not fake software scaling.

---

## ❗ Disclaimer

This profile is:

* Model specific
* EC specific
* Hardware specific

Only guaranteed safe for:

> Acer Nitro 5 AN515-43
> Ryzen 5 3550H
> Radeon RX 560X

Do NOT use on other models.

---

## 🧬 Philosophy

This is not a "fan curve".

This is a **thermal behavior model**.

Not noise-chasing.
Not benchmark-chasing.

**System health first.**
**Component longevity first.**
**Stability first.**

---

## ✍️ Author Note

This configuration was not generated.
It was:

* observed
* tested
* measured
* stressed
* refined
* iterated

Real hardware.
Real thermals.
Real behavior.

Built by: **Zion**

---

## ⭐ Contribution

If you improve it:

* test under stress
* document behavior
* never remove VRM airflow logic
* never add 0 RPM zones

Thermal systems are not aesthetics.
They are physics.




Acer Nitro 5 AN515-43 – Balanced Silent Fan Control Profile
(Ryzen 5 3550H & Radeon RX 560X)

Bu repo, Acer Nitro 5 AN515-43 modeli için özel olarak hazırlanmış,
NBFC (Notebook FanControl) uyumlu, optimize edilmiş bir fan kontrol konfigürasyonunu içerir.

Amaç:

Sessizlik

Termal stabilite

Donanım güvenliği

VRM/BRM ısı yönetimi

Laptop soğutma mimarisine uygun fan davranışı

Gerçek kullanım senaryolarına uygun termal eğri

Bu bir “fan curve” dosyası değil,
termal davranış modelidir.

🎯 Tasarım Felsefesi

Laptop soğutma sistemleri masaüstü gibi çalışmaz.

Özellikle:

VRM / BRM bileşenleri

Bakır ısı boruları (heatpipe)

Paylaşımlı soğutma blokları

Kapalı kasa yapısı

şu gerçeği doğurur:

CPU 40°C olsa bile, VRM/BRM 55–60°C olabilir.

Bu yüzden fanları tamamen durdurmak:

İç ısı birikimine,

Isının kasada hapsolmasına,

VRM stresine,

Uzun vadede donanım yıpranmasına neden olur.

Bu konfigin temel prensibi:

❌ Mutlak sessizlik
✅ Sürekli düşük devir + kontrollü akış
✅ Termal denge
✅ Isı birikimini önleme
✅ Uzun vadeli donanım sağlığı

Yani:

Fanlar hiçbir zaman tamamen durmaz
Ama her zaman minimum seviyede çalışır.

🧠 Çalışma Mantığı
Termal Kontrol Modeli:

Kademe kademe artış (smooth curve)

Ani sıçrama yok

Fan spike yok

Gereksiz bağırma yok

Termal osilasyon yok

Histerezis (Up/Down threshold) dengeli

Davranış:
Sıcaklık	Fan Davranışı
0–45°C	Minimum devir (sessiz akış)
50–60°C	Hafif aktif soğutma
65–70°C	Dengeli soğutma
75°C	Agresif soğutma
80°C	Yüksek soğutma
85°C+	Maksimum güvenlik modu
🌡 Fan Curve (Özet)
0°C   → 10%
45°C  → 15%
50°C  → 20%
55°C  → 28%
60°C  → 35%
65°C  → 45%
70°C  → 55%
75°C  → 70%
80°C  → 80%
85°C+ → 100%

Bu eğri:

Sessizlik

Stabilite

Termal güvenlik

Donanım ömrü

Laptop mimarisi
dengesi üzerine kuruludur.

🔧 Gereksinimler

Bu konfigin çalışması için:

1️⃣ NBFC (Notebook FanControl)

NBFC kurulu olmalıdır.

Kurulum:
Arch Linux / AUR:
yay -S nbfc-linux

Kurulum yolu:

/opt/nbfc/

Config dizini:

/opt/nbfc/Configs/
Pacman / Repo:
sudo pacman -S nbfc

Config dizini:

/etc/nbfc/Configs/
📁 Kurulum Adımları

Bu repodaki .xml config dosyasını alın

NBFC config klasörüne kopyalayın:

AUR için:

/opt/nbfc/Configs/

Pacman için:

/etc/nbfc/Configs/

Config seç:

sudo nbfc config -s "Acer Nitro 5 AN515-43 Balanced Silent"

Servisi başlat:

sudo nbfc start

Durumu kontrol et:

nbfc status --all
🧪 Test Edilmiş Senaryolar

Idle kullanım

Web / günlük kullanım

CPU stress test

Uzun süreli yük

Isınma-soğuma döngüleri

Termal geçiş testleri

Fan ramp testleri

Stabilite testleri

Sonuç:

Termal spike yok

Fan dalgalanması yok

Gürültü patlaması yok

Isı birikimi yok

Stabil çalışma

Dengeli soğutma

⚠️ Önemli Notlar

Bu config sadece Acer Nitro 5 AN515-43 modeli içindir

Farklı modelde register adresleri farklı olabilir

Yanlış modelde kullanmak donanıma zarar verebilir

VRM sensörü olmadığı için bu yapı önleyici soğutma mantığıyla çalışır

“Fan kapatma” yapılmamasının sebebi budur

📌 Amaç

Bu repo:

“Fan sesi kapatayım” yaklaşımı değil

“Laptopu sağlıklı yaşatayım” yaklaşımıdır

Sessizlik uğruna donanım riske atılmaz.
Bu konfig:

sessizlik + sağlık + denge + mühendislik

üzerine kuruludur.

👤 Yazar

Zion

Tasarım:

Termal denge modeli

Laptop mimarisi analizi

VRM/BRM ısı davranışı

Heatpipe fiziksel ısı yayılımı

Uzun süreli donanım sağlığı yaklaşımı

📄 Lisans

Bu proje açık kaynak olarak paylaşılmıştır.
Serbestçe kullanılabilir, geliştirilebilir ve paylaşılabilir.
Ancak:

Kaynak belirtilmesi rica edilir

Orijinal model bilgisi korunmalıdır
