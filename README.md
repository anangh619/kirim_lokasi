# kirim_lokasi

<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Kirim Lokasi via WhatsApp</title>
</head>
<body style="font-family:sans-serif;text-align:center;margin-top:50px;">
  <h2>Kirim Lokasi Saya via WhatsApp</h2>
  <button onclick="kirimLokasi()">Kirim Lokasi</button>

  <script>
    function kirimLokasi() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(success, error);
      } else {
        alert("Browser kamu tidak mendukung geolokasi.");
      }
    }

    function success(position) {
      const latitude = position.coords.latitude;
      const longitude = position.coords.longitude;
      const googleMapsLink = `https://www.google.com/maps?q=${latitude},${longitude}`;

      const pesan = encodeURIComponent(
        `Halo, ini lokasi saya: ${googleMapsLink}`
      );

      // Ganti nomor di bawah dengan nomor tujuan (format internasional tanpa +)
      const nomor = "6281234567890";

      const waLink = `https://wa.me/${nomor}?text=${pesan}`;
      window.open(waLink, "_blank");
    }

    function error() {
      alert("Tidak bisa mendapatkan lokasi. Pastikan izin lokasi aktif.");
    }
  </script>
</body>
</html>
