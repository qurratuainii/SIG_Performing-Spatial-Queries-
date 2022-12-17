# SIG_Performing-Spatial-Queries-

*Tutorial Performing Spatial Queries 

1. Download terlebih dahulu file metro_stations_accessbility.zip dan Bars_pubs_with_patron_capacity

2. Temukan file metro_stations_accessbility.zip di Perambang QGIS dan kembangkan. Pilih file metro_stations_accessbility dan seret ke kanvas. Metro_stations_accessbility layer baru akan dimuat di panel Layers (*Gambar 1*)

3. Lapisan data untuk data bar dan pub dalam format CSV. Untuk memuatnya di QGIS, pilih layer lalu add layer lalu pilih Add Delimited Text Layer ... (*Gambar 2*)

4. Pada Data Source Manager Delimited Text, pilih file Bars_and_pubs_with_patron_capacity.csv yang diunduh sebagai file name. Kolom bidang X dan bidang Y harus dipilih secara otomatis untuk masing-masing koordinat x dan koordinat y. Klik add (*Gambar 3*)

5. Kita akan melihat layer Bars_and_pubswith_patron_capacity baru ditambahkan ke panel layers. Kedua layer input berada di Geographic Coordinate Reference System (CRS) EPSG:4326 WGS84. Untuk melakukan analisis spasial, disarankan untuk menggunakan Projected Coordinate Reference System (CRS). Jadi sekarang kita akan memproyeksikan ulang kedua layer ke CRS regional yang sesuai yang meminimalkan distorsi dan memungkinkan kita bekerja dalam satuan jarak seperti meter (*Gambar 4*)

6. Cari dan temukan Vector General lalu Reprojected lyer tool. Klik dua kali untuk menampilkannya (*Gambar 5*)

7. Pilih Bars_and_pubs_with_patron_capacity sebagai lapisan input. Klik tombol Select CRS di sebelah target CRS (*Gambar 6*)

8. Saat memilih sistem koordinat yang diproyeksikan untuk analisis, tempat pertama yang harus dicari adalah CRS regional untuk area yang diminati. Untuk Australia, MAp Grid of Australia (MGA) 2020 adalah sistem grid berbasis UTM yang digunakan untuk pemetaan lokal dan regional (*Gambar 7*)

9. Selanjutnya, klik tombol ... di sebelah Reprojected dan pilih simpan ke GeoPackage. Geopackage adalah data spasial format data terbuka yang direkomendasikan dan merupakan format pertukaran data default untuk QGIS3. Ssatu file GeoPackage,gpkg dapat berisi beebrapa layer vektor dan raster dan simpan dengan nam spatialquery lalu klik save (*Gambar 8*)

10. Saat diminta nama lapisan, masukkan bar_and_pubs dan klik OK. Lalu klik Run untuk memproyeksikan ulang lapisan (*Gambar 9*)

11. Jendela akan beralih ke tab Log dan kita akan melihat algoritme berjalan dan membuat lapisan keluaran bar_and_pubs baru (*Gambar 10*)

12. Sekarang kita akan memproyeksikan ulang layer metro_stations_accessbility. Beralih kemabli ke tab Parameter di jendela Reprojected layer. Pilih metro_stations_accessbility sebagai lapisan input. Pertahankan Target CRS yang sama. selanjutnya, klik tombol ... di sebelah diproyeksikan ulang dan pilih simpan ke GeoPackage. Pilih file output spatialquery yang sama. MAsukkan metro_stations sebagai nama layer. Klik Run (*Gambar 11*)

13. Kembali ke jendela utama QGIS, kita akan melihat 2 layer beru dimuat di panel layer : bars_and_pubs dan metro_stations. Kita dapat mematikan lapisan asli. Sekarang, kita siap untuk melakukan kueri spasial. Karena kita tertarik untuk memilih bar dan pub dalam jarak 500m dari station metro, langkah pertama adalah membuat buffer di sekitar stasiun metro yang mewakili area pencarian. Cari vector geometry lalu buffer tool di processing toolbox (*Gambar 12*)

14. Dalam uffer pilih metro_stations sebagai lapisan input. TEtapkan 500 meter sebagai jarak. Simpan output ke geopackage spatialquery yang sama dan masukkan metro_stations_buffers sebagai nama layer. Klik Run (*Gambar 13*)

15. Kita akan melihat layer metro_stations_buffers baru dimuat di panel layers. Sekarang kita dapat mengetahuo titik mana dari layer bars_and_pubs yang termasuk dalam poligon dari layer metro_stations_buffers. Cari vector selection lalu extract by location dari processing toolbox (*Gambar 14*)

16. Pada Extract by location, pilih bar_and_pubs sebagai fitus extract. Centang Intersect sebagai predikat geometri. tetapkan metro_stations_buffers dengan membandingkan fitur dari simpan output ke geopackage spatialquery sebagai layer yang dipilih. Klik Run (*Gambar 15*)

17. Setelah pemrosesan selesai, kita akan melihat layer yang dipilih ditambahkan ke panel layers. Perhatikan bahwa lapisan ini hanya berisi poin dari bars_andPubs yang termasuk dalam poligon buffer (*Gambar 16*)

18. Analisi kita selesai. Kita mungkin memperhatikan bahwa poligon penyangga terlihat berbentuk oval. Ini karena proyek CRS masih disetel ke EPSG:4236. Untuk memvisualisasikan hasil dengan lebih baik, kita dapat pilih project lalu properties CRS dan pilih GDA 2020/MGA zone 55 / EPSG:7855 yang kita gunakan untuk analisis. Setelah diatur ke CRS ini, buffer akan muncul dalam bentuk yang benar (*Gambar 17*)
