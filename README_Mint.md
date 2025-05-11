
# 🟢 Huawei MateBook D15 - Linux Mint Ses ve Bluetooth Çözümü

Bu rehber, Huawei MateBook D15 (i5) modelinde **Linux Mint 22.1** üzerinde ses ve Bluetooth sorunlarını çözmek için hazırlanmıştır.

---

## 🔊 Ses Sorunu Çözümü

Bazı kernel sürümlerinde ses çalışmayabilir. Bu durumda ALSA sürücüsünü manuel seçerek çözüm sağlanabilir.

### 1. Dosyayı oluştur veya düzenle:

```bash
sudo nano /etc/modprobe.d/alsa-base.conf
```

### 2. Dosyanın en altına şunu ekle:

```bash
options snd-intel-dspcfg dsp_driver=1
```

> 💡 Eğer satır varsa tekrar yazma. Varsa `model=dell-headset-multi` gibi satırları yorum satırı (`#`) yapabilirsin.

### 3. Bilgisayarı yeniden başlat:

```bash
reboot
```

---

## 📶 Bluetooth Sorunu Çözümü

1. Gerekli Bluetooth servislerinin yüklü ve etkin olduğundan emin ol:

```bash
sudo apt update
sudo apt install bluez
sudo systemctl enable --now bluetooth
```

2. Bluetooth yöneticin açılıyor mu kontrol et (`blueman` varsa):

```bash
blueman-manager
```

> Eğer çalışmıyorsa `blueman` paketini kurabilirsin:

```bash
sudo apt install blueman
```

---

## 🔍 Tanılama ve Kontrol

- Yüklü kernel sürümünü görmek için:

```bash
uname -r
```

- Ses sisteminin çalışıp çalışmadığını kontrol etmek için:

```bash
pactl info
```

- Bluetooth cihazlarının bağlı olup olmadığını görmek için:

```bash
bluetoothctl
```

---

## ✅ Test Edilen Sürüm

- **Linux Mint 22.1 (kernel 6.x)**
- Cihaz: *Huawei MateBook D15, Intel i5*

---

✍️ Hazırlayan: `furkqnnq`  
📅 Tarih: Mayıs 2025
