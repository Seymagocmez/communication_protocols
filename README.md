# 🌐 Bilgisayar Ağları Temelleri: Protokoller, TCP/IP ve OSI Katmanlı Mimarisi

## 1. Protokol Nedir? Neden Protokollere İhtiyaç Vardır? 

Günümüzde milyarlarca cihaz birbiriyle iletişim kuruyor: telefonlar, bilgisayarlar, sunucular, hatta akıllı buzdolapları. Peki, bu kadar farklı veri formatı varken bu cihazlar birbirini nasıl tanıyor ve anlıyor?

İnsanlar arasında iletişim dil aracılığıyla kurulması gibi bilgisayarlar da **protokol** denilen kurallar dizisiyle iletişim kurar. Bir protokol:

“Veri nasıl gönderilir, nasıl alınır, kim iletişimi başlatacak, kim bekleyecek?” gibi kuralları belirler.

### 🔌 Cihazlar Arası İletişim Senaryosu

Farklı firmalar tarafından geliştirilen cihazlar arasında nasıl iletişim kurulabildiğini aşağıdaki senaryoda inceleyelim:

#### Senaryo:

Elimizde iki farklı üreticiye ait cihaz var:

- **Cihaz A**: Firma X tarafından geliştirilen bir sıcaklık sensörü. Verileri `JSON` formatında gönderiyor ve `REST API` kullanıyor.
- **Cihaz B**: Firma Y tarafından geliştirilen bir merkezi kontrol sistemi. Sadece `XML` formatında veri alabiliyor ve `SOAP` protokolüyle çalışıyor.

Bu iki cihazın yazılım dili, veri formatı ve iletişim protokolü farklıdır. Kısacası, bu cihazlar “aynı dijital dili” konuşmadıkları için veri alışverişi yapamazlar. Ta ki bir çevirici sistem devreye girene kadar. 

#### ❓ Peki bu cihazlar nasıl “birbirini anlar”?

Bu gibi durumlarda genellikle bir **ara katman (gateway / geçit yazılımı)** kullanılır. Bu yazılım şunları yapar:

1. Cihaz A’dan `JSON` ve `REST` protokolüyle gelen veriyi alır.
2. Gerekirse JSON formatını `XML`'e dönüştürür.
3. REST çağrısını `SOAP` formatına uygun hale getirir.
4. Dönüştürülmüş veriyi Cihaz B’ye iletir.

Aynı dönüşüm ters yönde de çalışır: B cihazından gelen `XML + SOAP` verisi, A’nın anlayacağı şekilde `JSON + REST` formatına çevrilir.

#### Bu iletişimi mümkün kılan etmenler:

- **Standart veri formatları**: JSON, XML, Protobuf vb.
- **Açık iletişim protokolleri**: REST, SOAP, MQTT, OPC UA vb.
- **API dökümantasyonu** ve veri sözleşmeleri
- **Geçit yazılımları ve adapter katmanlar**


Cihazlar farklı yazılım dillerinde geliştirilebilir, ancak **aynı veri formatı ve iletişim protokolü standartlarına uyarak**, hatta gerekirse ara katman yazılımlar sayesinde, birbirlerini “anlayabilir” hale gelirler.

Bu sayede endüstriyel IoT uygulamalarında farklı marka ve teknolojiye sahip cihazlar tek bir sistem içinde birlikte çalışabilir.

## 2. 🕰 Kısa Tarihçe: Ağlar Nasıl Doğdu?

