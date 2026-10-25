# TİO OTOMASYON
## ABB IRB 6750S-185/3.9 LID Endüstriyel Robot Hücresi
### Siber Güvenlik, Dijital Emniyet ve Regülasyon Uyumluluk (EU CRA & IEC 62443) SWOT Analizi Raporu

**Doküman No:** TIO-OT-SWOT-2026-01  
**Tarih:** 25 Ekim 2026  
**Hazırlayan:** Tio Otomasyon OT Siber Güvenlik ve Emniyet Sistemleri Çalışma Grubu  
**Hedef Sistem:** ABB IRB 6750S-185/3.9 LID Robotik Otomasyon Hücresi (IRC5 / OmniCore V250XT Kontrolör, SafeMove Pro, PROFINET/PROFIsafe)  
**İlgili Standart ve Mevzuat:** EU Cyber Resilience Act (CRA 2024/2847), EU 2023/1230 Makine Yönetmeliği, IEC 62443-3-3 / 4-1 / 4-2, ISO 13849-1, ISO 10218-1/2  

---

### 1. Giriş ve Kurumsal Bağlam

Tio Otomasyon olarak otomotiv ana sanayi, pres besleme, punta kaynağı ve ağır parça transfer hatlarında yüksek hassasiyet ve çevrim hızına sahip robotlu otomasyon hücreleri devreye almaktayız. Envanterimizde ve anahtar teslim projelerimizde yer alan ABB IRB 6750S-185/3.9 LID endüstriyel robotu; 185 kg taşıma kapasitesi, 3.9 metre erişim mesafesi ve gövdeye entegre edilmiş kablolama (Lean ID) mimarisiyle pres hatları ve gövde üretiminde kritik bir operasyonel varlıktır.

Avrupa Birliği'nin yürürlüğe koyduğu Siber Dayanıklılık Yasası (EU CRA) ve 20 Ocak 2027 tarihinde 2006/42/AT direktifinin yerini bütünüyle alacak olan Yeni Makine Yönetmeliği (EU 2023/1230), makine imalatçıları ve sistem entegratörlerine doğrudan hukuki ve teknik sorumluluklar getirmektedir. Yeni mevzuat gereğince:

1. Dijital bileşen barındıran tüm makinelerin yaşam döngüsü boyunca siber saldırılara karşı dayanıklı olması,
2. Donanım ve yazılımlarda güvenli kimlik doğrulama için kriptografik X.509 Açık Anahtar Altyapısı (PKI / CA) kullanılması,
3. Yazılım malzeme listelerinin (SBOM) çıkarılması ve bilinen zafiyetlerin (CVE) aktif olarak yönetilmesi,
4. Yetkisiz erişimlerin emniyet fonksiyonlarını (Functional Safety / SafeMove) devre dışı bırakamayacağının teknik olarak doğrulanması şart koşulmuştur.

Bu SWOT analizi, Tio Otomasyon'un ABB IRB 6750S robotlu üretim hücrelerini yeni yasalara, IEC 62443 standartlarına ve sertifika tabanlı (CA) modern haberleşme altyapısına uyarlarken sahip olduğu içsel dinamikleri ve dışsal çevre faktörlerini netleştirmek amacıyla hazırlanmıştır.

---

### 2. Güçlü Yönler (Strengths)

1. **Donanım ve Kontrolör Kriptografik Desteği:**
   ABB OmniCore ve güncel IRC5 kontrolör serisi; TLS 1.3/1.2, SFTP, IPsec tünelleme, IEEE 802.1X port tabanlı ağ kimlik doğrulama ve X.509 sayısal sertifikaları yerel olarak desteklemektedir. Robot kontrolörünün modern kriptografik protokollere uyumlu olması, ek bir donanım dönüştürücüye ihtiyaç duyulmadan CA sertifikalarının sisteme doğrudan entegre edilmesini sağlamaktadır.

