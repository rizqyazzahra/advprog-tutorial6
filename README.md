Nama: Rizqya Az Zahra Putri

NPM: 2306244936

Kelas: B

## Reflection
1. Inside the `handle_connection` Method

Method `handle_connection` digunakan untuk menangani koneksi TCP yang diterima oleh server. Hal ini terlihat pada fungsi `handle_connection` yang menerima parameter `stream` bertipe `TcpStream`. Kemudian, `BufReader` digunakan untuk membungkus `stream` agar dapat mempercepat pembacaan data dari stream. Permintaan HTTP yang diterima server selanjutnya dibaca baris demi baris dengan metode iterator `.lines()` dan hasilnya diproses dengan metode `.map(|result| result.unwrap())` untuk mengambil nilai String yang valid. Selanjutnya, metode `.take_while(|line| !line.is_empty())` digunakan untuk terus mengambil baris dari permintaan HTTP selama baris tersebut tidak kosong. Terakhir, hasil pembacaan yang didapat disatukan menjadi sebuah vektor (`Vec<String>`) menggunakan metode `.collect()` dam disimpan dalam variabel `http_request`.