# Windows ve macOS temiz kurulum

Uygulama, ham veri arşivi ve araştırmacının çalışma profili üç ayrı parçadır.
Uygulama güncellenince arşiv ve kişisel çalışmalar yeniden indirilmez.

## Dosyaları nereden alacağım?

- [Herkese açık indirme deposu](https://github.com/AstrocanX/diplomacy-dashboard-downloads)
- [Windows yükleyicileri](https://github.com/AstrocanX/diplomacy-dashboard-downloads/releases/latest)
- [Türkiye/ABD veri arşivi: 16 ZIP](https://github.com/AstrocanX/diplomacy-dashboard-downloads/releases/tag/data-88567b6e6c3b-20261009)
- Mac yerel derleme için: bu özel deponun `source-v1.4.2` sürümündeki **Diplomacy-Source-1.4.2-r2.zip**. Bu tam pakettir; önceki 8 GB aktarımına veya yamalara ihtiyaç duymaz. Kaynak indirmek için AstrocanX/diplomacy-dashboard erişimi gerekir.

**10 Ekim 2026:** Windows 1.4.2 temiz kurulum düzeltmesi hazırlanmıştır. Mac yükleyicisi, yerel Mac derlemesi ve testi bitmeden hazır sayılmaz. Mac ARM64 (Apple Silicon) ile Intel x64 ayrı hedeflerdir; Windows EXE Mac'te çalışmaz. GitHub'un otomatik `Source code.zip` dosyası, indirme deposunda uygulama kaynaklarını içermez.

## Önce arşivi hazırlayın

Var olan iki veri klasörü uygulamadan ayrı bir yerdeyse yeniden indirmeyin.
Yeni bilgisayarda 16 ZIP'in **tamamını** aynı kalıcı klasöre çıkarın. ZIP'ler ayrı ayrı açılır; birleştirilmez. Öneri: `~/DiplomacyArchive` (Mac), `Belgeler/DiplomacyArchive` (Windows).

```text
DiplomacyArchive/
  data_statedept_full_9h_media/all_posts_deduped.csv
  data_statedept_full_9h_media/media/ ... videos/ ...
  data_tc_disisleri_full_9h_images/all_posts_deduped.csv
  data_tc_disisleri_full_9h_images/media/ ... videos/ ...
```

İki CSV tek başına tüm görsel/video arşivi değildir. İndirme 7,80 GB; açılmış veri yaklaşık 8,18 GB'tır. ZIP ve açılmış kopyalar birlikte tutulacaksa en az 20 GB boş alan ayırın. `SHA256SUMS.txt` ve `data-release-manifest.json` indirme bütünlüğünü denetler. 69 `.part`/`.ytdl` dosyası eski yarım indirmedir; tam medya sayılmaz.

Yeni sürüm başlangıç veritabanını kendisi oluşturur. Ham arşivde AI/insan kodlamaları yoktur; mevcut ekip kayıtları yetkili kullanıcı girişinden sonra **Eşle** ile alınır. Çevrimdışı kullanım için daha önce alınmış yerel profil gerekir. Yeni cihazda internet olmadan eski ekip değerlendirmelerinin görünmesi beklenmez.

## Windows

1. Son sürümün `Diplomacy-Desk-...-win-x64.exe` dosyasını indirin ve çalıştırın. Temiz kurulum için **1.4.2 veya sonrası** kullanın; 1.4.1 eski başlangıç veritabanına ihtiyaç duyuyordu.
2. Başlat menüsünden **Pandemi Döneminde Dijital Diplomasi** uygulamasını açın.
3. İlk açılışta iki veri klasörünü içeren `DiplomacyArchive` klasörünü seçin.
4. Mevcut ekip kullanıcı adınızla ve atanmışsa parolanızla girin, **Eşle** düğmesine basın.
5. Genel bakışta **12.824** gönderi olduğunu, medyanın açıldığını ve kendi yetkinizin doğru geldiğini kontrol edin.

Yükleyici Python/Node/R kurulumu gerektirmez. Windows paketi henüz yayıncı sertifikasıyla imzalı değildir. İndirme kaynağını ve SHA-256 değerini doğrulayın; sistemin güvenlik korumalarını kapatmayın.

## Mac: eski uygulamayı kaldırmadan önce

1. Eski uygulamada **Eşle** yapın; bekleyen değişiklik ve çakışma olmadığını kontrol edin. Uygulama içinden yerel yedek alın.
2. Uygulamayı tamamen kapatın. Finder → Git → Klasöre Git ile `~/Library/Application Support/DiplomacyResearchDesk` klasörünü açın. Tümünü tarihli özel bir yedek klasörüne kopyalayın. Profil oturum içerir; GitHub'a yüklemeyin.
3. Arşiv eski `.app/Contents/Resources/runtime` içindeyse iki veri klasörünü uygulama dışına kopyalayın. Yeni uygulamanın arşiv aktarımı da bu işlemi dosya bütünlüğü kontrolüyle yapar. Kopya doğrulanmadan eski uygulamayı kaldırmayın.
4. Yeni Mac paketi hazır olduktan sonra eski `.app` dosyasını Çöp'e taşıyın. `DiplomacyResearchDesk`, `profiles`, `archive` veya yedekleri silmeyin. Çöp'ü yeni kurulum doğrulanana kadar boşaltmayın.

**Temiz uygulama kurulumu** için aynı profili koruyun. **Tamamen yeni profil** isterseniz, yedeği aldıktan sonra mevcut `profiles/default` klasörünü silmek yerine tarihli başka bir ada taşıyın. Henüz eşitlenmemiş taslaklar, dışa aktarımlar ve cihaz tercihleri Supabase'den geri gelmez; bunlar yerel yedektedir. Yeni profilde mevcut kullanıcı adı/parola ile katılın; otomatik yeni kullanıcı/rol atamayın.

## Mac yükleyicisi üretmek / bir agente vermek

`CODEX-MAC-CLEAN-INSTALL.md` dosyasındaki talimatları kullanın. Tam kaynak ZIP'i önce boş bir geliştirme klasörüne çıkarın. `SOURCE/` içindeki `INSTALL.md`, `MAC-BUILD.md`, `archive-requirements.json` ve `desktop-shell/r-engine/` birlikte gelmelidir. Kullanıcı kayıtları ve ham veriler kaynak ZIP'inde değildir.

Derleme hedef Mac'te yapılır. Xcode Command Line Tools, Python 3.12 ve Node.js gerekir; bunlar son kullanıcıya dağıtılan DMG'nin gereksinimi değildir. Paket üretildikten sonra yeni/geçici bir profille açılış, medya, yerel R motoru, eşitleme ve yeniden başlatma sınanır. İmzalama/noter sertifikası olmadan Mac otomatik kurulumunu etkinleştirmeyin; güvenlik korumalarını kapatmayın.

## Kayıtları nerede tutuyor?

| Platform | Electron uygulamasının araştırma profili |
|---|---|
| Windows | `Belgeler/DiplomacyResearchDesk/profiles/default` |
| macOS | `~/Library/Application Support/DiplomacyResearchDesk/profiles/default` |
| Linux | `~/.local/share/DiplomacyResearchDesk/profiles/default` |

Windows'ta kaynak `desktop.py` doğrudan çalıştırılırsa varsayılanı `%LOCALAPPDATA%` olur; Electron uygulaması Belgeler yolunu kullanır. CLI testlerinde her zaman açık bir `--state-dir` verin. Profil dışa aktarımı, cihaz oturumunu başka işletim sistemine aktarmakla aynı değildir.

**Kontrol listesi:** sürüm doğru → 12.824 gönderi → görsel/video açılıyor → kullanıcı/rol doğru → Eşle başarılı → eski kayıtlar görünüyor → kapatıp açınca korunuyor. Bu adımlar bitmeden eski kopyaları/yedekleri silmeyin.
