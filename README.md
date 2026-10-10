# Pandemi Döneminde Dijital Diplomasi

Türkiye ve ABD’nin Sosyal Medya Kullanımı · TÜBİTAK araştırma uygulaması

## Buradan başlayın

**[Windows / Mac kurulum rehberi](INSTALL.md)** · **[Mac’i temiz kurma ve kayıtları koruma](INSTALL.md#mac-eski-uygulamayı-kaldırmadan-önce)** · **[Agent için Mac talimatı](CODEX-MAC-CLEAN-INSTALL.md)**

| İhtiyacınız | Dosyalar |
|---|---|
| Windows x64 | [Son sürümün EXE yükleyicisi](https://github.com/AstrocanX/diplomacy-dashboard-downloads/releases/latest) — 1.4.2 veya sonrası |
| Mac Apple Silicon (M1/M2/M3/M4…) | ARM64 DMG — yerel derleme/test tamamlanınca aynı sürüm sayfasında |
| Mac Intel | x64 DMG — yerel derleme/test tamamlanınca aynı sürüm sayfasında |
| Tweet, resim ve video arşivi | [16 ZIP veri arşivi](https://github.com/AstrocanX/diplomacy-dashboard-downloads/releases/tag/data-88567b6e6c3b-20261009) |
| Mac'te geliştirme / kendi paketinizi üretme | [Tam özel kaynak paketi](https://github.com/AstrocanX/diplomacy-dashboard/releases/tag/source-v1.4.2): Diplomacy-Source-1.4.2-r2.zip; kaynak deposu erişimi gerekir |

Uygulama yükleyicisi **veri arşivi içermez**. 16 ZIP'i bir kez aynı kalıcı klasöre çıkarın; ilk açılışta iki veri klasörünü içeren klasörü seçin. Var olan dış arşivi yeniden indirmeyin. 12.824 gönderi / 9.650 kaynak dosyası. ZIP ve açılmış arşiv için en az 20 GB boş alan ayırın.

Ham arşivde araştırmacı/AI kodlamaları yoktur. Mevcut kullanıcı adınız ve atanmışsa parolanızla girin, **Eşle** yapın. Ekip kararları Supabase'den gelir; profil ve çevrimdışı kayıtlar bilgisayarınızda korunur. Yeni kullanıcı kendi hesabıyla katılır. Başkasının profilini kopyalayarak oturum/yetki devralmayın.

**Mac’te eski uygulamayı silmeden önce** profili ve uygulama içindeki medyayı yedekleyin. Uygulama kaldırmak `DiplomacyResearchDesk` klasörünü silmek değildir. Ayrıntılı adımlar INSTALL.md içindedir.

## Dosyaları karıştırmayın

- `...win-x64.exe`: Windows yükleyicisi.
- `...mac-arm64.dmg`: Apple Silicon Mac yükleyicisi; yalnız yayımlandığında indirin.
- `...mac-x64.dmg`: Intel Mac yükleyicisi; yalnız yayımlandığında indirin.
- `Diplomacy-Data-00...15...zip`: ayrı açılan ham veri parçaları; tümü gerekir.
- `latest.yml`, `.blockmap`: uygulamanın güncelleme yardımcıları; elle açmayın.
- `release-artifacts*.json`, `SHA256SUMS.txt`: boyut ve SHA-256 denetimi.
- GitHub'un otomatik **Source code.zip** dosyası bu indirme deposunda uygulama kaynaklarını içermez.

Uygulama dosyaları yayıncı sertifikasıyla imzalanmamış olabilir; sürüm açıklamasını ve SHA-256'sını doğrulayın. Mac otomatik kurulum için Developer ID / noter gerekir. Güvenlik korumalarını kapatmayın. Kaynak geliştirme paketi özel kaynak deposunda kalır; bu depo kullanıcı oturumu veya araştırma veritabanı içermez.
