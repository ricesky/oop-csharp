### Catatan Kuliah: Inheritance

#### 1. Apa itu Inheritance?
Inheritance atau pewarisan adalah konsep di mana sebuah kelas (yang disebut sebagai *derived class* atau *subclass*) mewarisi atribut dan metode dari kelas lain (yang disebut sebagai *base class* atau *superclass*). Inheritance memungkinkan pembentukan hubungan hirarki antar kelas dan digunakan untuk mempromosikan pemakaian ulang kode dan polimorfisme.

#### 2. Konsep dasar Inheritance
- **Base/Super/Parent Class**: Kelas yang memberikan atribut dan metode kepada kelas lain.
- **Derived/Sub/Child Class**: Kelas yang menerima atribut dan metode dari *base class*. Kelas ini dapat menambah atau memodifikasi atribut dan metode yang diwarisi.

#### 3. Kegunaan Inheritance
Inheritance digunakan untuk:
- Menyederhanakan pemeliharaan dan modifikasi kode dengan mengurangi duplikasi.
- Memperluas atau menyesuaikan fungsionalitas kelas yang sudah ada tanpa mengubahnya.
- Mendefinisikan hubungan antar objek yang memiliki karakteristik atau perilaku serupa.

Inheritance cocok digunakan ketika ada hubungan "is-a" antara objek, seperti "Sebuah Orc adalah Monster."

#### 4. Konsep Is-a Relationship
Dalam konsep OOP, hubungan "is-a" merepresentasikan hubungan pewarisan antara kelas. Jika kita mengatakan "Sebuah Orc adalah Monster," maka Orc mewarisi sifat-sifat dasar dari Monster.

#### 5. Sintaks Inheritance di C#

Dalam C#, inheritance atau pewarisan didefinisikan menggunakan tanda colon (`:`) setelah nama kelas yang diturunkan (derived class) diikuti dengan nama kelas induk (base class). Berikut ini adalah contoh syntax dasar untuk inheritance di C#:

```csharp
// Ini adalah base class
public class BaseClass
{
    public int baseValue;

    public BaseClass() // Constructor dari base class
    {
        baseValue = 5;
    }

    public void BaseMethod()
    {
        Console.WriteLine("Metode dari base class.");
    }
}

// Ini adalah derived class yang mewarisi BaseClass
public class DerivedClass : BaseClass
{
    public int derivedValue;

    public DerivedClass() // Constructor dari derived class
    {
        derivedValue = 10;
    }

    public void DerivedMethod()
    {
        Console.WriteLine("Metode dari derived class.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Membuat instans dari derived class.
        DerivedClass derivedObj = new DerivedClass();

        // Memanggil metode yang diwarisi dari base class.
        derivedObj.BaseMethod(); // Output: "Metode dari base class."

        // Mengakses property yang diwarisi dari base class.
        Console.WriteLine(derivedObj.baseValue); // Output: 5

        // Memanggil metode dari derived class itu sendiri.
        derivedObj.DerivedMethod(); // Output: "Metode dari derived class."
    }
}
```

Pada contoh di atas, `DerivedClass` mewarisi `BaseClass`. Itu berarti `DerivedClass` menerima semua metode dan variabel non-private dari `BaseClass`. Ketika kita membuat instans dari `DerivedClass`, kita dapat menggunakan metode dan properti yang didefinisikan dalam `BaseClass` serta yang ada pada `DerivedClass` itu sendiri.

Perlu diperhatikan bahwa constructors tidak diwariskan, tetapi sebuah derived class dapat memanggil constructor dari base class menggunakan keyword `base`. Juga, semua members dengan access modifier `private` di base class tidak dapat diakses langsung oleh derived class, sehingga hanya `public` dan `protected` members yang dapat diwarisi dan diakses oleh derived class.

