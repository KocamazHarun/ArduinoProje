Arduino ile Bluetooth aracılığıyla bir servo motoru kontrol etme.
Kütüphaneler: #include <Servo.h>(servo motor için), #include <SoftwareSerial.h>(Bluetooth modülü seri haberleşme)
Değişkenler: SoftwareSerial bt(8, 7);: Bluetooth için RX (alıcı) pini olarak 8, TX (verici) pini olarak 7,
Servo servo;: Bir servo motor nesnesi
int data = 0;: Gelen veriyi depolama
int value;: Servo motorun pozisyonunu belirleme
setup() Fonksiyonu:
bt.begin(9600);: Bluetooth modülü ile haberleşmenin hızını (baud rate) 9600 olarak ayarlıyortuz.
servo.attach(9);: Servo motoru Arduino'nun 9 numaralı dijital pinine bağlıyoruz.
loop() Fonksiyonu:
if (bt.available() > 0): Bluetooth modülünden gelen veri olup olmadığını kontrol eder.
data = bt.parseInt();: Bluetooth üzerinden gönderilen verileri tam sayı olarak alır ve data değişkenine kaydeder.
if (data > 0): Eğer gelen veri sıfırdan büyükse bu bloğa girer.
value = data;: Gelen veriyi value değişkenine aktarır.
servo.write(value);: Servo motorun pozisyonunu value değişkenine göre ayarlar. Servo motor, 0 ile 180 derece arasında dönebilir.
delay(20);: 20 milisaniyelik bir bekleme süresi koyar.
Çalışma Mantığı:
Bluetooth modülü üzerinden bir cihaz (telefon vb.) veri gönderdiğinde, bu veri data değişkenine atanır.
Eğer gelen veri sıfırdan büyükse, servo motorun pozisyonu bu değere göre ayarlanır. Örneğin, gelen veri 90 ise, servo motor 90 derece döner.
