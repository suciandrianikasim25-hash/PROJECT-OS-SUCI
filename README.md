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
- `mkdir` → membuat folder baru.
- `touch` → membuat file kosong dengan cepat.
- `echo` → menulis teks ke dalam file.
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
- find.-maxdepth 1 -type f -name "*.ext" → mencari file berdasarkan ekstensi di direktori saat ini.
- -exec mv {} folder/; → memindahkan file hasil pencarian ke folder sesuai.
- chmod +x → memberi izin eksekusi ke script.
# LANGKAH 3 FUNGSI PENCARIAN
_Karena saya sudah punya script pencarian file yang bisa mencari berdasarkan nama, ukuran, dan isi konten. Jadi saya langsunng baut fungsi pencariannya._
# Buat file search_file.sh
~~~
nano search_file.sh
~~~
(Deskripsi gambar)
# https://github.com/suciandrianikasim25-hash/PROJECT-OS-SUCI/edit/main/README.md
~~~
#!/bin/bash
# Script: search_file.sh
# Fungsi: Mencari file berdasarkan nama, ukuran, atau konten

cd ~/project_1

echo "=== PENCARIAN FILE ==="
echo "1. Cari berdasarkan nama"
echo "2. Cari berdasarkan ukuran"
echo "3. Cari berdasarkan isi konten"
read -p "Pilih opsi (1/2/3): " opsi

case $opsi in
  1)
    read -p "Masukkan nama atau pola file (contoh: *.txt): " nama
    echo "Hasil pencarian:"
    find . -type f -name "$nama"
    ;;
  2)
    read -p "Masukkan batas ukuran (contoh: +1M untuk lebih dari 1MB, -500k untuk kurang dari 500KB): " ukuran
    echo "Hasil pencarian:"
    find . -type f -size "$ukuran"
    ;;
  3)
    read -p "Masukkan kata kunci yang ingin dicari dalam file: " keyword
    echo "Hasil pencarian:"
    grep -r "$keyword" .
    ;;
  *)
    echo "Opsi tidak valid."
    ;;
esac
~~~
# Beri hak eksekusi
~~~
chmod +x search_file.sh
~~~
Penjelasan:
- find . -type f -name "*.txt" → mencari file dengan pola nama tertentu.
- find . -size +1M → mencari file berukuran lebih dari 1 MB.
- grep -r "teks" → mencari teks di dalam isi file secara rekursif.
# LANGKAH 4 - Generate laporan file sistem
_Script ini akan membuat laporan statistik tentang file di direktori proyek, lalu menyimpannya ke report.txt._
# Buat file report.sh
(Deskripsi gambar)
# https://github.com/suciandrianikasim25-hash/PROJECT-OS-SUCI/edit/main/README.md
~~~
#!/bin/bash
# Script: generate_report.sh
# Fungsi: Membuat laporan statistik file sistem

cd ~/project_f1

echo "=== LAPORAN FILE SISTEM ===" > report.txt
echo "Tanggal: $(date)" >> report.txt
echo "" >> report.txt

echo "--- Jumlah File dan Folder ---" >> report.txt
ls -lR | wc -l >> report.txt
echo "" >> report.txt

echo "--- Ukuran Total Folder ---" >> report.txt
du -sh . >> report.txt
echo "" >> report.txt

echo "--- Daftar 10 File Terbesar ---" >> report.txt
find . -type f -exec du -h {} + | sort -rh | head -10 >> report.txt
echo "" >> report.txt

echo "--- Statistik Berdasarkan Ekstensi ---" >> report.txt
echo "TXT: $(find . -type f -name '*.txt' | wc -l)" >> report.txt
echo "JPG: $(find . -type f -name '*.jpg' | wc -l)" >> report.txt
echo "PDF: $(find . -type f -name '*.pdf' | wc -l)" >> report.txt
echo "LOG: $(find . -type f -name '*.log' | wc -l)" >> report.txt

echo "" >> report.txt
echo "=== Selesai! Laporan disimpan di report.txt ==="
~~~
# Beri hak eksekusi
~~~
chmod +x report.sh
~~~
# Eksekusi file yang telah dibuat
~~~
./report.sh
~~~
_Jadi, ketika dijalankan perintah (./report.sh) maka laporan akan otomatis tersimpan di file report.sh_
# Melihat isi laporan
~~~
cat report.sh
~~~
Penjelasan:
- find . -type f -name "*.txt" → mencari file dengan pola nama tertentu.
- find . -size +1M → mencari file berukuran lebih dari 1 MB.
- grep -r "teks" → mencari teks di dalam isi file secara rekursif.
