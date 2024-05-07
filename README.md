![](docs/client_communication.png)

# Experiment 2.1: Original code, and how it run
Setelah menjalankan server, client dapat mengirim pesan. Salah satu hal unik adalah setiap suatu client mengetikkan pesan, pesan tersebut dikirimkan ke server yang kemudian disebarkan ke semua client yang terhubung. Sehingga semua client dapat melihat pesan-pesan yang dikirim oleh client lainnya secara real-time.

# Experiment 2.2: Modifying port
Merubah lokasi port pada server ada pada kode `let listener = TcpListener::bind("127.0.0.1:8080").await?;` yang berarti mendengarkan pada lokasi 127.0.0.1 port 8080 menggunakan komunikasi TCP. Websocket tidak perlu dispesifikasikan pada server dikarenakan WebSockets sendiri adalah protokol yang dibuat di atas TCP dan sudah dihandle library. Sedangkan pada server berada pada `let (mut ws_stream, _) = ClientBuilder::from_uri(Uri::from_static("ws://127.0.0.1:8080"))` dimana `ws` menandakan protokol websocket berlokasi 127.0.0.1 port 8080. 

# Experiment 2.3: Small changes, add IP and Port
pada server pengiriman text diubah menjadi `bcast_tx.send(format!("{} : {}", addr, text))?;`. Dengan begini server otomatis mengirim addres darimana pesan tersebut diterima. Untuk file lain tidak ada perubahan, kita dapat melihat addres client mana yang mengirim dari pesan tersebut.