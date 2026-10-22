# Her Şeyi Bilen Verity — ilk prototip

Baldi's Basics Plus için BepInEx **5 / Mono** eklentisi kaynak kodu. BepInEx 6 ve IL2CPP desteklenmez. Kesin oyun sürümü uyumluluğu henüz doğrulanmadı.

Verity, oyuncunun üstünde beliren mor bir göz şeklindedir. Oyuncunun konumunu her 12 saniyede bir sahnedeki aktif Baldi karakterlerine `Baldi.Hear` aracılığıyla bildirir. Baldi'nin kendi ses araştırma ve yol bulma davranışı kullanılır; karakter ışınlanmaz. Başka sesler ve oyun durumları bu hedefin önüne geçebilir. Verity bağımsız dolaşan, çarpışması olan bir NPC değildir; konumu bilen görsel bir gözlemcidir. Çok oyunculu oyun desteklenmez.

## Derleme ve kurulum

1. Oyunun Mono sürümüne BepInEx 5 kur ve oyunu bir kez açıp kapat.
2. .NET SDK yükle. PowerShell'de bu klasörden çalıştır:

   ```powershell
   ./build.ps1 -GameDir 'C:\Games\Baldis Basics Plus'
   ```

   Betik oyunun kendi Unity ve BepInEx DLL dosyalarına referans verir; bu dosyaları pakete kopyalamaz. Başarılı derlemeden sonra eklentiyi `BepInEx/plugins/Verity/VerityMod.dll` konumuna kurar. Gerekirse `-GameManagedDir` ile `*_Data/Managed` yolunu belirt.

3. Oyunu aç ve bir okul bölümü başlat. Ayarlar ilk açılışta `BepInEx/config/tr.yusufkodcu.verity.cfg` içine yazılır. Değişiklikten sonra oyunu yeniden başlat.

## Oyun içi doğrulama

- `BepInEx/LogOutput.log` içinde `Verity loaded` mesajını kontrol et. `Unsupported game API` hatası varsa oyun sürümü için uyarlama gerekir.
- Aktif Baldi bulunan okulda oyuncunun üzerinde mor gözün belirdiğini doğrula.
- Ses çıkarmadan başka bir koridora geç, en az 12 saniye bekle ve Baldi'nin bildirilen konumu araştırdığını gözle. Başka seslerin testi etkilemediğinden emin ol.
- Duraklatıldığında bildirim süresi ilerlememeli. Menüye dönüp yeniden bölüm açınca göz tekrar oluşmalı.
- Kaldırmak için oyunu kapatıp `BepInEx/plugins/Verity` klasörünü sil.

Bu bulut ortamında oyun DLL dosyaları, .NET SDK ve oyun çalışma zamanı bulunmuyor. Derleme ve oyun içi test yapılmadı; hazır veya doğrulanmış bir DLL sunulmuyor.
