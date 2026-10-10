# Tam kaynaktan Mac paket üretimi

Bu rehber önceki Mac kaynak/yama dosyalarını gerektirmez. Özel kaynak sürümü `source-v1.4.2` içindeki `Diplomacy-Source-1.4.2-r2.zip` dosyasını açın ve `SOURCE/` klasöründe Terminal başlatın. Apple Silicon için `uname -m` → `arm64`; Intel için → `x86_64`. Python ve Node aynı yerel mimaride çalışmalı; hedef mimariyi Windows'tan üretmeyin.

Gerekenler: Xcode Command Line Tools (`xcode-select --install`, yoksa), Python 3.12 (`python3.12`), Node.js/npm. Resmî sağlayıcıları kullanın. Arşivi derleme klasörüne kopyalamak gerekmez; beklenecek veri kimliği `archive-requirements.json` içinde sabittir.

```sh
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements-build.txt
(cd desktop-shell && npm ci)
.venv/bin/python build-desktop.py --no-archive --without-data
.venv/bin/python build-release.py
```

Çıktı: `dist/app-only-1.4.2-Darwin-arm64/` veya `...-x64/` içinde **DMG**, **ZIP**, `latest-mac.yml`, `release-artifacts.json`. Uygulama veriden bağımsızdır ve webR/nlme yerel motoru tam kaynak paketinde gelir. Önceki küçük yamalar motorun tamamını içermiyordu; temiz derleme için onları kullanmayın.

Derlenen `.app` dosyasını önce arşiv hazır olan hedef Mac'te geçici ayrı profil ile açın:

```sh
open -n '/tam/yol/Pandemi Döneminde Dijital Diplomasi.app' --args --state-dir "$HOME/DiplomacyTestProfile-1.4.2" --data-dir "$HOME/DiplomacyArchive"
```

Gerçek profili bu teste vermeyin. 12.824 gönderi, metin, resim/video, pencere yeniden açılması ve `desktop-shell/r-engine/run.cjs` içindeki `health()` (R/nlme çevrimdışı) doğrulanmalıdır. Yalnızca eski profilden veri alma yeterli temiz kurulum testi değildir. Ekip eşitlemesini yeni bir test hesabı yaratmadan, kullanıcı yetkisiyle gerçek kurulum sonrasında kontrol edin.

Developer ID imzası ve noter yoksa dağıtımı **imzasız / manuel kurulum** olarak belirtin. Sertifika/belgeyi ZIP'e veya repoya koymayın. Supabase Mac otomatik güncelleme kaydı, imzalı/noterlenmiş ZIP ve `latest-mac.yml` GitHub'a yüklenip bütünlüğü doğrulanmadan etkinleştirilmez. Intel ve Apple Silicon güncelleme dosyalarını birbirinin üzerine yazmayın. Windows `release-artifacts.json` dosyasını korumak için Mac manifestini `release-artifacts-darwin-arm64.json` veya `...-x64.json` adıyla yayımlayın.

## Depo ve paket sorumlulukları

Kaynak deposu özeldir; erişimi olan kullanıcı/agent tam kaynak ZIP'ini indirebilir. Halka açık indirme deposunda kaynak kod yerine son kullanıcı yükleyicileri ve ham arşiv bulunur. Tam kaynak ZIP'inin SHA-256 bilgisi sürüm açıklamasındaki değerle karşılaştırılır. `source-manifest.json` dosyasındaki her dosya özeti de denetlenebilir. Özel kaynak ZIP'ini indirme deposuna yanlışlıkla yüklemeyin.
