<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pengingat 28 Hari</title>

  <style>
    body {
      font-family: Arial;
      margin: 0;
      background: linear-gradient(135deg, #4facfe, #00f2fe);
    }

    .container {
      max-width: 400px;
      margin: auto;
      padding: 20px;
    }

    h2 {
      text-align: center;
      color: white;
    }

    .box {
      background: white;
      padding: 15px;
      border-radius: 12px;
      margin-bottom: 10px;
    }

    input {
      width: 100%;
      padding: 10px;
      margin-top: 8px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }

    button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border: none;
      border-radius: 8px;
      background: #4facfe;
      color: white;
      font-weight: bold;
    }

    .card {
      background: white;
      padding: 10px;
      border-radius: 10px;
      margin-top: 10px;
    }

    .expired {
      color: red;
      font-weight: bold;
    }
  </style>
</head>

<body>

<div class="container">
  <h2>📱 Pengingat 28 Hari</h2>

  <div class="box">
    <input type="text" id="nomor" placeholder="Masukkan nomor">
    <input type="date" id="tanggal">
    <button onclick="tambah()">+ Tambah</button>
  </div>

  <div class="box">
    <input type="date" id="cari">
    <button onclick="cari()">Cari Tanggal Keluar</button>
    <button onclick="tampil()">Reset</button>
  </div>

  <div id="list"></div>
</div>

<script>
let data = JSON.parse(localStorage.getItem("data28")) || [];

function tambah() {
  let nomor = document.getElementById("nomor").value;
  let tanggal = document.getElementById("tanggal").value;

  if (!nomor || !tanggal) {
    alert("Isi semua!");
    return;
  }

  let tgl = new Date(tanggal);
  let keluar = new Date(tgl);
  keluar.setDate(keluar.getDate() + 28);

  data.push({ nomor, tanggal, keluar });
  localStorage.setItem("data28", JSON.stringify(data));

  tampil();
}

function tampil(filter = null) {
  let list = document.getElementById("list");
  list.innerHTML = "";

  let today = new Date();

  data.forEach((d, i) => {
    let keluar = new Date(d.keluar);
    let tglStr = keluar.toISOString().split("T")[0];

    if (filter && tglStr !== filter) return;

    let expired = today >= keluar;

    list.innerHTML += `
      <div class="card">
        <b>${d.nomor}</b><br>
        Mulai: ${d.tanggal}<br>
        <span class="${expired ? 'expired' : ''}">
          Keluar: ${keluar.toLocaleDateString()}
        </span><br>
        <button onclick="hapus(${i})">Hapus</button>
      </div>
    `;
  });
}

function cari() {
  let tgl = document.getElementById("cari").value;
  tampil(tgl);
}

function hapus(i) {
  data.splice(i, 1);
  localStorage.setItem("data28", JSON.stringify(data));
  tampil();
}

tampil();
</script>

</body>
</html>      data.splice(index, 1);
      localStorage.setItem('nomor28', JSON.stringify(data));
      tampilkan();
    }

    tampilkan();
  </script>
</body>
</html>
