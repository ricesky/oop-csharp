### Lecture Notes #3

**Kelas dan Objek**

1. **Objek**
   Objek adalah entitas yang memiliki atribut (seperti warna, kecepatan, bentuk), state (seperti nilai dari warna, berapa kecepatan saat ini, bentuk saat ini), dan perilaku (seperti akselerasi dan deselerasi). Dalam C#, objek diciptakan dari template kelas, yang mendefinisikan atribut dan perilaku objek tersebut.

2. **Kelas**
   Kelas adalah blueprint atau template yang mendefinisikan atribut dan perilaku untuk objek. Seperti mobil dalam sebuah garasi, kelas mendefinisikan atribut umum (roda, pintu, jendela) dan perilaku (berpindah tempat, akselerasi, berhenti).

3. **Deklarasi Kelas di C#**
   Dalam C#, atribut direpresentasikan oleh properties dan perilaku oleh methods. Berikut contoh deklarasi kelas sederhana:

```csharp
public class Car
{
    // Attributes (properties)
    public string Color { get; set; }
    public string LicenseNumber { get; set; }
    public Wheel[] Wheels { get; set; }
    public string Brand { get; set; }

    // Methods (functions)
    public void Accelerate(int speed)
    {
        // Implementation for accelerate method
    }

    public void Brake()
    {
        // Implementation for brake method
    }

    public void Show()
    {
        // Implementation for show method
    }
}

public class Wheel
{
    // Properties of Wheel
    // Assume some properties here
}
```

4. **Instansiasi Objek di C#**
   Instansiasi adalah proses pembuatan objek dari sebuah kelas. Dalam C#, ini dilakukan menggunakan konstruktor. Sebuah kelas dapat memiliki konstruktor dengan atau tanpa parameter. Berikut adalah contoh instansiasi objek:

```csharp
public class Car
{
    // Attributes
    public string Color { get; set; }
    public string Brand { get; set; }

    // Default constructor
    public Car()
    {
    }

    // Parameterized constructor
    public Car(string color, string brand)
    {
        Color = color;
        Brand = brand;
    }

    // Methods
    public void Accelerate(int speed)
    {
        // Method implementation
    }

    public void Brake()
    {
        // Method implementation
    }

    public void Show()
    {
        // Method implementation
    }
}

// Example of object instantiation
Car mobilToyota = new Car("Hitam", "Toyota");
Car mobil = new Car();
```

Dalam contoh ini, `new Car("Hitam", "Toyota")` memanggil konstruktor dengan dua parameter dan `new Car()` memanggil konstruktor tanpa parameter. Objek yang dihasilkan memiliki state yang diinisialisasi melalui konstruktor ini.
