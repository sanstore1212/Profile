<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Pengingat Nomor 28 Hari</title>
  <style>
    body { font-family: Arial; padding: 20px; background: #f5f5f5; }
    h2 { text-align: center; }
    input, button { padding: 8px; margin: 5px; }
    .card { background: white; padding: 10px; margin-top: 10px; border-radius: 8px; }
    .expired { color: red; font-weight: bold; }
  </style>
</head>
<body>
  <h2>📱 Pengingat Nomor 28 Hari</h2>

  <input type="text" id="nomor" placeholder="Masukkan nomor">
  <input type="date" id="tanggal">
  <button onclick="tambahData()">Tambah</button>

  <hr>

  <h3>🔍 Cari berdasarkan tanggal keluar</h3>
  <input type="date" id="cariTanggal">
  <button onclick="cariData()">Cari</button>
  <button onclick="tampilkan()">Reset</button>

  <div id="list"></div>

  <script>
    let data = JSON.parse(localStorage.getItem('nomor28')) || [];

    function tambahData() {
      const nomor = document.getElementById('nomor').value;
      const tanggal = document.getElementById('tanggal').value;

      if (!nomor || !tanggal) {
        alert('Isi semua data!');
        return;
      }

      const startDate = new Date(tanggal);
      const expiredDate = new Date(startDate);
      expiredDate.setDate(expiredDate.getDate() + 28);

      data.push({ nomor, tanggal, expired: expiredDate });
      localStorage.setItem('nomor28', JSON.stringify(data));

      tampilkan();
    }

    function tampilkan(filterTanggal = null) {
      const list = document.getElementById('list');
      list.innerHTML = '';

      const today = new Date();

      data.forEach((item, index) => {
        const exp = new Date(item.expired);
        const isExpired = today >= exp;

        const expDateStr = exp.toISOString().split('T')[0];

        if (filterTanggal && expDateStr !== filterTanggal) return;

        list.innerHTML += `
          <div class="card">
            <div><b>${item.nomor}</b></div>
            <div>Mulai: ${item.tanggal}</div>
            <div class="${isExpired ? 'expired' : ''}">
              Harus keluar: ${exp.toLocaleDateString()}
            </div>
            <button onclick="hapus(${index})">Hapus</button>
          </div>
        `;
      });
    }

    function cariData() {
      const tanggal = document.getElementById('cariTanggal').value;
      if (!tanggal) {
        alert('Pilih tanggal dulu!');
        return;
      }
      tampilkan(tanggal);
    }

    function hapus(index) {
      data.splice(index, 1);
      localStorage.setItem('nomor28', JSON.stringify(data));
      tampilkan();
    }

    tampilkan();
  </script>
</body>
</html>
