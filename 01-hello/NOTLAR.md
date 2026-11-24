# 01 · İlk program: hello.c

> Görev 4 · 23–24.11.2026 · Faz 0

## Ne yaptım?

Bir C programı yazdım, `gcc` ile derledim ve terminalde çalıştırdım:

```
hello.c  ──gcc──▶  hello  ──./hello──▶  "omr başladı"
(metin)            (makine kodu)        (çıktı)
```

## Kavramlar

Her kavram iki katmanlı: **A)** mühendis tanımı, **B)** benzetme.

### Kaynak dosya
- **A)** Baytların sırasından oluşan düz bir metin dosyası. `.c` uzantısı içeriği değiştirmez; insana ve gcc'ye "bu C kodu" der.
- **B)** İpe dizilmiş harf boncukları.
- "Merhaba" 7 harf ama dosya **8 bayt**: 8. bayt görünmeyen `\n` (yeni satır, ASCII **10**).

### `#include <stdio.h>`
- **A)** Önişlemci komutu: derlemeden önce `stdio.h` (standard input/output header) dosyasının içeriğini buraya ekler. İçinde `printf`'in tanıtımı var. `< >` = sistemin standart klasöründe ara.
- **B)** Alet çantasını masaya getirmek. Getirmezsen tornavidayı (`printf`) kullanamazsın.

### `int main(void)`
- **A)** `main`, program başlayınca ilk çalışan fonksiyon. `int` = geri döndürdüğü değer tam sayı. `(void)` = dışarıdan bir şey almıyor.
- **B)** Binanın ana kapısı; herkes oradan girer.
- `{ }` = fonksiyonun gövdesi. Açılan her `{` için bir `}` olmalı.

### `printf("...\n");`
- **A)** Çift tırnak içindeki karakter dizisini (**string**) terminale yazar. `\n` imleci alt satıra geçirir.
- **B)** Hoparlöre okunacak not.
- **`;`** = komut bitti. C'de her komut `;` ile biter.

### `return 0;`
- **A)** `main`'i bitirir ve shell'e **çıkış kodu** gönderir. 0 = başarı, 0 dışı = hata. `echo $?` ile görülür.
- **B)** Görevden dönen askerin "tamam" raporu.

### Yorum (comment)
- **A)** Derleyicinin tamamen görmezden geldiği metin: `/* ... */` ya da `// ...`. Programın boyutunu ve davranışını değiştirmez.
- **B)** Kitabın kenarına düşülen kurşun kalem notu.

## Komutlar

| Komut | Ne yapar |
|---|---|
| `nano hello.c` | Dosyayı terminal editöründe aç (yoksa oluştur). Ctrl+O kaydet, Ctrl+X çık. |
| `gcc -Wall -Wextra -Werror -std=c11 hello.c -o hello` | Derle. Uyarıları aç, uyarı varsa derleme, C11 standardını kullan, çıktının adı `hello`. |
| `./hello` | **Bu klasördeki** `hello` programını çalıştır. Shell sadece `/usr/bin` gibi sistem klasörlerinde arar; `./` olmadan bulamaz. |
| `echo $?` | Son programın çıkış kodunu göster. |

## Ölçümler

| Ölçüm | Değer | Yorum |
|---|---|---|
| `hello.c` (yorumlar eklenmeden) | 82 B | `ş` ve `ı` UTF-8'de 2'şer bayt |
| `hello.c` (yorumlar eklendikten sonra) | 277 B | +195 B yorum ve girinti |
| `hello` (derlenmiş, yorumlu ve yorumsuz) | 15.952 B | Kaynağın ~195 katı: başlık bilgileri + `main` öncesi hazırlık kodu. `printf`'in kendisi içinde yok, çalışırken C kütüphanesinden ödünç alınıyor. |
| `echo $?` | 0 | `return 0` shell'e ulaştı |
| İzinler | `hello`: `rwxr-xr-x` · `hello.c`: `rw-r--r--` | `x` (çalıştırma) iznini gcc koydu |

**Yorum kanıtı:** kaynak 82 B'tan 277 B'a büyüdü ama program aynı boyutta kaldı (15.952 B). Derleyici yorumları gerçekten atıyor.

Gömülü bakış: 15.952 B, Arduino Uno'nun program belleğinin (32.768 B) neredeyse yarısı. Bilgisayarda önemsiz, mikrodenetleyicide her bayt sayılır.

## Hatalarım ve kök nedenleri

| Hata | Kök neden | Kural |
|---|---|---|
| `<stido.h>` | Harf sırası karıştı | Adı anlamıyla oku: **std**-**io** |
| `gcc` komutunu nano'nun içine yazdım | Editör ile terminal karıştı | Kod nano'ya, komut prompt'a (`omer@legion:...$`) |
| `return0;` | Anahtar kelime ile değer bitişik | Aralarına boşluk |
| `printf(...)` sonunda `;` yok | Komut sonu işareti unutuldu | Her komut `;` ile biter |
