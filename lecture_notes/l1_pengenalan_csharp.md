### Lecture Notes #1

#### Pengenalan C# dan Kompilasi menggunakan C# Compiler

1. **Bahasa Pemrograman C#**
   - C# adalah bahasa pemrograman yang berbasis objek dan dikembangkan oleh Microsoft sebagai bagian dari .NET framework.
   - C# dirancang untuk pengembangan aplikasi Windows tetapi sekarang bisa dijalankan di berbagai sistem operasi menggunakan .NET Core yang merupakan platform lintas platform.
   - Aplikasi C# dijalankan di atas Common Language Runtime (CLR), yang mirip dengan JVM pada Java, yang menyediakan layanan seperti manajemen memori, keamanan tipe, dan pengecualian (exception handling).
   - C# memiliki interoperabilitas yang kuat dengan bahasa .NET lainnya dan mendukung prinsip-prinsip pemrograman seperti enkapsulasi, pewarisan, dan polimorfisme.

2. **Struktur Program C#**
   ```csharp
   using System;

   class Program {
       public static void Main(string[] args) {
           Console.WriteLine("Hello World");
       }
   }
   ```
   - Struktur di atas terdiri dari deklarasi kelas `Program` dan fungsi `Main` yang merupakan titik masuk (entry point) dari aplikasi C#.
   - Fungsi `Main` harus dideklarasikan sebagai `static` dan dapat memiliki parameter `args` yang memungkinkan argumen baris perintah.

3. **Unit Kompilasi C#**
   - Kode sumber C# disimpan dalam file dengan ekstensi `.cs`.
   - Setiap file `.cs` bisa berisi lebih dari satu kelas, tetapi hanya satu yang dapat berisi metode `Main`.
   - Nama file tidak harus sama dengan kelas yang ada di dalamnya, yang berbeda dengan Java.

4. **Model Kompilasi C#**
   - Kode sumber C# dikompilasi menjadi Intermediate Language (IL), yang kemudian dikompilasi menjadi native code oleh CLR pada waktu eksekusi.
   - Hasil kompilasi adalah file berekstensi `.exe` atau `.dll` tergantung pada jenis aplikasi yang dikembangkan.

5. **Perintah-perintah Kompilasi**
   - Menggunakan C# Compiler (csc.exe) untuk mengompilasi kode sumber:
     ```
     csc Program.cs
     ```
   - Perintah di atas akan menghasilkan file `Program.exe` yang dapat dieksekusi.

6. **Menjalankan File Executable**
   - File executable yang dihasilkan oleh compiler dapat dijalankan langsung di Windows atau menggunakan command `dotnet` pada .NET Core di sistem operasi lain.
   - Perintah untuk menjalankan executable:
     ```
     Program.exe
     ```
     atau
     ```
     dotnet Program.dll
     ```
   - CLR akan mengkonversi IL menjadi native code dan menjalankannya.