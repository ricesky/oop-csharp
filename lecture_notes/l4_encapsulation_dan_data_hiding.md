### Lecture Notes #4

**Kelas dan Objek**

**Enkapsulasi (Encapsulation)**

Enkapsulasi adalah salah satu dari empat prinsip utama dalam pemrograman berorientasi objek (OOP). Konsep ini merujuk pada pengemasan data (variabel) dan fungsi (metode) yang bekerja pada data tersebut ke dalam satu unit atau kelas. Enkapsulasi memungkinkan suatu objek untuk menyembunyikan detil internal dari objek tersebut terhadap objek lain, sehingga hanya menampilkan operasi yang diizinkan.

Dengan enkapsulasi, kita bisa:
- Menyembunyikan kompleksitas.
- Mencegah dari perubahan yang tidak diinginkan.
- Membuat kode lebih mudah untuk dijaga dan dikelola.

**Penyembunyian Data (Data Hiding)**

Penyembunyian data adalah sebuah teknik dalam enkapsulasi yang membatasi akses langsung ke beberapa komponen objek. Ini biasanya diimplementasikan dengan menggunakan hak akses seperti `private`, `protected`, dan `public`. 

Dalam C#, `private` adalah level akses yang paling membatasi, di mana anggota hanya bisa diakses dari dalam kelas itu sendiri. Ini adalah cara efektif untuk menyembunyikan data dan hanya memperbolehkan akses melalui metode yang didefinisikan dalam kelas, yang sering disebut sebagai *accessor* (untuk membaca data) dan *mutator* (untuk mengubah data).

**Contoh Kode dalam C#:**

```csharp
public class Account
{
    // Data yang disimpan secara private
    private decimal balance;

    // Konstruktor untuk inisialisasi balance
    public Account(decimal initialBalance)
    {
        balance = initialBalance;
    }

    // Metode untuk mendapatkan balance (Accessor)
    public decimal GetBalance()
    {
        return balance;
    }

    // Metode untuk menyetor uang (Mutator)
    public void Deposit(decimal amount)
    {
        if (amount > 0)
        {
            balance += amount;
        }
    }

    // Metode untuk menarik uang (Mutator)
    public bool Withdraw(decimal amount)
    {
        if (amount <= balance)
        {
            balance -= amount;
            return true;
        }
        return false;
    }
}
```

**Penggunaan:**

```csharp
class Program
{
    static void Main(string[] args)
    {
        Account myAccount = new Account(1000); // Membuat objek dengan balance awal 1000
        myAccount.Deposit(500); // Menyetor uang ke dalam akun
        Console.WriteLine(myAccount.GetBalance()); // Menampilkan balance, hasilnya akan 1500

        bool isWithdrawn = myAccount.Withdraw(200); // Mencoba menarik uang
        if (isWithdrawn)
        {
            Console.WriteLine($"Penarikan berhasil. Balance terkini: {myAccount.GetBalance()}");
        }
        else
        {
            Console.WriteLine("Penarikan gagal.");
        }
    }
}
```

Dalam contoh di atas, variabel `balance` adalah private, sehingga tidak dapat diakses atau dimodifikasi langsung dari luar kelas `Account`. Sebagai gantinya, kelas menyediakan metode `GetBalance`, `Deposit`, dan `Withdraw` untuk berinteraksi dengan `balance`. Ini adalah contoh dari enkapsulasi dan penyembunyian data.

**Access Modifier (Pengubah Akses)**

Dalam C#, hak akses atau *access modifier* mengontrol level visibilitas anggota kelas (variabel, properti, metode, dan konstruktor) kepada kode lain. Berikut adalah hak akses yang tersedia di C#:

- `public`: Anggota dapat diakses dari kode manapun dalam assembly atau assembly lain yang merujuknya.
- `private`: Anggota hanya dapat diakses dari dalam kelas atau struktur tempat mereka dideklarasikan.
- `protected`: Anggota hanya dapat diakses dari dalam kelas tempat mereka dideklarasikan, serta oleh turunan dari kelas tersebut.
- `internal`: Anggota dapat diakses oleh kode apa pun dalam assembly yang sama, tetapi tidak dari assembly lain.
- `protected internal`: Anggota dapat diakses oleh kode apa pun dalam assembly yang sama, atau oleh turunan dari kelas dalam assembly lain.
- `private protected`: Anggota hanya dapat diakses oleh kelas yang mengandung anggota tersebut, atau oleh kelas turunan yang terletak dalam assembly yang sama.

Penggunaan `access modifier` ini memungkinkan pengembang untuk lebih mengontrol bagaimana properti dan metode suatu objek diakses dan dimodifikasi. Dengan mengontrol akses ini, dapat ditegakkan prinsip enkapsulasi yang lebih baik.

**Contoh Kode dalam C#:**

```csharp
public class Employee
{
    // Data yang disimpan secara private
    private int id;
    private string name;
    protected decimal salary;

    // Konstruktor untuk inisialisasi data
    public Employee(int id, string name, decimal salary)
    {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    // Metode publik untuk mengakses data karyawan
    public string GetName()
    {
        return name;
    }

    // Metode internal untuk bekerja dengan gaji
    internal void RaiseSalary(decimal percentage)
    {
        if (percentage > 0)
        {
            salary += salary * percentage / 100;
        }
    }

    // Metode protected yang mungkin digunakan dalam turunan kelas Employee
    protected decimal CalculateBonus(decimal percentage)
    {
        return salary * percentage / 100;
    }
}

public class Manager : Employee
{
    public Manager(int id, string name, decimal salary) : base(id, name, salary)
    {
    }

    public void IncreaseSubordinateSalary(Employee employee, decimal percentage)
    {
        if (employee is Manager)
        {
            // Hanya Manager yang dapat menaikkan gaji Manager lain
            employee.RaiseSalary(percentage);
        }
    }
}
```

Pada contoh di atas, kita dapat melihat bagaimana `private`, `protected`, dan `internal` access modifiers digunakan untuk membatasi akses ke anggota kelas `Employee`. Kelas `Manager`, yang mewarisi dari `Employee`, dapat mengakses anggota yang `protected` seperti `salary`, tetapi tidak dapat mengakses anggota yang `private` dari `Employee` seperti `id` dan `name`.

Penggunaan access modifier memastikan bahwa hanya metode yang sesuai yang dapat mengakses dan memodifikasi data, melindungi objek dari perubahan yang tidak diinginkan dan tidak aman dari kode luar. Ini adalah prinsip enkapsulasi yang sangat penting dalam membangun aplikasi yang aman dan mudah untuk dipelihara.

Referensi: 
- [Access Modifiers in C#](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)