2. **Donanımsal ve Mantıksal Emniyet Ayrımı (SafeMove Pro):**
   Hücre emniyet mimarisi, standart operasyonel PLC mantığından bağımsız çalışan SafeMove Pro güvenlik denetleyicisi ve PROFIsafe protokolü ile korunmaktadır. Robotun güvenli duruşu (STO - Safe Torque Off), hız denetimi (SLS) ve güvenli çalışma alanı sınırlandırmaları donanımsal emniyet çekirdeğinde icra edilmektedir. Bu durum, olası bir ağ saldırısında kontrolörün operasyonel yazılımı manipüle edilse dahi insan hayatını koruyan fonksiyonların fiziksel olarak izole kalmasını temin eder.

3. **RobotStudio Gelişmiş Kimlik ve Yetki Yönetimi (UAS):**
   ABB RobotStudio ortamının sunduğu Kullanıcı Yetkilendirme Sistemi (UAS - User Authorization System), rol tabanlı erişim kontrolü (RBAC) sağlamaktadır. Mühendis, teknisyen ve operatör profillerinin ayrıştırılabilmesi ve konfigürasyon yüklemelerinde dijital imza/sertifika doğrulama adımlarının devreye alınabilmesi firmamızın güvenlik mimarisini güçlendirmektedir.

4. **Tio Otomasyon'un Robotik Entegrasyon Tecrübesi:**
   Mühendislik ekibimizin saha devreye alma, bus haberleşmesi (PROFINET, EtherNet/IP) ve PLC-robot arayüz tasarımı konusundaki uzun yıllara dayanan deneyimi, siber güvenlik protokollerinin üretim çevrim zamanını (cycle time) düşürmeden entegre edilmesine olanak tanımaktadır.

5. **Kurumsal Ağ Segmentasyonu Kabiliyeti:**
   Tio Otomasyon panolarında endüstriyel yönetilebilir switchler ve güvenlik duvarları standart olarak kullanılmaktadır. Hücre içi ağın fiziksel ve mantıksal olarak VLAN yapılarıyla bölünmesi altyapı olarak hazır durumdadır.

---

### 3. Zayıf Yönler (Weaknesses)

1. **Sertifika Yaşam Döngüsü ve Otomasyon Eksikliği:**
   X.509 CA sertifikalarının kontrolöre manuel olarak RobotStudio üzerinden yüklenmesi, sertifika geçerlilik sürelerinin (örneğin 1 veya 2 yıl) takibinde operasyonel risk oluşturmaktadır. Sertifika süresi dolduğunda robotun haberleşmeyi kesmesi sonucu plansız hat duruşlarının meydana gelme riski mevcuttur. SCEP veya EST gibi otomatik sertifika yenileme mekanizmaları henüz sahada devreye alınmamıştır.

2. **Eski Nesil Saha Ekipmanlarının Şifreleme Yetersizliği:**
   Hücre içerisinde robotun tutucusu (gripper), punta pensesi, parça varlık sensörleri veya harici I/O adaları çoğunlukla şifresiz düz metin haberleşen eski protokolleri kullanmaktadır. Robot kontrolörü şifreli haberleşmeyi desteklese de, hücre içi alt ağın uç noktaları şifreleme yeteneğinden yoksundur.

3. **Saha Personeli ve Bakım Teknisyenlerinin PKI Yetkinliği:**
   Fabrika sahasındaki bakım personelinin açık anahtar altyapısı (PKI), özel anahtar (private key) gizliliği, sertifika yetkilisi (CA) kök zincirleri ve mTLS (Mutual TLS) konularındaki farkındalığı yetersizdir. Sahada servis esnasında şifrelerin veya özel anahtarların güvensiz USB belleklerle taşınması riski sürmektedir.

4. **Merkezi Log ve Olay İzleme Eksikliği:**
   Robot kontrolöründe meydana gelen başarısız oturum açma denemeleri, konfigürasyon değişiklikleri veya port taramaları merkezi bir SIEM / Syslog sunucusuna otomatik aktarılmamakta, kontrolörün yerel hafızasında tutulmaktadır. Bu durum adli bilişim ve olay müdahale süreçlerini geciktirmektedir.

