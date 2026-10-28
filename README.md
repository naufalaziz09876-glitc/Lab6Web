# Lab6Web
1. Tujuan

Praktikum ini bertujuan agar saya mampu:
- Memahami DOM sebagai representasi dokumen HTML yang dapat diakses melalui JavaScript.
- Memilih elemen dengan id, class, dan selector CSS.
- Mengubah teks, atribut, kelas CSS, dan gaya elemen melalui JavaScript.
- Menangani event pengguna menggunakan addEventListener().
- Membuat validasi form dan menampilkan pesan sesuai kondisi input

2. Struktur File

- index.html berfungsi sebagai struktur halaman
- style.css berfungsi sebagai Tampilan halaman
- script.js berfungsi sebagai Logika Java script

3.  Menghubungkan CSS dan JavaScript

Pada tahap persiapan, index.html dibuat dengan template dari modul. File CSS dihubungkan dengan <link> dan file JavaScript dengan <script>. Atribut defer membuat JavaScript dijalankan setelah HTML selesai diparsing, sehingga elemen yang dipilih sudah tersedia.

```Html
<!DOCTYPE html>
<html lang="id">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Praktikum DOM dan Event</title>
 <link rel="stylesheet" href="style.css">
 <script src="script.js" defer></script>
</head>
<body>
 <h1 id="judul">Latihan DOM</h1>
 <p id="pesan">Belum ada tindakan.</p>
 <button id="tombolAksi" type="button">Klik Saya</button>
</body>
</html>
```

4. Pemeriksaan koneksi

Sebelum latihan dimulai, script.js diisi sementara dengan console.log untuk memastikan file terhubung dan elemen dapat dipilih. Halaman dibuka di browser dengan Developer Tools aktif.
```Javascript
console.log("script.js berhasil dimuat.");
console.log("Elemen #judul:", document.getElementById("judul"));
console.log("Elemen #pesan:", document.getElementById("pesan"));
console.log("Elemen #tombolAksi:", document.getElementById("tombolAksi"));
 ```
<img width="688" height="320" alt="image" src="https://github.com/user-attachments/assets/4e5e71d4-ad12-4352-b8c8-e0e7eb7ee098" />

Console menampilkan keempat pesan tersebut tanpa error, sehingga lingkungan kerja siap digunakan. Kode pemeriksaan ini kemudian diganti dengan kode Latihan 1–6 pada script.js.

5. Langkah Kerja Praktikum

Seluruh latihan digabung dalam satu halaman (index.html) dengan satu file script.js dan satu file style.css. Setiap latihan berada pada elemen section tersendiri agar mudah diuji. Pengujian dilakukan di browser Chromium, dan Console tidak menampilkan error selama pengujian.

- Latihan 1: Mengubah Teks dengan DOM

Elemen dipilih berdasarkan id, lalu isi teksnya diubah dengan properti textContent.
```Javascript
const judul = document.getElementById("judul");
const pesan = document.getElementById("pesan");
judul.textContent = "Belajar JavaScript DOM";
pesan.textContent = "Konten berhasil diubah oleh JavaScript.";
 ```
<img width="688" height="200" alt="image" src="https://github.com/user-attachments/assets/30893af9-7817-42e7-8ec0-f0e13f333ed8" />

Hasil: judul berubah dari "Latihan DOM" menjadi "Belajar JavaScript DOM", dan paragraf berubah dari "Belum ada tindakan." menjadi "Konten berhasil diubah oleh JavaScript.". Jika kalimat pada baris pesan.textContent diganti, paragraf akan menampilkan kalimat yang baru setelah halaman dimuat ulang. textContent menampilkan isi sebagai teks biasa.

- Latihan 2: Event Click

Tombol diberi event listener untuk event click. Setiap kali diklik, paragraf menampilkan waktu saat tombol ditekan.
```JavaScript
const tombol = document.getElementById("tombolAksi");
tombol.addEventListener("click", function () {
  pesan.textContent = "Tombol diklik pada " + new Date().toLocaleTimeString();
});
 ```
<img width="688" height="200" alt="image" src="https://github.com/user-attachments/assets/ed76ab51-622f-491d-a11b-1a1e2aa2da74" />

Hasil: tombol ditekan dua kali dengan jeda sekitar satu detik, dan pesan diperbarui pada setiap klik dengan waktu terbaru. Ini menunjukkan fungsi pada addEventListener() dijalankan setiap kali event click terjadi.

- Latihan 3: Mengubah Kelas dan Gaya CSS

Dua kelas CSS ditambahkan pada style.css, lalu dikontrol dari JavaScript dengan classList.toggle().
```Css
.highlight {
  color: #173f75;
  background-color: #e6f1ff;
  border-left: 4px solid #3478c8;
  padding: 12px;
}
.teks-besar { font-size: 1.4rem; }

const tombolGaya = document.getElementById("tombolGaya");
const teksGaya = document.getElementById("teksGaya");
tombolGaya.addEventListener("click", function () {
  teksGaya.classList.toggle("highlight");
  teksGaya.classList.toggle("teks-besar");
});
 ```
<img width="688" height="172" alt="image" src="https://github.com/user-attachments/assets/bbfb0f87-97ed-4524-a65e-e368c1383ae4" />

<img width="688" height="216" alt="image" src="https://github.com/user-attachments/assets/665ab384-33a0-4686-aea1-a6672c1c69f3" />

Hasil: pada klik pertama, atribut class paragraf menjadi "highlight teks-besar". Pada klik kedua, kedua kelas dilepas dan tampilan kembali seperti semula.

Perbedaan ketiga metode classList:

Metode	Perilaku

