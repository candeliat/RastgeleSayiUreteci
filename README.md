🔐 LFSR Tabanlı Sözde Rastgele Sayı ve Metin Üreteci (PRNG)
Bu proje, Bilgi Sistemleri Güvenliği dersi kapsamında, Akış Şifreleme (Stream Cipher) algoritmalarının temel yapı taşı olan LFSR (Linear Feedback Shift Register) mantığını simüle etmek amacıyla geliştirilmiştir.

Proje, deterministik bir algoritma kullanarak sayısal değerler üretir ve bu değerleri ASCII karakter setine eşleyerek rastgele parola/metin oluşturur.

📋 Proje Hakkında
Ders: Bilgi Sistemleri Güvenliği

Dil: Python 3

Platform: Google Colab / Jupyter Notebook

Kategori: Kriptografi / Sözde Rastgele Sayı Üreteçleri (PRNG)

🚀 Özellikler
Bu notebook içerisindeki kodlar şunları gerçekleştirir:

Bit Manipülasyonu: Python'un bit operatörlerini (>>, &, |, ^) kullanarak donanım seviyesindeki register kaydırma işlemlerini simüle eder.

Özelleştirilebilir Yapı: Başlangıç tohumu (Seed) ve Tap noktaları (Polinom) kullanıcı tarafından değiştirilebilir.

Sayı Üretimi: Belirlenen bit uzunluğunda (örn. 8-bit) tamsayılar üretir.

Metin/Parola Üretimi: Üretilen sayıları A-Z, a-z, 0-9 ve sembollerden oluşan bir havuza map ederek rastgele string (metin) çıktısı verir.

🛠️ Algoritma Mantığı
Kod, 16-bitlik bir register simülasyonu üzerinde çalışır:

Seed (Tohum): Başlangıç durumu (0 olmamalıdır).

Taps (Musluklar): Geri besleme polinomunu belirleyen bit konumlarıdır (Örn: [0, 2, 3, 5]).

İşleyiş:

Tap noktalarındaki bitler XOR işlemine tabi tutulur.

Register bir adım sağa kaydırılır (Shift).

XOR sonucu, en soldaki (MSB) bite yerleştirilir.

Bu işlem tekrarlanarak yeni sayılar/bitler üretilir.

💻 Kullanım
Sınıfı başlatın ve üretim yapın:

Python
# 1. LFSR Motorunu Başlat (Tohum ve Tap noktaları ile)
my_lfsr = LFSR_RNG(tohum=123456789, tap_noktalari=[0, 2, 3, 5])

# 2. Rastgele Sayı Üret (Örn: 8 bitlik sayı)
sayi = my_lfsr.rastgele_sayi_uret(bit_uzunlugu=8)

# 3. Rastgele Metin/Parola Üret
parola = rastgele_metin_uret(my_lfsr, karakter_sayisi=16)
print(parola)
⚠️ Güvenlik Uyarısı
Bu proje eğitim amaçlıdır. Standart bir LFSR algoritması, kriptografik olarak güvenli değildir. Çıktı dizisi yeterince analiz edilirse (Berlekamp-Massey algoritması vb. ile) başlangıç durumu ve polinom tahmin edilebilir.

Gerçek dünyadaki yüksek güvenlikli sistemlerde (Bankacılık, Askeri İletişim vb.) CSPRNG (Cryptographically Secure Pseudo-Random Number Generator) kullanılması önerilir.
