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