- **1960’lar:** Bilgisayarlar sadece büyük merkezlerdeydi. İlk ağ deneyleri yapılmaya başlandı.
- **1969:** ARPANET kuruldu. Bu, internetin atası sayılır.
- **1980’ler:** Ağların sayısı arttı. Ancak farklı sistemler birbiriyle **uyumsuzdu**.
- **1983:** TCP/IP protokolü resmi olarak ARPANET’te kullanılmaya başlandı.
- **1984:** ISO, daha genel bir referans modeli olan OSI modelini önerdi.

  > OSI modeli, ağ iletişimini anlamak için oldukça sistemli ve teorik bir yapı sunsa da, pratikte yaygın olarak kullanılmadı çünkü geliştirilmesi yavaş ilerledi ve karmaşık yapısıyla uygulamaya geçmesi zorlaştı. Buna karşılık, TCP/IP modeli daha önce sahaya çıktı, üniversiteler ve askeri kurumlar tarafından hızla benimsendi ve gerçek dünyada işe yarayan çözümler sundu. OSI’nin aksine TCP/IP modeli daha sade, esnek ve geliştiriciler için uygulanabilir olduğundan, internetin büyümesiyle birlikte fiili standart haline geldi. Sonuç olarak OSI modeli eğitim ve kavramsal analiz için değerli kalırken, TCP/IP modeli ağ teknolojilerinin temelini oluşturdu.

## 3.  Neden Katmanlı Model?

- Ağ iletişimi katmanlı bir yapıda tasarlanmıştır çünkü bu yapı, karmaşık iletişim süreçlerini daha anlaşılır, yönetilebilir ve esnek hâle getirir. 
- Her katman belirli bir görevi üstlenir ve sadece bir alt ve bir üst katmanla iletişim kurarak sistemin bütünlüğünü sağlar. Bu modüler yapı, hata ayıklamayı kolaylaştırır, farklı donanım ve yazılımların birbiriyle uyumlu çalışmasını mümkün kılar ve teknolojik gelişmelere açık bir altyapı sunar.
- Böylece ağ sistemleri daha kolay geliştirilebilir, sürdürülebilir ve evrensel standartlara uygun hâle gelir.

## Katmanlı modelin avantajları:
✅ Sorunları izole etme kolaylığı  
✅ Standartlaşma  
✅ Geliştirilebilirlik

## 4.  OSI ve TCP/IP Modellerine Giriş

### OSI Modeli (Open Systems Interconnection)
- ISO tarafından geliştirilmiş 7 katmanlı teorik modeldir.
- Amaç: Ağ sistemlerinin nasıl işlemesi gerektiğini tanımlamak.

### TCP/IP Modeli (Transmission Control Protocol/Internet Protocol)
- Gerçek hayatta kullanılan **uygulamalı model**.
- İnternetin temelini oluşturur.
- 4 katmandan oluşur: Ağ Erişim, İnternet, Taşıma ve  Uygulama Katmanı

## 5. OSI vs TCP/IP: Katmanların Eşleşmesi

