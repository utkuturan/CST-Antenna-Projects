# RF ve Elektronik Mühendisliği Portfolyosu

Bu depo, CST Studio Suite, Altium Designer ve diğer RF araçları kullanılarak yapılan anten ve PCB tasarım projelerimi içermektedir.

---

## Proje 1: 1 GHz Dipol Anten Tasarımı ve Optimizasyonu (CST)

**Tarih:** 23 Ekim 2025

**Proje Özeti:** Bu projede, 1 GHz hedef frekansı için temel bir yarım dalga dipol anten CST Studio Suite kullanılarak modellendi, simüle edildi ve optimize edildi.

### Adım 1: İlk Tasarım ve Analiz (Teorik)
Anten, $\lambda/4$ teorik hesabına göre 75 mm'lik kol boyu ile modellendi. Simülasyon, "kalın iletken etkisinden" (fat-dipole effect) dolayı antenin hedeflenen 1 GHz'de değil, **0.91 GHz**'de rezonansa girdiğini doğru bir şekilde gösterdi.

*(Not: Bu ilk sonuç, optimizasyonun gerekliliğini göstermek için referans olarak belirtilmiştir.)*

### Adım 2: Optimizasyon (Parametrik Tarama)
Anteni tam olarak 1.0 GHz'e ayarlamak için CST'nin "Parametric Sweep" (Parametrik Tarama) özelliği kullanıldı.
1.  **Kaba Tarama (Coarse Sweep):** 70-75 mm arası taranarak hedefin 70 mm'ye yakın olduğu bulundu.
2.  **İnce Ayar Taraması (Fine Sweep):** 65-70 mm arası daha hassas taranarak optimal kol boyunun **68 mm** olduğu tespit edildi.

### Adım 3: Nihai Tasarım ve Doğrulama
`kol_boyu = 68 mm` olarak ayarlanan nihai model, hedeflenen frekansı tam olarak vurduğunu doğrulamak için yeniden simüle edildi.

#### Nihai S-Parametre (S11)
Nihai tasarımın rezonans çukuru (dip), tam olarak **1.0 GHz**'e mükemmel bir şekilde oturmuştur.

![Nihai S11 Grafiği](S11_final_1GHz.png)

#### Nihai Işıma Diyagramı (Farfield)
Nihai 68 mm'lik tasarım, teorik olarak beklenen 2.15 dBi'a çok yakın bir yönlülükle (directivity) klasik "simit" (doughnut) ışıma diyagramını korumuştur.

![Nihai 3D Işıma Diyagramı](Farfield_final_1GHz_3D.png)

### Çıkarım
Bu proje, temel anten teorisinin simülasyonla doğrulandığı ve bir tasarımın "Teori -> Analiz -> Optimizasyon -> Nihai Tasarım" iş akışı kullanılarak nasıl hedefe kilitlendiğini göstermektedir.
