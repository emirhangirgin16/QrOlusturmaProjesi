Dijital QR Kod Oluşturucu
Bu projede, kullanıcıların kolayca QR kodları oluşturmasına ve kaydetmesine olanak tanıyan basit bir Python uygulaması geliştirdik. Uygulama, kullanıcının girdiği URL'ye dayalı olarak bir QR kodu oluşturur ve SVG formatında bir dosya olarak kaydeder.

Gereklilikler
Bu uygulamayı çalıştırmak için aşağıdaki kütüphanelere ihtiyacınız var:

tkinter: Python'un standart GUI kütüphanesi

pyqrcode: QR kodları oluşturmak için kullanılan kütüphane

tkinter.filedialog: Dosya yolunu kullanmak ve kaydetmek için gerekli
**************************************************************************
Kurulum
Gerekli kütüphaneleri yüklemek için aşağıdaki komutu çalıştırın:
pip install pyqrcode pypng
**************************************************************************
Kullanım
Uygulamayı çalıştırın.

QR kodunu oluşturmak istediğiniz URL'yi girin.

"QR KOD OLUŞTUR" butonuna tıklayın.

Dosya adını ve kaydetmek istediğiniz konumu seçin.

QR kodunuz belirtilen konuma SVG formatında kaydedilecektir.
***************************************************************************
Gerekli Kütüphaneler:
import tkinter as tk
from tkinter import filedialog
import pyqrcode
from pyqrcode import QRCode
***************************************************************************
Fonksiyon Oluşturma:
def qr_kod_olusturucu():
    url = url_girdi.get()
    if url:
        qr_url = pyqrcode.create(url)
        dosya_yolu = filedialog.asksaveasfilename(defaultextension=".svg", filetypes=[("SVG DOSYASI","*.svg")])
        if dosya_yolu:
            qr_url.svg(dosya_yolu, scale=8)
            durum_etiketi.config(text="QR kod oluşturuldu ve kaydedildi.")
****************************************************************************
Tasarım:
uygulama_penceresi = tk.Tk()
uygulama_penceresi.title("Dijital QR Kod Oluşturucu")

etiket = tk.Label(uygulama_penceresi, text="Lütfen QR kod oluşturmak istediğiniz bağlantıyı yazınız:")
url_girdi = tk.Entry(uygulama_penceresi, width=40)
qr_kod_olustur_butonu = tk.Button(uygulama_penceresi, text="QR KOD OLUŞTUR", command=qr_kod_olusturucu)
durum_etiketi = tk.Label(uygulama_penceresi, text="")
*****************************************************************************
Grid Düzeni:
etiket.grid(row=0, column=0, padx=10, pady=10)
url_girdi.grid(row=0, column=1, padx=10, pady=10)
qr_kod_olustur_butonu.grid(row=1, column=0, columnspan=2, padx=10, pady=10)
durum_etiketi.grid(row=2, column=0, columnspan=2, padx=10, pady=10)
*****************************************************************************
Uygulamayı Başlatma:
uygulama_penceresi.mainloop()
