# MimLine

MimLine, "0"'ın dizinin başında ve sonunda olduğu merkezde "1"in olduğu iki kutuplu ve çok boyutluluğa müsaid bir sayı dizini örneğidir. Bu dizinde "1" merkezde olarak pozitif eki "2" olup, nekatif komşusu "-2"'dir. "-1" dizinde yer almayıp sanrısal olarak dikey alt alanında konumlandırılmıştır: ama unutmayın sanrısal olarak.

Negatif alan sayı nesnesinin içeriğini içlemini temsil etmekteyken, pozitif alan kapsamını kapsayıcılarını temsil eder. Kapsam ve içlem'de her bir öteki bir katmanı ifade eder; ve her katmanın boyutu kendi içindedir.

Örnek vermek gerekirse:
Bir elma = "1"
Elmanın birinci dereceden içlemi -bu her zaman nesnenin tüm içeriklerinin toplamını temsil eder- = -2
Elmanın ikinci dereceden içlemi -örneğin fizik ilmi cihetinden içlemi- -3

Boyu örneği için: -3 üzerinden örneklemek gerekirse: -gene elme üzerinden-
[-3[0,1]] = Burada fiziksel olarak iki parçadan incelendiğini görüyoruz: bu iki sayı için de şu örneklemeyi yapabiliriz:
0 = kütlesi
1 = hızı

pozitif durumunu da izahata geleceğiz.

## Özellikler

- `name`: Örneğin adını temsil eder.
- `centerArray`: Merkez dizisi olarak adlandırılan bir dizi tutar.
- `dimensional_centerArray`: Boyutlu merkez dizisini tutar.

## Kurulum

Herhangi bir ek kurulum gerektirmez. Kodu doğrudan kullanabilirsiniz.

## Kullanım

Aşağıdaki örnek, MimLine sınıfının nasıl kullanılacağını göstermektedir:

# Örnek kullanım
```python
line = MimLine("Example", inEnd=2, outEnd=1, inDimension=3, outDimension=2)
line.display()
```
# Testler
MimLine sınıfının doğru çalışıp çalışmadığını kontrol etmek için testler oluşturulmuştur. Aşağıdaki kod örneği, 5000 adet testi gerçekleştirecek olan MimLineTest sınıfını içermektedir:

```python
import random

class MimLineTest:
    def __init__(self):
        self.tests = 5000

    def run_tests(self):
        for i in range(self.tests):
            print(f"--- Test {i+1} ---")
            inEnd = random.randint(1, 10)
            outEnd = random.randint(1, 10)
            inDimension = random.randint(1, 10)
            outDimension = random.randint(1, 10)
            line = MimLine(f"Example{i+1}", inEnd, outEnd, inDimension, outDimension)
            self.test_mimline(line)
            print()

    def test_mimline(self, line):
        # Başında ve sonunda sıfır olup olmadığını kontrol etme
        if line.centerArray[0] == 0 and line.centerArray[-1] == 0:
            print("Başında ve sonunda sıfır var.")
        else:
            raise ValueError("Başında veya sonunda sıfır yok.")

        # Liste içinde 1 değerinin olup olmadığını kontrol etme
        if 1 in line.dimensional_centerArray:
            print("Listede 1 değeri mevcut.")
        else:
            raise ValueError("Listede 1 değeri yok veya değiştirilmiş.")
```
# MimLineTest sınıfı kullanarak testleri çalıştırma
```python
test = MimLineTest()
test.run_tests()
```

Testlerin sonucunda oluşan hatalar, ValueError türünde bir hata fırlatarak gösterilmektedir. Başarı durumunda herhangi bir çıktı üretilmeyecektir.