5. **Dokümante Edilmiş SBOM (Yazılım Malzeme Listesi) Bulunmayışı:**
   Robot hücresinde kullanılan kontrolör yazılımı (RobotWare), SafeMove firmware ve üçüncü parti yardımcı sürücülerin bileşen bazlı güncel SBOM listeleri kurumsal envanterimizde merkezi olarak indekslenmemiştir.

---

### 4. Fırsatlar (Opportunities)

1. **AB CRA ve Yeni Makine Yönetmeliği ile İhracat Üstünlüğü:**
   Avrupa Birliği'ne ihraç edilecek makinelerde siber güvenlik ve CA kimlik doğrulama zorunlulukları 2027 başında bağlayıcı hale gelecektir. Tio Otomasyon'un bu dönüşümü erken tamamlayarak CE işaretlemesini ve teknik dosyasını IEC 62443 uyumlu hale getirmesi, yerli ve yabancı rakiplerine karşı belirgin bir rekabet avantajı sağlayacaktır.

2. **Siber Güvenli Uzaktan Servis Sözleşmeleri (Katma Değerli Hizmet):**
   Müşterilere sunulan uzaktan arıza tespit ve kestirimci bakım hizmetlerinin mTLS, jump server ve merkezi CA altyapısıyla güvenli hale getirilmesi, Tio Otomasyon için sürekli gelir getiren güvenli SLA (Hizmet Seviyesi Anlaşması) paketlerinin satılmasını mümkün kılacaktır.

3. **Otomotiv Ana Sanayi ve Tier-1 Müşteri Güveni:**
   Büyük otomotiv üreticileri (OEM) tedarik zincirlerinde TISAX ve IEC 62443 standartlarına tam uyum şartı koşmaktadır. ABB IRB 6750S hücresinin doğrulanmış bir CA sertifikasyon mimarisine kavuşturulması, yüksek bütçeli endüstriyel ihalelerde teknik puanımızı doğrudan artıracaktır.

4. **Standardize Edilmiş Hücre Güvenlik Şablonu:**
   Bu robot hücresi için geliştirilecek OpenSSL/PKI sertifika betikleri, ağ zonlama kuralları ve konfigürasyon dosyaları, firmamızın devreye alacağı diğer tüm ABB robot projelerinde hazır bir şablon (blueprint) olarak kullanılabilecektir.

---

### 5. Tehditler (Threats)

1. **Mevzuat Yaptırımları ve CE İptali Riski:**
   CRA kapsamında siber güvenlik gereksinimlerini karşılamayan ürün ve hücrelerin AB pazarına girişi yasaklanacak, uygunsuzluk durumunda 15 milyon Euro veya küresel cironun yüzde 2.5'ine varan idari para cezaları uygulanabilecektir. Ayrıca CE uygunluk beyanının geçersiz kılınması riski mevcuttur.

2. **Ortadaki Adam (MitM) ve Konfigürasyon Manipülasyonu:**
   Mühendislik bilgisayarı ile robot kontrolörü arasındaki hat şifrelenmediği ve çift yönlü kimlik doğrulama (mTLS) uygulanmadığı takdirde; yetkisiz bir aktörün ağa sızarak robotun hareket yörüngelerini, kaynak parametrelerini veya SafeMove sınırlarını değiştirmesi, ciddi fiziksel kazalara ve ekipman kırılmalarına yol açabilir.

3. **Servis Bilgisayarları Üzerinden Tedarik Zinciri Bulaşması:**
   Müşteri fabrikalarına giren servis teknisyenlerinin veya harici taşeronların virüslü dizüstü bilgisayarlarını servis portuna doğrudan takmaları sonucunda fidye yazılımlarının veya zararlı kodların kontrolöre bulaşma tehlikesi bulunmaktadır.

