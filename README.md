<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Message For You</title>
    <!-- Memuat Tailwind CSS untuk layout dasar -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Memuat font dari Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* Mengatur font dasar untuk seluruh halaman */
        body {
            font-family: 'Poppins', sans-serif;
            overflow: hidden; /* Mencegah scroll bar karena animasi */
        }

        /* Menggunakan font Pacifico yang lebih imut untuk judul */
        .handwriting {
            font-family: 'Pacifico', cursive;
        }

        /* --- KEYFRAMES UNTUK ANIMASI --- */
        @keyframes fadeInPop { 0% { opacity: 0; transform: scale(0.8); } 100% { opacity: 1; transform: scale(1); } }
        @keyframes fadeOut { from { opacity: 1; } to { opacity: 0; } }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes beatHeart { 0%, 100% { transform: scale(1); } 25%, 75% { transform: scale(1.1); } 50% { transform: scale(1); } }
        @keyframes floatUp { 0% { transform: translateY(0); opacity: 1; } 100% { transform: translateY(-100vh); opacity: 0; } }

        /* --- KELAS UNTUK MENERAPKAN ANIMASI --- */
        .card-enter { animation: fadeInPop 0.8s ease-out forwards; }
        .heart-beat { animation: beatHeart 1.5s infinite ease-in-out; }
        .text-fade-out { animation: fadeOut 0.6s ease-out forwards; }
        .text-fade-in { animation: fadeIn 0.8s ease-in forwards; }

        /* Kontainer untuk hati yang melayang */
        .floating-hearts { position: absolute; width: 100%; height: 100%; top: 0; left: 0; z-index: 0; overflow: hidden; }
        .floating-hearts .heart { position: absolute; bottom: -50px; font-size: 24px; color: #ff8fab; animation: floatUp 10s infinite linear; }
        .floating-hearts .heart:nth-child(1) { left: 10%; animation-duration: 12s; }
        .floating-hearts .heart:nth-child(2) { left: 20%; animation-duration: 8s; animation-delay: 1s; font-size: 16px; }
        .floating-hearts .heart:nth-child(3) { left: 35%; animation-duration: 15s; animation-delay: 3s; }
        .floating-hearts .heart:nth-child(4) { left: 50%; animation-duration: 9s; animation-delay: 0.5s; font-size: 20px; }
        .floating-hearts .heart:nth-child(5) { left: 65%; animation-duration: 13s; animation-delay: 2s; }
        .floating-hearts .heart:nth-child(6) { left: 80%; animation-duration: 7s; animation-delay: 4s; font-size: 18px; }
        .floating-hearts .heart:nth-child(7) { left: 90%; animation-duration: 11s; animation-delay: 1.5s; }
    </style>
</head>
<body class="bg-pink-100 transition-colors duration-1000">

    <!-- Latar belakang dengan hati-hati yang melayang -->
    <div class="floating-hearts">
        <div class="heart">♡</div><div class="heart">♥</div><div class="heart">♡</div><div class="heart">♥</div><div class="heart">♡</div><div class="heart">♥</div><div class="heart">♡</div>
    </div>

    <!-- Kontainer utama untuk menengahkan kartu -->
    <div class="min-h-screen flex items-center justify-center p-4 relative z-10">
        <div class="card-enter bg-white rounded-2xl shadow-xl p-8 sm:p-12 text-center max-w-md w-full transform">
            <!-- Ikon hati di atas, kita berikan ID agar bisa dihilangkan -->
            <div id="heart-icon" class="heart-beat text-red-500 text-5xl mb-4">♥</div>
            
            <!-- Judul utama yang akan berubah -->
            <h1 id="main-text" class="handwriting text-5xl sm:text-6xl font-bold text-pink-500 mb-4 transition-colors duration-1000">Miss U</h1>
            
            <!-- Pesan tambahan yang akan berubah -->
            <p id="sub-text" class="text-lg text-gray-500">Lagi mikirin kamu...</p>
        </div>
    </div>

    <script>
        window.onload = function() {
            // Ambil semua elemen yang akan kita ubah
            const mainText = document.getElementById('main-text');
            const subText = document.getElementById('sub-text');
            const heartIcon = document.getElementById('heart-icon');
            const body = document.body;

            // --- BABAK 1: Transisi ke "Good Night" ---
            setTimeout(() => {
                mainText.classList.add('text-fade-out');
                subText.classList.add('text-fade-out');
                body.classList.remove('bg-pink-100');
                body.classList.add('bg-indigo-200');

                setTimeout(() => {
                    mainText.innerText = 'Good Night';
                    subText.innerText = 'Mimpi Indah';
                    mainText.classList.remove('text-pink-500');
                    mainText.classList.add('text-indigo-600');
                    mainText.classList.remove('text-fade-out');
                    subText.classList.remove('text-fade-out');
                    mainText.classList.add('text-fade-in');
                    subText.classList.add('text-fade-in');

                    // --- BABAK 2: Transisi ke Pesan Terakhir (Plot Twist) ---
                    setTimeout(() => {
                        mainText.classList.add('text-fade-out');
                        subText.classList.add('text-fade-out');
                        heartIcon.classList.add('text-fade-out'); // Hati juga ikut menghilang

                        body.classList.remove('bg-indigo-200');
                        body.classList.add('bg-gray-200'); // Ganti suasana jadi lebih datar

                        setTimeout(() => {
                            // Hilangkan ikon hati selamanya
                            heartIcon.style.display = 'none';

                            // Ubah teks & gaya font jadi lebih tegas (bukan tulisan tangan lagi)
                            mainText.classList.remove('handwriting');
                            mainText.classList.remove('text-indigo-600');
                            mainText.classList.add('text-gray-800', 'font-bold');
                            mainText.innerText = 'Jangan Skrol Mulu';

                            subText.innerText = 'Jomblo!';
                            subText.classList.add('font-semibold');
                            
                            // Tampilkan pesan terakhir dengan fade in
                            mainText.classList.remove('text-fade-out');
                            subText.classList.remove('text-fade-out');
                            mainText.classList.add('text-fade-in');
                            subText.classList.add('text-fade-in');

                        }, 600); // Waktu untuk animasi fade-out selesai

                    }, 4000); // Tunggu 4 detik setelah "Good Night" muncul

                }, 600); // Waktu untuk animasi fade-out selesai

            }, 4000); // Tunggu 4 detik setelah "Miss U" muncul
        };
    </script>
</body>
</html>
