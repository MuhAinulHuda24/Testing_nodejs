# Laporan CRUD server.js

Implementasi dilakukan dalam satu file JavaScript bernama server.js, yang sudah mencakup CRUD untuk /movies (dari sesi praktikum sebelumnya) dan ditambahkan CRUD untuk /directors. Setiap objek sutradara memiliki atribut id, name, dan birthYear. Saya menggunakan basis data in-memory (array) untuk menyimpan data, middleware seperti express.json() untuk parsing body request, dan penanganan error seperti 404 Not Found secara konsisten.
## implementasi Kriteria Fungsionalitas pada Bab 3.3:

## GET /directors:
Endpoint ini mengembalikan daftar semua sutradara dalam format JSON. Jika tidak ada data, endpoint mengembalikan array kosong.
Contoh respons: [{ "id": 1, "name": "Bong Joon-ho", "birthYear": 1969 }, ...].
GET /directors/:id:
Endpoint ini mengembalikan detail satu sutradara berdasarkan ID. Jika ID tidak ditemukan, endpoint mengembalikan respons 404 dengan pesan error JSON seperti { "error": "Sutradara tidak ditemukan" }.
dok.

<img width="1919" height="1003" alt="image" src="https://github.com/user-attachments/assets/a26fc4cc-77f8-43d9-9003-7ba40d3b50a3" />

dok.get by id
<img width="1919" height="1006" alt="image" src="https://github.com/user-attachments/assets/893b3034-93ab-486f-85aa-f233491c8c6a" />


## POST /directors:
Endpoint ini digunakan untuk membuat sutradara baru. Validasi dilakukan untuk memastikan name dan birthYear disertakan dalam body request. Jika data tidak lengkap, endpoint mengembalikan 400 Bad Request dengan pesan error seperti { "error": "name dan birthYear wajib diisi" }. ID baru di-generate secara otomatis menggunakan variabel sekuens. Respons sukses adalah 201 Created dengan data sutradara baru.
*dok sebelum post.
<img width="1919" height="1006" alt="image" src="https://github.com/user-attachments/assets/7a12b1a4-e0fe-45f7-a7c9-ce7fbccf45ec" />
* melakukan post
<img width="1919" height="1003" alt="image" src="https://github.com/user-attachments/assets/e683cd12-0681-40ba-81b5-7cc6b7cbb190" />
*hasil
<img width="1919" height="1004" alt="image" src="https://github.com/user-attachments/assets/32041627-ec04-48b9-84e0-feda3554a5cc" />

## PUT /directors/:id:
Endpoint ini memperbarui data sutradara berdasarkan ID. Body request dapat mencakup name dan/atau birthYear. Jika ID tidak ditemukan, endpoint mengembalikan 404 dengan pesan error. Respons sukses adalah data sutradara yang telah diperbarui.
*sebelum diubah
<img width="1919" height="1003" alt="image" src="https://github.com/user-attachments/assets/6be231d6-1fe1-4b3d-94b9-898dfa96c3bb" />

*proses PUT
<img width="1919" height="1004" alt="image" src="https://github.com/user-attachments/assets/7b88535e-dee4-495f-9df7-0505991e3774" />

*sesudah PUT
<img width="1919" height="1007" alt="image" src="https://github.com/user-attachments/assets/b6acaac2-6237-49ee-98bc-9698388d8016" />


## DELETE /directors/:id:
Endpoint ini menghapus data sutradara berdasarkan ID. Jika ID tidak ditemukan, endpoint mengembalikan 404 dengan pesan error. Respons sukses adalah 204 No Content tanpa body.
* sebelum delete
<img width="1919" height="1002" alt="image" src="https://github.com/user-attachments/assets/0ebaa36d-3703-4d0b-8634-90417ff96329" />
* proses delete
<img width="1919" height="1002" alt="image" src="https://github.com/user-attachments/assets/70082d3f-16ef-446f-a84d-5dfafe8522c8" />
* setelah delete
<img width="1919" height="1009" alt="image" src="https://github.com/user-attachments/assets/c6b0fa8b-8ffc-4563-98f0-b7395e069bb6" />

## Penanganan Kasus 404 Not Found:
Semua endpoint yang melibatkan ID (GET, PUT, DELETE) telah diimplementasikan dengan pengecekan keberadaan data. Selain itu, middleware fallback 404 telah ada dari sesi praktikum sebelumnya untuk menangani rute yang tidak ditemukan. Saya juga memastikan penggunaan kode status HTTP yang semantik (seperti 200 OK, 201 Created, 204 No Content, 400 Bad Request, 404 Not Found) dan middleware CORS untuk memungkinkan akses dari frontend. Server dijalankan pada port 3200, dan saya menggunakan Nodemon untuk pengembangan efisien agar server restart otomatis saat ada perubahan kode.

*dok. eror 404 karena id tidak dotemukan 
<img width="1919" height="1005" alt="image" src="https://github.com/user-attachments/assets/3acc82af-b8f7-4d56-b96b-e1db17ea1441" />

## Pengujian dilakukan secara sistematis menggunakan Postman untuk semua endpoint, baik untuk /movies maupun /directors. Saya telah membuat koleksi Postman yang mencakup:

Request GET untuk daftar dan detail (dengan variasi ID valid dan invalid).
Request POST dengan body JSON valid dan invalid (untuk uji validasi).
Request PUT dengan update parsial dan lengkap.
Request DELETE dengan ID valid dan invalid.

## Kesimpulan
Tugas ini telah selesai sepenuhnya dan sesuai dengan tujuan pembelajaran pada Modul 2, yaitu membangun API RESTful yang fungsional dan dapat diuji. Implementasi memperkuat pemahaman saya tentang arsitektur Node.js, Express.js, dan prinsip desain API RESTful. Tidak ada isu yang ditemukan selama pengujian, dan API siap untuk diintegrasikan dengan aplikasi lain.
