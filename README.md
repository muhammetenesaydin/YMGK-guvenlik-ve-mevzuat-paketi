# TİO OTOMASYON
## ABB IRB 6750S-185/3.9 LID Endüstriyel Robot Hücresi
### Siber Güvenlik, X.509 CA Sertifikasyonu ve Safety 4.0 Uyumluluk Projesi

Bu depo; Tio Otomasyon bünyesinde entegre edilen ABB IRB 6750S-185/3.9 LID endüstriyel robot hücresinin, Avrupa Birliği Siber Dayanıklılık Yasası (EU Cyber Resilience Act - CRA), Yeni Makine Yönetmeliği (EU 2023/1230) ve IEC 62443 serisi standartlara tam uyumlu hale getirilmesi amacıyla hazırlanmış dokümantasyon, analiz ve kriptografik altyapıyı içermektedir.

---

### Depo Yapısı ve Dizinler

```text
.
├── swot_analizi/
│   ├── SWOT_Analizi_Tio_Otomasyon_ABB_IRB_6750S.md     # Kapsamlı teknik SWOT analizi raporu
│   └── SWOT_Analizi_Tio_Otomasyon_ABB_IRB_6750S.docx   # Resmi Word formatında SWOT analizi
├── laboratuvar_foyleri/
│   ├── Hafta_01_LAB_1_Safety_Architecture.docx        # Safety Architecture (EP 03)
│   ├── Hafta_02_LAB_2_IEC_62443_Mini_Workshop.docx     # Zone / Conduit Diagram (EP 05)
│   ├── Hafta_03_LAB_3_Threat_and_Risk_Matrix.docx      # Risk Register (EP 04)
│   ├── Hafta_04_LAB_4_Secure_Remote_Access.docx        # Secure Remote Architecture (EP 02 + 06)
│   ├── Hafta_05_LAB_5_SBOM_CVE_Patch.docx              # Vulnerability Decision (EP 09-11)
│   ├── Hafta_06_LAB_6_CRA_Incident_Simulation.docx     # Incident Workflow (EP 13)
│   ├── Hafta_07_LAB_7_AI_Safety_Challenge.docx         # AI Fail-Safe Decision (EP 03 + 15)
│   └── README.md                                       # Laboratuvar föyleri fihristi
└── ca_sertifikasyon/
    ├── openssl_root_ca.cnf                             # 4096-bit Kök CA konfigürasyonu
    ├── openssl_intermediate_ca.cnf                     # 3072-bit Operasyonel Ara CA konfigürasyonu
    ├── openssl_robot.cnf                               # ABB Robot SAN ve sunucu uzantıları
    ├── openssl_client.cnf                              # RobotStudio mTLS istemci uzantıları
    ├── generate_pki_certs.sh                           # Otomatik sertifika üretim ve test betiği
    └── README_PKI_Kurulum_Rehberi.md                   # OmniCore / IRC5 yükleme kılavuzu
```

---

### Temel Çıktılar

1. **Kurumsal SWOT Analizi:**
   - İnsan yazımı üslubuyla, teknik ve sahadan gerçekçi değerlendirmelerle hazırlanmıştır.
   - Güçlü, zayıf yönler, fırsatlar, tehditler ve TOWS matrisi içerir.
   - Hem Markdown hem de Word formatında sunulmuştur.

2. **Haftalık Laboratuvar Föyleri (Safety 4.0):**
   - Hafta 1'den Hafta 7'ye kadar tüm laboratuvarlar bağımsız `.docx` dosyaları olarak ayrılmıştır.
   - Orijinal bootcamp föy şablonuna birebir sadık kalınmış, kavram kutuları, tablolar ve soru akışları eksiksiz aktarılmıştır.
   - Soruların tamamı Tio Otomasyon ve ABB IRB 6750S robot hücresinin gerçek parametreleriyle doldurulmuştur.

3. **Üretime Hazır X.509 CA ve PKI Altyapısı:**
   - Root CA (Kök Yetkili), Intermediate CA (Ara Yetkili), Robot Kontrolör Sertifikası ve RobotStudio mTLS İstemci Sertifikası üretilmiştir.
   - `generate_pki_certs.sh` betiği ile tüm zincir doğrulanmış (OpenSSL Verify OK) ve Windows/RobotStudio için PKCS#12 (`.p12`) paketi oluşturulmuştur.

