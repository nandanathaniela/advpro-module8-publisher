# Module 8 Publisher

#### Nanda Nathaniela Meizari - 2206824136

### How many data your publisher program will send to the message broker in one run?
Program publisher akan mengirimkan 5 pesan ke broker pesan dalam satu siklus, karena setiap kali `p.publish_event` dipanggil, satu pesan akan dikirim, dan terdapat 5 pemanggilan dalam fungsi utamanya

###
URL `amqp://guest:guest@localhost:5672` digunakan untuk menghubungkan ke broker AMQP. Dalam program publisher dan subscriber, URL tersebut mengarah ke broker AMQP yang beroperasi di mesin lokal. Penjelasannya adalah sebagai berikut:
1. `amqp://` adalah protokol yang digunakan, menandakan bahwa koneksi akan dibuat menggunakan protokol AMQP
2. Bagian `guest:guest@` menunjukkan username dan password untuk autentikasi. Untuk RabbitMQ, secara default, username dan password adalah `guest`
3. `localhost` mengacu pada nama host mesin di mana broker berjalan, menandakan bahwa broker beroperasi pada mesin yang sama di mana program publisher dan subscriber dijalankan
4. `5672` adalah nomor port default tempat broker AMQP menerima koneksi

Publisher dan subscriber perlu terhubung ke broker yang sama agar dapat menerima dan mengirim pesan, sehingga mereka menggunakan string koneksi yang sama

## Running RabbitMQ as message broker
![Running RabbitMQ as message broker](assets/images/Running%20RabbitMQ%20as%20message%20broker.jpg)

## Sending and processing event
![Sending and processing event](assets/images/Sending%20and%20processing%20event.jpg)
Ketika RabbitMQ sedang berjalan, dan kita menjalankan cargo run pada publisher dan subscriber, maka publisher akan mengirimkan 5 event data ke message broker yang nantinya akan diterima oleh subscriber

## Monitoring chart based on publisher
![Monitoring chart based on publisher](assets/images/Monitoring%20chart%20based%20on%20publisher.jpg)
Jika cargo run dijalankan beberapa kali dalam satu detik dan hanya sekali dalam satu detik, kita dapat melihat perbedaan dalam message rates. Ini menunjukkan bahwa message rates meningkat ketika message broker menerima data dari publisher, dan seberapa cepat message rates tersebut dipengaruhi oleh jumlah data yang diterima message broker dari publisher dalam satu detik