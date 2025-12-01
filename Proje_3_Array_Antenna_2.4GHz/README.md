# 📡 2x1 Mikroşerit Dizi (Array) Anten Tasarımı ve T-Junction Güç Bölücü

Bu projede, daha önce tasarlanan tekli 2.4 GHz yama anten temel alınarak **2 elemanlı bir Dizi Anten (Array Antenna)** oluşturulmuş ve toplam kazanç (gain) **8.92 dBi** seviyesine çıkarılmıştır.

İki anteni aynı anda ve eş fazlı beslemek, böylece ışıma huzmesini daraltıp yönlendirmek için **Çeyrek Dalga Dönüştürücü (Quarter-Wave Transformer)** tabanlı bir **T-Junction Güç Bölücü** tasarlanmıştır.

## 🎯 Proje Hedefleri
* **Amaç:** Tekli antenin kazancını (6.3 dBi) dizi yapı kullanarak artırmak.
* **Hedef Frekans:** 2.4 GHz (ISM Bandı)
* **Besleme Ağı:** Empedans uyumsuzluğunu gidermek için T-Junction tasarımı.

## 📐 Tasarım Teorisi: T-Junction Güç Bölücü

İki adet $50\Omega$ anten paralel bağlandığında, birleşim (T) noktasındaki eşdeğer empedans yarıya düşer:
$$Z_{paralel} = \frac{50 \cdot 50}{50 + 50} = 25 \Omega$$

Bu $25\Omega$ noktayı, $50\Omega$ ana besleme hattına (Main Feed) uydurmak için araya **Çeyrek Dalga Dönüştürücü ($\lambda/4$ Transformer)** eklenmiştir. Dönüştürücünün karakteristik empedansı şu formülle hesaplanmıştır:

$$
Z_{trans} = \sqrt{Z_{giriş} \cdot Z_{çıkış}} = \sqrt{25 \cdot 50} \approx 35.35 \Omega
$$

CST Studio Suite hesaplamalarına göre bu empedans için gereken hat boyutları:
* **Dönüştürücü Genişliği ($W_{trans}$):** 5.8 mm
* **Dönüştürücü Uzunluğu ($L_{trans}$):** 16.5 mm ($\lambda/4$ @ 2.4 GHz)

---

## 🛠️ Simülasyon Sonuçları

### 1. 3D Işıma Deseni ve Anten Yapısı
Dizi yapı sayesinde ışıma huzmesi daraltılmış ve enerji daha güçlü bir şekilde yönlendirilmiştir. Aşağıdaki görselde, tasarlanan T-Junction beslemeli 2x1 anten yapısı ve üzerinde oluşan 3D ışıma deseni (transparent olarak) birlikte gösterilmiştir.

* **Yönlülük (Directivity):** **8.92 dBi**
* **Kazanç Artışı:** Tekli antene göre yaklaşık **+2.6 dB** artış sağlanmıştır.

![3D Farfield ve Yapı](3D_Pattern_Overlay.png)
*(Şekil 1: 2x1 Dizi Anten Yapısı üzerinde 8.92 dBi 3D Işıma Deseni)*

### 2. S-Parametre Sonuçları (S11)
Antenin rezonans frekansındaki performansını gösteren S11 (Geri Dönüş Kaybı) grafiği aşağıdadır. Tasarlanan T-Junction besleme ağı sayesinde, hedef frekans olan 2.4 GHz'de mükemmel bir empedans uyumu sağlanmış ve Geri Dönüş Kaybı endüstri standardı olan -10 dB'nin oldukça altına inmiştir.

![S11 Grafiği](S11_Graph.png)
*(Şekil 2: 2.4 GHz'de S11 (Geri Dönüş Kaybı) Grafiği)*

---

## 📂 Dosya Bilgisi
* `Proje_3_Array_Anten_2.4GHz.cst`: CST Studio Suite proje dosyası.
* **Substrate (Zemin):** FR-4 (Lossy), $\epsilon_r=4.3$, Kalınlık ($h$)=1.6 mm.

---
*Yazar: Utku Turan*