4. **Kriptografik Algoritmaların Eskimesi ve Anahtar Yönetimi Zaafı:**
   Kullanılan kök sertifikaların veya anahtarların (örneğin zayıf hash fonksiyonları veya yetersiz anahtar uzunlukları) zamanla güvenlik açıklarına maruz kalması veya özel anahtarların kurum dışına sızdırılması durumunda tüm hücre güvenlik mimarisinin çökmesi riski mevcuttur.

---

### 6. Stratejik Değerlendirme ve Eylem Planı (TOWS Matrisi)

| Kategori | Stratejik Yaklaşım ve Eylemler |
| :--- | :--- |
| **SO Stratejileri**<br>*(Güçlü Yönleri Kullanarak Fırsatları Değerlendirme)* | • ABB kontrolörün yerel TLS ve mTLS kabiliyeti kullanılarak Tio Otomasyon bünyesinde çift seviyeli (Root CA + Intermediate CA) bir PKI altyapısı kurulmalı ve AB CRA uyumu pazarlama gücüne dönüştürülmelidir.<br>• SafeMove Pro ayrık emniyet mimarisi referans gösterilerek otomotiv OEM şartnamelerindeki en üst siber-fiziksel güvenlik puanı hedeflenmelidir. |
| **WO Stratejileri**<br>*(Zayıf Yönleri Fırsatlarla Giderme)* | • Sertifika süre takibini otomatikleştirmek için RobotStudio API veya SNMP/Syslog tabanlı erken uyarı sistemi yazılmalı, böylece plansız hat duruşları engellenmelidir.<br>• Bakım teknisyenleri için "Saha PKI ve Anahtar Hijyeni" konulu iç eğitim programı başlatılmalıdır.<br>• Hücredeki tüm donanım ve yazılımlar için CycloneDX formatında SBOM oluşturulmalı ve CVE açıkları periyodik izlemeye alınmalıdır. |
| **ST Stratejileri**<br>*(Güçlü Yönlerle Tehditleri Bertaraf Etme)* | • Mühendislik yazılımı (RobotStudio) ile robot arasına X.509 istemci sertifikası zorunluluğu getirilerek sahte servis bilgisayarlarının robota parametre yüklemesi kesin olarak engellenmelidir.<br>• Ağ segmentasyonu yetkinliği kullanılarak robot hücresi fabrikadan bağımsız bir Industrial DMZ arkasına alınmalı, doğrudan internet çıkışları kapatılmalıdır. |
| **WT Stratejileri**<br>*(Zayıf Yönleri Azaltıp Tehditlerden Korunma)* | • Eski sensör ve I/O cihazlarının bulunduğu alt hatlar, şifrelenmiş kontrol hattından VLAN ve endüstriyel güvenlik duvarı kuralları ile tamamen tecrit edilmelidir.<br>• Robot kontrolörünün yerel denetim kayıtları (audit log) harici bir güvenli sunucuya syslog üzerinden anlık aktarılmalı, log silme veya resetleme durumunda kanıt kaybı önlenmelidir. |

---

### 7. Sonuç ve Yönetici Özeti

Tio Otomasyon'un ABB IRB 6750S-185/3.9 LID robot hücresi; donanım kalitesi, hareket kabiliyeti ve SafeMove emniyet mimarisi bakımından uluslararası standartlarda güçlü bir temele sahiptir. Ancak EU Cyber Resilience Act ve EU 2023/1230 yönetmeliklerinin getirdiği yeni yasal zorunluluklar, siber güvenliğin artık opsiyonel bir iyileştirme değil, makinenin CE işaretinin ve yasal uygunluğunun asli bir parçası olduğunu ortaya koymaktadır.

Bu doğrultuda ivedilikle atılması gereken üç somut mühendislik adımı şunlardır:
1. Kurumsal X.509 Kök ve Ara Sertifika Yetkilisi (CA) mimarisinin devreye alınması ve robota mTLS ile bağlanılması,
2. IEC 62443 standardına uygun Zone ve Conduit mimarisinin hücre panosunda fiziksel olarak uygulanması,
3. Yazılım Malzeme Listesi (SBOM) ve Olay Müdahale (Incident Response) prosedürlerinin teknik dosyaya dahil edilmesi.

