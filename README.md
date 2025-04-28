# ping-pong

### 1. CM7 (Master çekirdek) → her 10 saniyede bir sırasıyla 0'dan 20'ye kadar sayı gönderiyor ve "X PING" mesajı terminale yazıyor.

### 2. CM4 (Remote çekirdek) → gelen sayıya karşılık sayının ismini (örneğin "two") ve sonuna "PONG" ekleyerek cevap veriyor ve kendi terminaline yazıyor. 

CM7 veri gönderiyor → CM4 alıyor ve cevaplıyor.

CM7 cevabı bekliyor → cevabı alınca bir sonrakine geçiyor.

İkisi birbiriyle senkronize çalışıyor (sırayla gidiyor, üst üste binmiyor).

---

# 📜 Yaptıklarımızın Özeti:

### 1. **CM7 (COM5)**:
- 0'dan 20'ye kadar olan **sayıları (uint32_t)** OpenAMP ile **CM4'e gönderdi**.
- Her gönderdiği sayıyı **kendi terminalinde (COM5)** **"0", "1", "2", "3", ...** şeklinde yazdırdı.
  
  ➔ Burada `sprintf` ile sayıları yazıya çevirip `UART`'a bastık.

---

### 2. **CM4 (COM6)**:
- CM7'den gelen **sayısal veriyi aldı**.
- Gelen sayının değeri kaçsa, onu İngilizce **("zero", "one", "two", "three"...)** şeklinde kendi terminaline yazdırdı.
  
  ➔ Burada gelen sayıyı `number_strings[]` isimli bir diziden eşleştirerek yazdık.

---

# 📈 Terminalde Görüntü:
| CM7 (COM5)            | CM4 (COM6)           |
|:----------------------|:---------------------|
| 0                     | zero                 |
| 1                     | one                  |
| 2                     | two                  |
| ...                   | ...                  |
| 20                    | twenty               |

---

# 📌 Sonuç:
✅ CM7 ➔ Sayıyı gönderiyor, terminale sayının kendisini yazıyor.  
✅ CM4 ➔ Sayıyı alıyor, terminale yazıyla yazıyor.

---

İstersen sana **daha profesyonel bir sürüm** de hazırlayabilirim:  
➔ Mesela otomatik tekrar eden döngü, "başla/dur" komutu eklemek vs.  
İster misin? 🎯 (evet profesyonel sürüm yapalım dersen hemen başlıyoruz)  
Bekliyorum! 🚀
