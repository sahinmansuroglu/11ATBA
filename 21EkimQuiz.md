
> Aşağıda verilenlere göre  bir sınıf tasarlayınız.Ve bu sınıftan klavyeden girilen verilere göre for döngüsü yardımıyla 3 nesne oluşturup bilgilerini ekrana yazdırınız.

1. adSoyad, puan1, puan2 alanları bulunacak ve aşağıdaki şartlarda kapsüllenecek
    1. adSoyad boş gelirse "Ad Soyad girilmedi" atanacak"
    2. puan1, puan2 0 ile 100 arasında girilmezse 0 değeri atanacak
2.  ortalamaPuan ve kaldıGectiDurumu adında sadece okunabilir  property olacak.
3.  bilgileriEkranaYaz metodları bulunacak.

> **Kurucu metot kullanılmalı**
> **Kapsülleme yapılmalı**


**Çözümü**

```csharp
using System;
public class Ogrenci
{
    private string adSoyad;
    private short puan1;
    private short puan2;

    public string AdSoyad
    {
        get
        {
            return adSoyad;
        }

        set
        {
            if (value == "")
            {
                adSoyad = "Ad Soyad Girilmedi";
            }
            else
            {
                adSoyad = value;
            }

        }
    }


    public short Puan1
    {
        get
        {
            return puan1;
        }
        set
        {
            if (value >= 0 && value <= 100)
            {
                puan1 = value;
            }
            else
            {
                puan1 = 0;
            }

        }
    }
    public short Puan2
    {
        get
        {
            return puan2;
        }
        set
        {
            if (value >= 0 && value <= 100)
            {
                puan2 = value;
            }
            else
            {
                puan2 = 0;
            }

        }
    }

    public double Ortalama
    {
        get
        {
            return (Puan1 + Puan2) / 2.0;
        }
    }

    public string kaldıGectiDurumu
    {
        get
        {
           
            if (Ortalama < 50)
            {
                return "Kaldınız..";
            }
            else
            {
                return "Geçtiniz....";
            }

            //yada aşağıdaki gibi ternary operatörü kullanılabilir.
            // return Ortalama < 50 ? "Kaldınız..." : "Geçtiniz...";
        }
    }

    public Ogrenci(string adSoyad,  short puan1, short puan2)
    {
        this.AdSoyad = adSoyad;
        this.Puan1 = puan1;
        this.Puan2 = puan2;
      
    }
    public void bilgileriEkranaYaz()
    {
        Console.WriteLine("---------Öğrenci Bilgileri----------");
        Console.WriteLine($" Ad Soyad:{adSoyad}");
        Console.WriteLine($" Puan1: {puan1}");
        Console.WriteLine($" Puan2: {puan2}");
        Console.WriteLine($" Ortalama:{Ortalama}");
        Console.WriteLine($" Durumu:{kaldıGectiDurumu}");

    }
}

    class AnaProgram
{
    public static void Main(string [] args)
    {
        Ogrenci ogr1 = new Ogrenci("Şahin MANSUROĞLU",  95, 100);
        ogr1.bilgileriEkranaYaz();
        Ogrenci ogr2 = new Ogrenci("Ali AR", 61, 50);
        ogr2.bilgileriEkranaYaz();
        Ogrenci ogr3 = new Ogrenci("Mehmet UÇTU",  95, 60);
        ogr3.bilgileriEkranaYaz();
        Console.ReadKey();
    }
}
```

**Program Çıktısı**

![image](https://user-images.githubusercontent.com/28144917/137868976-095860a9-a23e-4e2b-98f3-4a0370b805a3.png)
