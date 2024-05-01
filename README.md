### Reflection
1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable? <br>
- pada unary RPC, client mengirimkan sebuah request ke server dan menunggu sebuah response. Unary RPC cocok skenario dimana client perlu mengirimkankan sebuah data dan membutuhkan sebuah response juga seperti fetch data user, melakukan kalkulasi dan lainnya.
- pada server streaming RPC, client mengirimkan sebuah request ke server dan server memberikan response dengan 1 stream data. Server streaming RPC cocok utuk skenario dimana server perlu memberikan response banyak data untuk sebuah request dari client. Contohnya seperti fetch list item, retrieve data real-time.
- pada bi-directional RPC, client dan server mengirimkan stream data secara asinkronus. Cocok untuk skenario dimana diperlukan komunikasi terus menerus antara client dan server. Contohnya aplikasi chat, real-time collaboration tool.
2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption? <br>
- authentication : gunakan SSL/TLS karena menyediakan enkripsi dan autentikasi mutual antara client dan server.
- authorization : menentukan role dan permission untuk user atau client
- data encryption : enkripsi data sensitif yang dikirim di antara client dan server
3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications? <br>
Isu yang dapat muncul ketika membuat bi-directional grpc adalah concurrency. Selain itu, session management juga harus diperhatikan untuk menghandle seperti koneksi terputus dan session timeout.
4. What are the advantages and disadvantages of using the `tokio_stream::wrappers::ReceiverStream` for streaming responses in Rust gRPC services? <br>
- keuntungan yang didapatkan adalah antara lain proses data asinkronus sehingga lebih cepat, integrasi dengan tokio.
- kerugiannya adalah kompleksitas program asinkronus, kemungkinan isu compatibility tokio.
5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time? <br>
untuk memfasilitasi code reuse and modularity, promoting maintainability dan extensibility, kode Rust gRPC dapat melakukan beberapa best practice atau design pattern. 
6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic? <br>
dapat menggunakan tipe streaming yang lain yaitu server streaming agar pengiriman data kompleks dapat dilakukan dengan lebih cepat.
7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms? <br>
penggunaan gRPC sebagai communication protocol mendukung architecture microservice, standarisasi service interface dimana gRPC bergantung pada protocol buffers untuk membentuk service contract dan message format
8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs? <br>
- keuntungannya adalah HTTP/2 mendukung multiplexing, header compression, dan server push.
- kerugiannya adalah lebih kompleks dari HTTP/1.1, menggunakan memori dan processing power yang lebih banyak, dan beberapa browser belum mendukung HTTP/2
9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness? <br>
REST API clien melakukan request lalu menunggu hingga server mengirimkan response. gRPC bidirectional streaming dapat mendukung petukaran data secara bersamaan antara client dan server, sehingga mendukung komunikasi real-time lebih baik.
10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads? <br>
pendekatan schema-based gRPC menggunakan protocol buffers memiliki serialisasi yang efisien, strictness pada message format sehingga data yang dikirim/terkirim terjamin. pada REST API, ada fleksibilitas pada tipe data sehingga memungkinkan untuk mengirimkan data yang tidak sesuai.