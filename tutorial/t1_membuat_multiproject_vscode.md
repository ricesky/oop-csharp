### Tutorial #1

#### Membuat Solusi C# dengan Multi Project di VSCode

Di tutorial ini kita akan membuat sebuah solusi sederhana untuk mencetak string **Hello, Nama!**. Solusi bernama **HelloWorld** yang berisi dua proyek menggunakan Visual Studio Code dan C#. Proyek pertama bernama **HelloConsole** (Console Application) sebagai startup project, dan proyek kedua bernama **HelloLibrary** (Class Library). **HelloConsole** akan memanggil metode `SayHello(string name)` dari kelas `HelloPrinter` yang ada di **HelloLibrary**.

Berikut adalah hierarki struktur solusi dan project:

```plaintext
HelloWorldSolution/
│
├── HelloWorld.sln
│
├── HelloConsole/
│   ├── HelloConsole.csproj
│   └── Program.cs
│
└── HelloLibrary/
    ├── HelloLibrary.csproj
    └── HelloPrinter.cs
```

### Penjelasan Struktur:
- `HelloWorldSolution/`: Folder utama yang menampung seluruh proyek dan file solusi.
  - `HelloWorld.sln`: File solusi untuk menampung proyek-proyek dalam solusi.
  - `HelloConsole/`: Proyek Console Application.
    - `HelloConsole.csproj`: File proyek untuk HelloConsole.
    - `Program.cs`: File utama yang berisi `Main` method yang memanggil `HelloPrinter`.
  - `HelloLibrary/`: Proyek Class Library.
    - `HelloLibrary.csproj`: File proyek untuk HelloLibrary.
    - `HelloPrinter.cs`: File kelas `HelloPrinter` yang berisi metode `SayHello`.

### Langkah 1: Persiapkan Lingkungan
Pastikan Anda telah menginstal .NET SDK dan Visual Studio Code. Untuk memeriksa apakah .NET SDK telah terpasang, jalankan perintah ini di terminal:

```bash
dotnet --version
```

Jika belum terpasang, unduh dan instal dari [sini](https://dotnet.microsoft.com/download).

### Langkah 2: Buat Folder Proyek
Buat folder baru di komputer Anda untuk menampung solusi dan proyek-proyeknya, misalnya:

```bash
mkdir HelloWorldSolution
cd HelloWorldSolution
```

### Langkah 3: Buat Solusi Baru
Jalankan perintah ini untuk membuat file solusi (.sln) yang akan menampung proyek-proyek:

```bash
dotnet new sln -n HelloWorld
```

### Langkah 4: Buat Proyek Console (HelloConsole)
Sekarang, buat proyek Console Application di dalam solusi ini. Jalankan perintah:

```bash
dotnet new console -n HelloConsole
```

Ini akan membuat folder `HelloConsole` dengan semua file proyek yang diperlukan.

### Langkah 5: Buat Proyek Class Library (HelloLibrary)
Selanjutnya, buat proyek Class Library yang akan berisi kelas `HelloPrinter`:

```bash
dotnet new classlib -n HelloLibrary
```

Ini akan membuat folder `HelloLibrary` dengan file `.csproj` dan `Class1.cs`.

### Langkah 6: Tambahkan Proyek ke Solusi
Setelah proyek dibuat, tambahkan kedua proyek ini ke dalam solusi **HelloWorld**:

```bash
dotnet sln add HelloConsole/HelloConsole.csproj
dotnet sln add HelloLibrary/HelloLibrary.csproj
```

### Langkah 7: Buat Kelas HelloPrinter di HelloLibrary
Sekarang, kita perlu memodifikasi **HelloLibrary** untuk menambahkan kelas `HelloPrinter`. Buka file `Class1.cs` di **HelloLibrary** dan ubah isinya menjadi seperti ini:

```csharp
namespace HelloLibrary
{
    public class HelloPrinter
    {
        public void SayHello(string name)
        {
            Console.WriteLine($"Hello, {name}!");
        }
    }
}
```

### Langkah 8: Tambahkan Referensi Proyek
Agar **HelloConsole** dapat menggunakan **HelloLibrary**, tambahkan referensi dari proyek **HelloConsole** ke **HelloLibrary**:

```bash
dotnet add HelloConsole/HelloConsole.csproj reference HelloLibrary/HelloLibrary.csproj
```

### Langkah 9: Modifikasi HelloConsole
Buka file `Program.cs` di proyek **HelloConsole** dan ubah isinya menjadi seperti ini:

```csharp
using HelloLibrary;

class Program
{
    static void Main(string[] args)
    {
        HelloPrinter printer = new HelloPrinter();
        printer.SayHello("World");
    }
}
```

### Langkah 10: Setel HelloConsole sebagai Startup Project
Pastikan proyek **HelloConsole** menjadi proyek startup. Untuk melakukannya, saat menjalankan solusi, pastikan Anda berada di direktori solusi dan jalankan:

```bash
dotnet run --project HelloConsole
```

### Langkah 11: Bangun dan Jalankan Solusi
Untuk membangun solusi dan memastikan semuanya berjalan dengan baik, gunakan perintah:

```bash
dotnet build
```

Setelah berhasil dibangun, Anda dapat menjalankan proyek **HelloConsole**:

```bash
dotnet run --project HelloConsole
```

Jika semuanya benar, output yang akan Anda lihat di terminal adalah:

```bash
Hello, World!
```

### Kesimpulan
Anda telah berhasil membuat solusi **HelloWorld** yang berisi dua proyek: **HelloConsole** sebagai aplikasi konsol, dan **HelloLibrary** sebagai library dengan metode `SayHello` di kelas `HelloPrinter`. **HelloConsole** memanggil metode dari **HelloLibrary** untuk menampilkan pesan "Hello, World!" di konsol.