# PROJECT-OS-SUCI
Project Based Learing 1
# LANGKAH 1 BUAT STRUKTUR DIREKTORI
# Berikut contoh membuat direktori project_1
#(Deskripsi gambar)
# https://github.com/suciandrianikasim25-hash/PROJECT-OS-SUCI/edit/main/README.md
~~~
#ubuntu@suci:~ mkdir project_1
~~~
# Berikut contoh perintah berpindah direktori ke project_1 dan membuat folder documents images archives logs
(Deskripsi gambar)
# https://github.com/suciandrianikasim25-hash/PROJECT-OS-SUCI/edit/main/README.md
~~~
cd project_1
~~~
~~~
mkdir document images archives  logs
~~~
# Berikut contoh perintah membuat 20 file sample:
(Deskripsi gambar)
# https://github.com/suciandrianikasim25-hash/PROJECT-OS-SUCI/edit/main/README.md
~~~
touch file{1..10}.txt file{11..15}.jpg file{16..18}.pdf file(19..20}.log
~~~
# Berikut contoh perintah memasukkan sebuah teks ke masing-masing file yang berbeda
(Deskripsi gambar)
# https://github.com/suciandrianikasim25-hash/PROJECT-OS-SUCI/edit/main/README.md
~~~
echo "Contoh dokumen" > file1.txt
~~~
~~~
echo "Data gambar" >> file11.jpg
~~~
~~~
echo "Log sistem contoh" >> file20.log
~~~
Penjelasan:
- `mkdir` : membuat folder baru.
- touch : membuat file kosong dengan cepat.
- echo : menulis teks ke dalam file.
# LANGKAH 2 SCRIPT OPERASI FILE
# Buat script organisasi file di dalam direktori projek:
~~~
nano operasi_file.sh
~~~
# ISI SCRIPT
(Deskripsi gambar)
# https://github.com/suciandrianikasim25-hash/PROJECT-OS-SUCI/edit/main/README.md
~~~
#!/bin/bash
# Script untuk mengorganisasi file berdasarkan ekstensi

# Pastikan berada di direktori proyek
cd ~/project_1

# Pindahkan file sesuai ekstensi
find . -maxdepth 1 -type f -name "*.txt" -exec mv {} documents/ \;
find . -maxdepth 1 -type f -name "*.jpg" -exec mv {} images/ \;
find . -maxdepth 1 -type f -name "*.pdf" -exec mv {} archives/ \;
find . -maxdepth 1 -type f -name "*.log" -exec mv {} logs/ \;

# Konfirmasi hasil
echo "File berhasil dipindahkan ke folder sesuai ekstensi!"
ls documents images archives logs
~~~
# Beri hak eksekusi:
~~~
chmod +x operasi_file.sh
~~~
~~~
./operasi_file.sh
~~~
Penjelasan:
- find.-maxdepth 1 -type f -name "*.ext" -> mencari file berdasarkan ekstensi di direktori saat ini
- -exec mv {} folder/; ~> memindahkan file hasil pencarian ke folder sesuai.
- chmod +x _> memberi izin eksekusi ke script.

