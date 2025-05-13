# Penjelasan Server dan Client

## Pengertian Server

Server adalah sebuah sistem komputer yang menyediakan layanan tertentu dalam sebuah jaringan. Server bertugas menerima permintaan (request) dari client, memprosesnya, dan mengirimkan respon (response) kembali ke client. Server biasanya memiliki spesifikasi hardware yang lebih tinggi dan berjalan secara terus-menerus untuk melayani banyak client sekaligus.

Contoh layanan server:
- Web server (menyajikan halaman web)
- Database server (menyimpan dan mengelola data)
- File server (menyimpan dan membagikan file)

## Pengertian Client

Client adalah perangkat atau aplikasi yang meminta layanan atau data dari server. Client mengirimkan permintaan ke server, kemudian menerima dan menampilkan hasil dari server. Client bisa berupa komputer, smartphone, atau aplikasi tertentu.

Contoh client:
- Browser (Google Chrome, Firefox)
- Aplikasi email
- Aplikasi mobile

## Ilustrasi Server dan Client

![Ilustrasi Server dan Client](https://csirt.bpbatam.go.id/storage/post-image/pSnnPDx0gB4Jhz2txvKfLQ2uqHj8M4hNEbQzhb7k.png)

Pada gambar di atas, terlihat beberapa client (komputer) yang terhubung ke satu server melalui jaringan. Setiap client dapat berkomunikasi dengan server untuk meminta layanan atau data.

## Contoh Sederhana Komunikasi Server dan Client dengan Python

### Server (Python)

```python
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(('localhost', 12345))
server_socket.listen(1)
print("Server siap menerima koneksi...")

while True:
    client_socket, addr = server_socket.accept()
    print(f"Koneksi dari {addr}")
    data = client_socket.recv(1024).decode()
    print(f"Pesan dari client: {data}")
    client_socket.send("Pesan diterima server".encode())
    client_socket.close()
```

### Client (Python)

```python
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(('localhost', 12345))
client_socket.send("Halo server!".encode())
data = client_socket.recv(1024).decode()
print(f"Pesan dari server: {data}")
client_socket.close()
```

Pada contoh di atas, server menunggu koneksi dari client. Client mengirim pesan ke server, lalu server membalas pesan tersebut.


