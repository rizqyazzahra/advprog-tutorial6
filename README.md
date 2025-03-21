Nama: Rizqya Az Zahra Putri

NPM: 2306244936

Kelas: B

## Reflection
### Commit 1 Reflection notes
**Inside the `handle_connection` Method**

Method `handle_connection` digunakan untuk menangani koneksi TCP yang diterima oleh server. Hal ini terlihat pada fungsi `handle_connection` yang menerima parameter `stream` bertipe `TcpStream`. Kemudian, `BufReader` digunakan untuk membungkus `stream` agar dapat mempercepat pembacaan data dari stream. Permintaan HTTP yang diterima server selanjutnya dibaca baris demi baris dengan metode iterator `.lines()` dan hasilnya diproses dengan metode `.map(|result| result.unwrap())` untuk mengambil nilai String yang valid. Selanjutnya, metode `.take_while(|line| !line.is_empty())` digunakan untuk terus mengambil baris dari permintaan HTTP selama baris tersebut tidak kosong. Terakhir, hasil pembacaan yang didapat disatukan menjadi sebuah vektor (`Vec<String>`) menggunakan metode `.collect()` dam disimpan dalam variabel `http_request`.

### Commit 2 Reflection notes
Pada kode sebelumnya, fungsi `handle_connection` hanya membaca dan menampilkan permintaan HTTP dari _client_. Setelah diperbarui, fungsi ini tidak hanya membaca request tetapi juga mengirimkan respons HTTP kembali ke client. `"HTTP/1.1 200 OK"` digunakan untuk menunjukan bahwa permintaan berhasil diproses. Setelah permintaan berhasil diproses, server akan membaca isi file HTML dan mengirimkannya sebagai _body_ respons menggunakan `fs::read_to_string("hello.html")`. Lalu, terdapat penggunaan `.len()` yang penting untuk komunikasi HTTP agar browser _client_ dapat mengetahui seberapa besar data yang diterima. Setelah menyusun string respons lengkap dengan memanfaatkan `format!`, data tersebut dikirimkan ke _client_ menggunakan `stream.write_all(response.as_bytes()).unwrap()`.

![Commit 2 screen capture](/assets/images/commit2.png)