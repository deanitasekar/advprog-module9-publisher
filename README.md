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