<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pengingat Nomor 28 Hari</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; font-family: 'Inter', sans-serif; }
    body { margin: 0; background: linear-gradient(135deg, #4facfe, #00f2fe); }
    .container { max-width: 500px; margin: auto; padding: 20px; }
    .card { background: white; padding: 15px; margin-top: 10px; border-radius: 16px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
    h2, h3 { text-align: center; color: white; }
    .box { background: white; padding: 15px; border-radius: 16px; margin-bottom: 15px; }
    input { width: 100%; padding: 10px; margin-top: 8px; border-radius: 10px; border: 1px solid #ddd; }
    button { width: 100%; padding: 10px; margin-top: 10px; border: none; border-radius: 10px; background: #4facfe; color: white; font-weight: bold; cursor: pointer; }
    button:hover { opacity: 0.9; }
    .expired { color: red; font-weight: bold; }
    .row { display: flex; gap: 5px; }
    .row button { flex: 1; }
  </style>
</head>
<body>
  <div class="container">
    <h2>📱 Pengingat 28 Hari</h2>

    <div class="box">
      <input type="text" id="nomor" placeholder="Masukkan nomor">
      <input type="date" id="tanggal">
      <button onclick="tambahData()">+ Tambah Data</button>
    </div>

    <div class="box">
      <h3>🔍 Cari Tanggal Keluar</h3>
      <input type="date" id="cariTanggal">
      <div class="row">
        <button onclick="cariData()">Cari</button>
        <button onclick="tampilkan()">Reset</button>
      </div>
    </div>

    <div id="list"></div>
  </div>

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
              Keluar: ${exp.toLocaleDateString()}
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