classList.add()	 berfungsiMenambahkan kelas. Jika kelas sudah ada, tidak terjadi duplikasi.
classList.remove()	berfungsi Menghapus kelas dari elemen.
classList.toggle()	berfungsi Menambahkan kelas jika belum ada, dan menghapusnya jika sudah ada.

- Latihan 4: Event Input dan Penghitung Karakter

Event input dijalankan setiap kali isi kolom berubah, sehingga jumlah karakter diperbarui secara langsung.
```JavaScript
const namaInput = document.getElementById("namaInput");
const jumlahKarakter = document.getElementById("jumlahKarakter");
namaInput.addEventListener("input", function () {
  jumlahKarakter.textContent = namaInput.value.length;
});
 ```
<img width="688" height="198" alt="image" src="https://github.com/user-attachments/assets/18f24c41-0dde-4425-95e0-12e4639d7542" />

 
<img width="688" height="198" alt="image" src="https://github.com/user-attachments/assets/359e8826-cde2-4d20-bf74-2ec37ea1c49e" />

Pengujian	Hasil di layar	Keterangan
Mengetik "Budi Santoso"	12	Sesuai jumlah karakter.
Menghapus 4 karakter	8	Angka berkurang.
Menempelkan teks panjang	40	Dibatasi maxlength="40".

- Latihan 5: Validasi Form Pendaftaran

Form dibuat dengan atribut novalidate agar validasi dilakukan oleh JavaScript. Pada event submit, event.preventDefault() mencegah halaman dimuat ulang sebelum pemeriksaan selesai.
```Javascript
const form = document.getElementById("formPendaftaran");
const pesanForm = document.getElementById("pesanForm");
form.addEventListener("submit", function (event) {
  event.preventDefault();
  const nama = document.getElementById("nama").value.trim();
  const email = document.getElementById("email").value.trim();
  const usiaInput = document.getElementById("usia").value;
  const usia = Number(usiaInput);
  const polaEmail = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (nama === "") {
    pesanForm.textContent = "Nama wajib diisi.";
  } else if (!polaEmail.test(email)) {
    pesanForm.textContent = "Masukkan email yang valid.";
  } else if (usiaInput === "" || !Number.isInteger(usia) || usia < 17 || usia > 100) {
    pesanForm.textContent = "Usia harus berupa bilangan bulat 17–100.";
  } else {
    pesanForm.textContent = "Validasi berhasil. Form siap diproses.";
    form.reset();
  }
});
```
Pengujian dilakukan pada lima kondisi, dan hasilnya sesuai dengan yang diharapkan.
 
<img width="453" height="245" alt="image" src="https://github.com/user-attachments/assets/5945f8a5-ec77-444a-a471-99edc9fe0964" />

<img width="453" height="245" alt="image" src="https://github.com/user-attachments/assets/b6ed1d65-c80b-4817-ba0b-8d2f05755b2c" />
 
<img width="453" height="245" alt="image" src="https://github.com/user-attachments/assets/b071a7ae-2f5c-4269-bc72-ff086eba911d" />
	 
<img width="453" height="245" alt="image" src="https://github.com/user-attachments/assets/eea066c9-047c-43f1-99a1-3af020eed8ec" />
 
<img width="453" height="245" alt="image" src="https://github.com/user-attachments/assets/63b04ada-141a-4fd4-8041-9bf613921ecd" />

Pada kondisi 5, form.reset() mengosongkan seluruh kolom setelah validasi berhasil. Pemeriksaan dilakukan berurutan (nama, email, usia), sehingga hanya satu pesan kesalahan yang tampil pada satu waktu.

- Latihan 6: Daftar Tugas Sederhana (To-do List)

Aplikasi ini membuat elemen li secara dinamis dengan document.createElement(), lalu menambahkannya ke daftar. Teks pengguna dimasukkan dengan textContent sehingga ditampilkan sebagai teks, bukan markup HTML.
```Javascript
const inputTugas = document.getElementById("inputTugas");
const tambahTugas = document.getElementById("tambahTugas");
const daftarTugas = document.getElementById("daftarTugas");
const pesanTugas = document.getElementById("pesanTugas");
tambahTugas.addEventListener("click", function () {
  const teks = inputTugas.value.trim();
  if (teks === "") {
    pesanTugas.textContent = "Tulis tugas terlebih dahulu.";
    return;
  }
  const item = document.createElement("li");
  const label = document.createElement("span");
  const selesai = document.createElement("button");
  label.textContent = teks + " ";
  selesai.type = "button";
  selesai.textContent = "Tandai selesai";
  selesai.addEventListener("click", function () {
    item.classList.toggle("selesai");
    selesai.textContent = item.classList.contains("selesai")
      ? "Batalkan selesai" : "Tandai selesai";
  });
  item.append(label, selesai);
  daftarTugas.appendChild(item);
  inputTugas.value = "";
  pesanTugas.textContent = "Tugas ditambahkan.";
  inputTugas.focus();
});
```
```Css
.selesai span { text-decoration: line-through; color: #687386; }
li { margin-bottom: 8px; }
```
 
<img width="688" height="211" alt="image" src="https://github.com/user-attachments/assets/c2bcc5a6-b5dc-485d-b03e-833887fa3837" />

<img width="688" height="380" alt="image" src="https://github.com/user-attachments/assets/3adf75cc-f4e6-4119-9c33-f757d63afb07" />

<img width="688" height="380" alt="image" src="https://github.com/user-attachments/assets/2c9c2d35-60eb-4e60-83b2-d1639b07fc98" />

Hasil: saat input kosong, muncul pesan "Tulis tugas terlebih dahulu.". Setelah tiga tugas ditambahkan, pesan berubah menjadi "Tugas ditambahkan." dan daftar berisi tiga item. Saat tombol "Tandai selesai" ditekan, teks tugas tercoret dan tombol berubah menjadi "Batalkan selesai".
