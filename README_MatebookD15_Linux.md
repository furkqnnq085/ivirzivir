
# 🛠️ Huawei MateBook D15 - Linux Yapılandırma Notları

Bu notlar, Huawei MateBook D15 (i5 işlemcili) modelinde **Linux (Arch ve Mint)** kullanırken yaşanan ses ve Bluetooth sorunlarının çözümünü içerir.

---

## ✅ Ses Sorunu Çözümü

**Dosya yolu:** `/etc/modprobe.d/alsa-base.conf`

```bash
options snd-intel-dspcfg dsp_driver=1
# options snd-hda-intel model=dell-headset-multi
```

🔧 Açıklama:  
`dsp_driver=1` parametresi, bazı yeni cihazlarda varsayılan olarak etkin olan SOF (Sound Open Firmware) sürücüsü yerine, klasik ALSA sürücüsünü kullanmaya zorlar. Bu, sesin çalışmasını sağlar.  

`model=` satırı bazı cihazlarda işe yarar, ama soruna yol açarsa yoruma alınabilir (`#` işaretiyle).

---

## ✅ Bluetooth Sorunu Çözümü (Arch Linux İçin)

1. Gerekli paketleri yükle:

```bash
sudo pacman -S bluez bluez-utils
```

2. Gerekli firmware dosyasını yükle (örnek: Realtek için):

```bash
yay -S rtl8761b-fw
```

3. Bluetooth servisini başlat ve sistemle birlikte açılmasını sağla:

```bash
sudo systemctl enable --now bluetooth
```

🔎 Not: Firmware paketi, cihazın `lsusb` çıktısına göre değişebilir.

---

## 🧱 Sistem Bilgisi ve Tanılamalar

Kernel sürümünü kontrol et:

```bash
uname -r
```

Ses sistemi bilgisi al (PulseAudio veya PipeWire):

```bash
pactl info
```

---

## 💾 Faydalı Dosyalar (yedeklemeyi unutma!)

- `/etc/modprobe.d/alsa-base.conf`
- `~/.asoundrc` (varsa)
- Yüklediğin firmware paketlerinin adları (`sof-firmware`, `rtl8761b-fw` vs.)

---

## 📌 Not

Bu yapılandırmalar, Linux Mint 22.1 ve Arch Linux üzerinde test edilmiştir.  
Önceki Linux Mint 21 sürümünde bu ayarlar gerekmeden çalışmış olabilir çünkü kullanılan kernel farklı olabilir.

---

✍️ Derleyen: `furkqnnq`  
📅 Tarih: Mayıs 2025
