# ivirzivir
Huawei MateBook D15 ses ve bluetooth sorunu çözümü
<pre> ## 🛠️ Huawei MateBook D15 - Linux Yapılandırma Notları ### ✅ Ses Sorunu Çözümü **Dosya:** `/etc/modprobe.d/alsa-base.conf` ``` options snd-intel-dspcfg dsp_driver=1 # options snd-hda-intel model=dell-headset-multi ``` ### ✅ Bluetooth Sorunu Çözümü (Arch için) ``` sudo pacman -S bluez bluez-utils yay -S rtl8761b-fw sudo systemctl enable --now bluetooth ``` ### 🧱 Kernel Kontrolü ``` uname -r ``` ### 🗃️ Faydalı Dosyalar - `/etc/modprobe.d/alsa-base.conf` </pre>
