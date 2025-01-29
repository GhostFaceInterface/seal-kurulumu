# SEAL Kurulumu ve Örnek Çalıştırma

Bu doküman, Microsoft SEAL (Simple Encrypted Arithmetic Library) kütüphanesinin **v3.2.0** sürümünün nasıl kurulacağını ve örneklerin nasıl çalıştırılacağını açıklamaktadır.

## Neden SEAL v3.2.0?

Ders kapsamında verilen örnekler **SEAL v3.2.0** sürümüne dayanmaktadır. Dolayısıyla, doğru sürümü kullanarak SEAL'i indirip derlememiz gerekmektedir. Aksi takdirde, verilen örnekler uyumsuzluk nedeniyle çalışmayabilir.

## Kurulum Adımları

### 1. SEAL v3.2.0 Kütüphanesini Klonlama

Öncelikle, SEAL'in doğru sürümünü **git** kullanarak klonluyoruz:
```bash
git clone --branch v3.2.0 https://github.com/microsoft/SEAL.git
```
Bu komut, SEAL deposunun **v3.2.0** sürümünü bilgisayarımıza indirir.

### 2. SEAL Kaynak Dizini İçine Giriş

```bash
cd SEAL
cd native/src
```
Bu komutlar, SEAL klasörüne ve kaynak dosyalarının bulunduğu `native/src` dizinine giriş yapmamızı sağlar.

### 3. Ana Projeyi Derleme

Derleme sürecini başlatmak için aşağıdaki komutları sırasıyla çalıştırıyoruz:

```bash
cmake -S . -B build
cmake --build build
```

Bu komutlar:
- **`cmake -S . -B build`**: SEAL kaynak dosyalarından **build** klasörü oluşturarak derleme yapılandırmasını hazırlar.
- **`cmake --build build`**: SEAL kütüphanesini oluşturur.

### 4. Kütüphaneyi Sisteme Yükleme

Oluşturulan SEAL kütüphanesini sistemimize yüklemek için şu komutu çalıştırıyoruz:

```bash
sudo cmake --install build
```
Bu komut, SEAL kütüphanelerini `/usr/local/lib/cmake/SEAL-3.2` dizinine yükler.

### 5. Örnek Kodları Derleme

Örnekleri derlemek için **examples** klasörüne gidiyoruz:

```bash
cd ..
cd examples
```
Daha sonra aşağıdaki komutları çalıştırarak örneklerin derlenmesini sağlıyoruz:

```bash
cmake -S . -B build -DSEAL_DIR=/usr/local/lib/cmake/SEAL-3.2
cmake --build build
```

Burada:
- **`cmake -S . -B build -DSEAL_DIR=/usr/local/lib/cmake/SEAL-3.2`**: Derleme sürecine, SEAL kütüphanesinin sistemde nerede bulunduğunu bildiriyoruz.
- **`cmake --build build`**: Örnek kodları derleyerek çalıştırılabilir dosyalar oluşturur.

### 6. Derlenen Örnekleri Çalıştırma

Derlenen örnekler `bin/` klasörü içinde yer alır. Çalıştırmak için:

```bash
../bin/sealexamples
```
Bu komut, SEAL örneklerini çalıştırarak detaylı çözümlerini görmemizi sağlar.

---

Bu adımları tamamladıktan sonra, SEAL kütüphanesi başarıyla kurulmuş ve örnek kodlar çalıştırılmaya hazır hale gelmiş olacaktır. Eğer herhangi bir hata ile karşılaşırsanız, hata mesajını dikkatlice inceleyerek eksik bağımlılıkları kontrol edebilirsiniz.

