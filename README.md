# 🌐 Bilgisayar Ağları, Protokoller ve Katmanlı Mimariler: Temelden TCP/IP ve OSI'ye

## 1.Protokol Nedir? Neden Protokollere İhtiyaç Vardır? 

Günümüzde milyarlarca cihaz birbiriyle iletişim kuruyor: telefonlar, bilgisayarlar, sunucular, akıllı buzdolapları bile! Peki, bu cihazlar birbirini nasıl tanıyor ve anlıyor?

İnsanlar arasında iletişim dil aracılığıyla kurulur. Benzer şekilde, bilgisayarlar da **protokol** denilen kurallar dizisiyle iletişim kurar. Bir protokol:

> “Veri nasıl gönderilir, nasıl alınır, kim konuşacak, kim bekleyecek?” gibi kuralları belirler.

---

## 2. 🕰 Kısa Tarihçe: Ağlar Nasıl Doğdu?

- **1960’lar:** Bilgisayarlar sadece büyük merkezlerdeydi. İlk ağ deneyleri yapılmaya başlandı.
- **1969:** ARPANET kuruldu. Bu, internetin atası sayılır.
- **1980’ler:** Ağların sayısı arttı. Ancak farklı sistemler birbiriyle **uyumsuzdu**.
- **1983:** TCP/IP protokolü resmi olarak ARPANET’te kullanılmaya başlandı.
- **1984:** ISO, daha genel bir referans modeli olan OSI modelini önerdi.

  > Neden TCP/IP Modeli OSI modeli, ağ iletişimini anlamak için oldukça sistemli ve teorik bir yapı sunsa da, pratikte yaygın olarak kullanılmadı çünkü geliştirilmesi yavaş ilerledi ve karmaşık yapısıyla uygulamaya geçmesi zorlaştı. Buna karşılık, TCP/IP modeli daha önce sahaya çıktı, üniversiteler ve askeri kurumlar tarafından hızla benimsendi ve gerçek dünyada işe yarayan çözümler sundu. OSI’nin aksine TCP/IP modeli daha sade, esnek ve geliştiriciler için uygulanabilir olduğundan, internetin büyümesiyle birlikte fiili standart haline geldi. Sonuç olarak OSI modeli eğitim ve kavramsal analiz için değerli kalırken, TCP/IP modeli ağ teknolojilerinin temelini oluşturdu.


---

## 3. 🧱 Neden Katmanlı Model?

Ağ iletişimi **karmaşık** bir süreçtir. Bu süreci anlamak ve yönetmek kolay olsun diye, bilim insanları bunu **katmanlara ayırdı**.

Her katman:
- Belirli bir görevi yerine getirir,
- Alt katmandan gelen veriyi alır, işler ve üst katmana iletir.

Katmanlı modelin avantajları:
✅ Sorunları izole etme kolaylığı  
✅ Standartlaşma  
✅ Geliştirilebilirlik

---

## 4. 🌐 OSI ve TCP/IP Modellerine Giriş

### 📊 OSI Modeli (Open Systems Interconnection)
- ISO tarafından geliştirilmiş 7 katmanlı teorik modeldir.
- Amaç: Ağ sistemlerinin nasıl işlemesi gerektiğini tanımlamak.

### 📡 TCP/IP Modeli
- Gerçek hayatta kullanılan **uygulamalı model**.
- İnternetin temelini oluşturur.
- 4 katmandan oluşur.

---

## 5. 🔗 OSI vs TCP/IP: Katmanların Eşleşmesi

| OSI Modeli                  | TCP/IP Modeli              | Görev Açıklaması |
|-----------------------------|----------------------------|------------------|
| 7. Uygulama (Application)   | 4. Uygulama                | Kullanıcıya hizmet |
| 6. Sunum (Presentation)     | 4. Uygulama                | Veriyi biçimlendirir |
| 5. Oturum (Session)         | 4. Uygulama                | Oturum yönetimi |
| 4. Taşıma (Transport)       | 3. Taşıma                  | Uçtan uca bağlantı |
| 3. Ağ (Network)             | 2. İnternet                | IP adresleme, yönlendirme |
| 2. Veri Bağlantı (Data Link)| 1. Ağ Erişim               | Fiziksel adresleme |
| 1. Fiziksel (Physical)      | 1. Ağ Erişim               | Bitlerin iletimi |

---

## 6. 📦 Katmanlara Göre Protokoller

### ✅ Uygulama Katmanı (OSI 7 / TCP-IP 4)
**Amaç**: Kullanıcıya hizmet sağlar  
**Protokoller**:  
- HTTP, HTTPS (web)
- FTP (dosya aktarımı)
- SMTP, POP3, IMAP (e-posta)
- DNS (isim çözümleme)

---

### ✅ Taşıma Katmanı (OSI 4 / TCP-IP 3)
**Amaç**: Kaynaktan hedefe güvenilir veri iletimi  
**Protokoller**:  
- **TCP**: Güvenilir, sıralı aktarım  
- **UDP**: Hızlı, güvensiz, sırasız aktarım (ör: canlı yayın)

---

### ✅ Ağ Katmanı (OSI 3 / TCP-IP 2)
**Amaç**: IP adresleme, yönlendirme  
**Protokoller**:  
- IP (IPv4, IPv6)
- ICMP (hata bildirimi, ping)
- ARP (adres çözümleme)

---

### ✅ Veri Bağlantı + Fiziksel Katman (OSI 2-1 / TCP-IP 1)
**Amaç**: Fiziksel bağlantı, veri çerçeveleri  
**Protokoller/Teknolojiler**:  
- Ethernet
- MAC Adresi
- Wi-Fi
- Fiziksel kablolar, fiber optik

---

## 7. 🎯 Örnek: Web Sitesi Nasıl Yüklenir?

1. **Uygulama katmanı**: Tarayıcı `www.ornek.com` adresini ister (HTTP)
2. **Taşıma katmanı**: TCP bağlantısı kurulur
3. **Ağ katmanı**: IP adresi bulunur, paket yönlendirilir
4. **Veri bağlantı/fiziksel katman**: Veri fiziksel olarak aktarılır

---

## 8. 📌 Sonuç

Ağ iletişimi görünmeyen ama hayatımızın temel taşı olan bir teknolojidir. Bu teknolojinin düzgün işlemesi için:
- Standartlara (protokollere),
- Katmanlı yapılara,
- Ve bu yapıların birlikte çalışmasına ihtiyaç vardır.

TCP/IP bugün internetin temelidir. OSI ise bu yapıyı daha iyi anlamak için bir rehber sunar.

---

## 📚 Kaynaklar
- [How the Internet Works - Mozilla Developer Docs](https://developer.mozilla.org/)
- RFC 791, RFC 793, RFC 1122
- ISO/IEC 7498-1 OSI Reference Model
