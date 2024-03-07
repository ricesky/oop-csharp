### Lecture Notes #2

#### Pengenalan Visual Studio 2022 dan Pengembangan Aplikasi dengan C#

1. **Integrated Development Environment (IDE) untuk C#**

   Visual Studio 2022 adalah sebuah IDE yang umum digunakan untuk pengembangan aplikasi dengan bahasa C#. Berbeda dengan editor teks sederhana seperti Notepad, Visual Studio menyediakan fitur lengkap yang mendukung siklus pengembangan perangkat lunak seperti coding, kompilasi, dan debugging. Fitur-fitur ini meliputi:

   - **Text Editor**: Mendukung penyuntingan kode, syntax highlighting, dan penataan kode otomatis.
   - **Code Completion**: Memberikan saran kode berdasarkan konteks yang sedang dikerjakan.
   - **Compiler**: Terintegrasi dalam IDE, memungkinkan kompilasi dengan perintah sederhana.
   - **Debugger**: Memudahkan proses debugging dengan visualisasi breakpoint, stack trace, dan variabel.
   - **Dukungan Bahasa Pemrograman**: Visual Studio mendukung C# dan banyak bahasa lainnya, dengan dukungan fitur-fitur khusus dari masing-masing bahasa.

2. **Pengenalan Visual Studio 2022**

   Visual Studio 2022 adalah versi terbaru dari IDE populer dari Microsoft. IDE ini mendukung pengembangan beragam tipe aplikasi, termasuk aplikasi desktop, web, dan mobile. Untuk menjalankan Visual Studio 2022, sistem operasi Windows yang kompatibel diperlukan. Pada saat pertama kali menjalankan, Visual Studio akan meminta pengguna untuk melakukan sign in dengan akun Microsoft dan menyesuaikan environment pengembangan sesuai kebutuhan.

   Tampilan utama Visual Studio terdiri dari:

   - **Menubar**: Menu atas yang menyediakan berbagai fungsi IDE.
   - **Toolbar**: Berisi tombol-tombol shortcut untuk akses fungsi cepat.
   - **Solution Explorer**: Menampilkan struktur proyek dan memungkinkan navigasi file.
   - **Editor**: Area kerja untuk menulis dan menyunting kode.
   - **Properties Window**: Menampilkan dan mengedit properti dari item yang dipilih.
   - **Output Window**: Menampilkan hasil dari build dan output dari aplikasi yang dijalankan.

3. **Membuat dan Menjalankan Proyek C#**

   Langkah-langkah untuk membuat proyek C# di Visual Studio adalah sebagai berikut:

   1. Pilih `File > New > Project` dari menubar.
   2. Pilih template proyek yang diinginkan, misalnya `Console App (.NET Core)`.
   3. Isi nama proyek, misalnya `MyFirstCSharpApp`, dan tentukan lokasi penyimpanan.
   4. Pilih `Create` untuk membuat proyek baru.

   Contoh struktur kode sederhana pada file C#:

   ```csharp
   // MyFirstCSharpApp.cs
   using System;

   namespace MyFirstCSharpApp
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello, World!");
           }
       }
   }
   ```

   Untuk menjalankan aplikasi, tekan tombol `Start` atau `F5` untuk menjalankan dalam mode debugging, atau `Ctrl+F5` untuk menjalankan tanpa debugging.

4. **Melakukan Debugging dengan Visual Studio**

   Visual Studio menyediakan lingkungan debugging yang canggih. Fitur-fitur debugging termasuk:

   - **Breakpoint**: Menandai titik di mana eksekusi akan berhenti.
   - **Step Over**: Melanjutkan eksekusi ke statement berikutnya di luar fungsi saat ini.
   - **Step Into**: Memasuki fungsi atau method untuk mengikuti eksekusi dari dalam.
   - **Step Out**: Keluar dari fungsi atau method yang saat ini sedang dieksekusi.
   - **Start/Continue**: Memulai atau melanjutkan eksekusi hingga breakpoint berikutnya.
   - **Watch Windows**: Memantau nilai dari variabel selama proses debugging.

Selalu pastikan bahwa Anda telah menginstall .NET SDK yang sesuai dengan proyek yang ingin dikembangkan agar semua fitur dapat berfungsi dengan baik di Visual Studio 2022.