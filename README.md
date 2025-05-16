# Module 09
###### Deanita Sekar Kinasih
###### 2306229405

## a. How much data your publisher program will send to the message broker in one run?

Publisher akan mengirimkan 5 data ke message broker dalam satu kali eksekusi (one run). Setiap data yang dikirim merupakan pesan berisi UserCreatedEventMessage yang terdiri dari kombinasi user_id dan user_name. Pada main.rs, terdapat 5 kali pemanggilan method publish_event() dimana setiap pemanggilan mengirimkan 1 UserCreatedEventMessage sebagai parameter. Dengan demikian, setiap kali publisher dijalankan, maka akan ada 5 event yang dikirimkan ke message broker.

## b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

URL “amqp://guest:guest@localhost:5672” memiliki arti bahwa keduanya terhubung ke message broker, seperti RabbitMQ, yang sama. URL ini adalah informasi koneksi yang digunakan oleh publisher dan subscriber untuk berkomunikasi dengan message broker.

- `guest:guest` adalah format username:password default untuk login ke message broker.

- `localhost` adalah hostname yang menunjukkan bahwa broker berjalan di local machine.

- `5672` adalah port number yang digunakan secara default untuk menerima koneksi AMQP.

Dengan menggunakan URL yang sama, publisher dan subscriber membentuk komunikasi terintegrasi dimana keduanya terhubung ke server AMQP yang sama. Hal ini memastikan bahwa pesan yang dipublikasikan oleh publisher dapat diterima dan diproses oleh subscriber dalam satu sistem messaging. Server AMQP berperan sebagai perantara (broker) yang menjembatani komunikasi antara publisher dan subscriber.

## Running RabbitMQ as message broker:
![Message broker](images/message_broker.png)

## Running RabbitMQ with one connection:
![One connection](images/running_one_connection.png)

## Running cargo run from the console:
![Publisher console](images/publisher_console.png)
![Subsciber console](images/subscriber_console.png)

Kedua gambar berikut merupakan tampilan console yang saya miliki ketika saya menjalankan `cargo run` pada subscriber dan publisher. Publisher mengirimkan 5 event kepada message broker yang kemudian diterima dan diproses oleh publisher, ditandai dengan output yang dihasilkan pada console subscriber.

## Running RabbitMQ monitoring chart:
![Monitoring chart](images/monitoring_chart.png)

Spike pada grafik "message rates last minute" muncul ketika cargo run dijalankan sebanyak 2 kali pada publisher. Spike ini merepresentasikan pengiriman pesan (publish rate 1.5/s) ke RabbitMQ. Meskipun terdapat 2 antrean dan 1 konsumen, tidak ada pesan yang tertahan (queued messages = 0), menandakan pesan langsung diproses. Lonjakan pada grafik secara langsung berkorelasi dengan aktivitas publisher yang mengirim pesan ke broker. Begitu publisher dijalankan, grafik menunjukkan spike, yang membuktikan bahwa pengiriman pesan berhasil meski tidak ada pesan yang tertinggal dalam sistem