![image](https://github.com/user-attachments/assets/2366411b-3d03-478a-802d-5895df5a3b8f)

# TCP/IP Katmanları ve Protokoller
![image](https://github.com/user-attachments/assets/be1c07da-578a-49b0-8a82-551209704d03)
##  Uygulama Katmanı (Application Layer)

### 📧 E-Posta Protokolleri
- **SMTP (Simple Mail Transfer Protocol):** E-posta gönderimi sağlar.
- **IMAP (Internet Message Access Protocol):** E-postaları sunucuda tutarak yönetilmesini sağlar.
- **POP (Post Office Protocol):** E-postaları sunucudan indirir, genelde siler.

### 📁 Dosya Aktarımı
- **FTP (File Transfer Protocol):** Sunucu-istemci arası dosya transferi sağlar.
- **TFTP (Trivial File Transfer Protocol):** Basit, hızlı, kimlik doğrulamasız dosya aktarımı.

### 🌐 Web
- **HTTP (HyperText Transfer Protocol):** Web sayfalarının transferini sağlar.

### 🧭 Ad Sistemi
- **DNS (Domain Name System):** Alan adlarını IP adreslerine çevirir.

### ⏱️ Zaman Senkronizasyonu
- **NTP (Network Time Protocol):** Ağ üzerindeki saatleri senkronize eder.
- **IRIG (Inter-Range Instrumentation Group):** Endüstriyel/askeri zaman senkronizasyon sistemi.

## Taşıma Katmanı (Transport Layer)

### TCP (Transmission Control Protocol)

**TCP**, internetin en temel taşıma protokolüdür ve **güvenilir veri iletimi** sağlar. Verilerin doğru sırayla, eksiksiz ve hatasız bir şekilde hedefe ulaşmasını garanti eder.

####  Özellikleri:
- **Bağlantı tabanlıdır:** Veri aktarımı başlamadan önce bağlantı kurulur (3 yönlü el sıkışma - *three-way handshake*).
- **Sıralama yapar:** Paketleri numaralandırarak doğru sırada iletir.
- **Hata kontrolü sağlar:** Bozuk veya kayıp paketler yeniden gönderilir.
- **Akış kontrolü uygular:** Alıcının alabileceği kadar veri gönderir.
- **Tıkanıklık kontrolü vardır:** Ağın kapasitesine göre veri trafiğini düzenler.

#### TCP Nasıl Çalışır?
1. **Bağlantı Kurulumu**  
   - A → B: `SYN`  
   - B → A: `SYN-ACK`  
   - A → B: `ACK`
2. **Veri Aktarımı**  
   - Paketler numaralandırılır, onaylanır (ACK).
3. **Bağlantı Sonlandırma**  
   - `FIN` ve `ACK` paketleri ile kapatılır.

####  Kullanım Alanları:
- Web: **HTTPS**
- E-posta: **SMTP, IMAP, POP**
- Dosya aktarımı: **FTP**
- Uzaktan erişim: **SSH**

####  Avantajları:
- Güvenilir ve sıralı veri aktarımı sağlar.
- Hataları otomatik düzeltir.

####  Dezavantajları:
- Kontrol mekanizmaları nedeniyle **UDP'den daha yavaştır**.

##  İnternet Katmanı (Internet Layer)

###  IP ve Yardımcı Protokoller
- **IP (Internet Protocol):** Verilerin cihazlar arasında yönlendirilmesini sağlar.
- **NAT (Network Address Translation):** Özel IP’leri genel IP’ye çevirir.
- **ICMP (Internet Control Message Protocol):** Ağ hatalarını bildirir, ping komutunda kullanılır.

### Yönlendirme Protokolleri
- **RIP (Routing Information Protocol):** Basit, mesafe vektör tabanlı yönlendirme.
- **OSPF (Open Shortest Path First):** Bağlantı durumu tabanlı, büyük ağlarda yaygın.
- **EIGRP (Enhanced Interior Gateway Routing Protocol):** Cisco'nun geliştirdiği hibrit protokol.
- **BGP (Border Gateway Protocol):** İnternetin çekirdeğindeki yönlendirme protokolü.


##  Ağ Erişim Katmanı (Network Access Layer)

- **ARP (Address Resolution Protocol):** IP adreslerini MAC adreslerine çevirir.
- **Ethernet:** Kablolu LAN bağlantı standardı.
- **Wi-Fi:** Kablosuz ağ bağlantı standardı (IEEE 802.11).
- **FDDI (Fiber Distributed Data Interface):** Fiber optik yüksek hızlı veri aktarımı.
- **LLC (Logical Link Control):** Veri bağlantı kontrol alt katmanı.
- **PPP (Point-to-Point Protocol):** Seri bağlantılar üzerinden veri aktarımı sağlar.
- **Interface Drivers:** Donanım ve yazılım arasındaki sürücüler.
- **DSL (Digital Subscriber Line):** Telefon hattı üzerinden geniş bant internet.
- **Bluetooth:** Kısa mesafeli kablosuz veri aktarımı standardı.


## 📚 Kaynaklar
- [How the Internet Works - Mozilla Developer Docs](https://developer.mozilla.org/)
- RFC 791, RFC 793, RFC 1122
- ISO/IEC 7498-1 OSI Reference Model