#### 6. Contoh Kasus tanpa Inheritance (C#)
```csharp
public class Orc
{
    public int Health { get; set; }
    public void Attack() { /* Implementasi serangan */ }
}

public class Goblin
{
    public int Health { get; set; }
    public void Attack() { /* Implementasi serangan yang mirip dengan Orc */ }
}

public class Witch
{
    public int Health { get; set; }
    public void CastSpell() { /* Implementasi sihir */ }
}
```
Di sini, metode `Attack` di kelas `Orc` dan `Goblin` bisa jadi sangat mirip, menunjukkan duplikasi kode.

#### 7. Contoh Kasus dengan Inheritance (C#)
```csharp
public class Monster
{
    public int Health { get; set; }
    public virtual void Attack() { /* Implementasi serangan dasar */ }
}

public class Orc : Monster
{
    // Pewarisan Health dan Attack sudah termasuk
}

public class Goblin : Monster
{
    // Pewarisan Health dan Attack sudah termasuk
    public override void Attack()
    {
        // Modifikasi perilaku serangan untuk Goblin
    }
}

public class Witch : Monster
{
    public void CastSpell() { /* Implementasi sihir */ }
}
```
Kelas `Orc` dan `Goblin` mewarisi `Health` dan `Attack` dari `Monster`, mengurangi duplikasi kode.


#### 8. Implicit Inheritance
Di C#, semua tipe data secara default mewarisi dari kelas `System.Object`.

#### 9. Method Overriding
Method overriding memungkinkan subclass untuk menyediakan implementasi spesifik yang berbeda dari metode yang diwarisi dari superclass.

#### 10. Access Modifier di Inheritance

Dalam C#, access modifiers berperan penting dalam menentukan bagaimana anggota kelas (seperti fields, properties, dan methods) dapat diakses, khususnya dalam konteks inheritance. Berikut penjelasan untuk masing-masing access modifier yang berhubungan dengan inheritance:

1. `public`:
   - Anggota dengan access modifier `public` dapat diakses dari mana saja, baik dalam kelas itu sendiri, kelas turunan, maupun kelas lain di luar hierarki inheritance.
   
2. `protected`:
   - Anggota dengan access modifier `protected` hanya dapat diakses dalam kelas itu sendiri dan oleh kelas turunan, tidak peduli apakah mereka berada di assembly yang sama atau berbeda.
   
3. `internal`:
   - Anggota dengan access modifier `internal` hanya dapat diakses oleh kode yang berada dalam assembly yang sama. Ini tidak terkait langsung dengan inheritance, tetapi berkaitan dengan visibilitas antar assembly.
   
4. `protected internal`:
   - Anggota dengan access modifier `protected internal` dapat diakses oleh kode yang berada di assembly yang sama atau oleh kelas turunan di assembly manapun. Ini adalah kombinasi dari `protected` dan `internal`.
   
5. `private protected`:
   - Anggota dengan access modifier `private protected` hanya dapat diakses oleh kelas turunan yang berada dalam assembly yang sama. Ini adalah kombinasi yang lebih restriktif dari `protected internal`, membatasi akses ke turunan dalam assembly yang sama.
   
6. `private`:
   - Anggota dengan access modifier `private` hanya dapat diakses oleh kelas itu sendiri. Mereka tidak dapat diakses oleh kelas turunan atau oleh kode di luar kelas.

Dalam konteks inheritance, `public` dan `protected` adalah access modifiers yang paling sering digunakan untuk memungkinkan kelas turunan mengakses dan mengoverride (jika diperlukan) anggota kelas induk. `internal` dan variasi `protected`-nya sering digunakan untuk mengontrol akses di level assembly. Modifier `private` secara eksplisit mencegah akses dari kelas turunan, yang berguna untuk menyembunyikan detail implementasi yang tidak seharusnya diexpose di luar kelas itu sendiri.

- `private`: Tidak dapat diwarisi sama sekali.
- `protected`: Hanya dapat diakses oleh kelas yang sama atau turunannya.
- `public`: Dapat diakses oleh siapa saja.

#### 11. Single vs Multiple Inheritance di C#
C# mendukung single inheritance (sebuah kelas hanya dapat mewarisi dari satu superclass) dan tidak mendukung multiple inheritance secara langsung, tetapi konsep serupa dapat dicapai menggunakan *interfaces*.