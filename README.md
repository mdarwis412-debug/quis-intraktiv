<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Interaktif MTs DDI Kelurahan Baru</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- Canvas Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Poppins', 'sans-serif'],
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-slate-950 text-slate-100 font-sans min-h-screen flex flex-col justify-between selection:bg-indigo-500 selection:text-white">

    <!-- Header Navigation -->
    <header class="bg-slate-900/90 backdrop-blur-md border-b border-slate-800 py-3.5 px-4 sticky top-0 z-50 shadow-md">
        <div class="max-w-4xl mx-auto flex justify-between items-center">
            <div class="flex items-center space-x-3 cursor-pointer" onclick="showScreen('welcomeScreen')">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-indigo-500 to-purple-600 flex items-center justify-center text-white font-extrabold text-xl shadow-lg shadow-indigo-500/20">
                    <i class="fa-solid fa-graduation-cap"></i>
                </div>
                <div>
                    <h1 class="font-extrabold text-base text-white leading-tight tracking-wide">MTs DDI KELURAHAN BARU</h1>
                    <p class="text-xs text-indigo-400 font-medium">Quiz Interaktif AI & Teknologi</p>
                </div>
            </div>
            
            <div id="navUserBadge" class="hidden flex items-center space-x-3">
                <span id="userInfoLabel" class="text-xs font-semibold bg-slate-800 border border-slate-700 px-3 py-1.5 rounded-xl text-slate-300">
                    <i class="fa-solid fa-user text-indigo-400 mr-1.5"></i> <span id="currentRoleText">Peserta</span>
                </span>
                <button onclick="logout()" class="text-xs font-semibold px-3 py-1.5 bg-rose-500/10 hover:bg-rose-500/20 text-rose-400 border border-rose-500/30 rounded-xl transition cursor-pointer">
                    <i class="fa-solid fa-right-from-bracket mr-1"></i> Keluar
                </button>
            </div>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="max-w-4xl w-full mx-auto px-4 py-8 flex-1 flex flex-col justify-center">

        <!-- 1. DASHBOARD AWAL / WELCOME SCREEN -->
        <section id="welcomeScreen" class="bg-slate-900 border border-slate-800 rounded-3xl p-6 sm:p-10 text-center shadow-2xl relative overflow-hidden backdrop-blur-xl">
            <div class="absolute -top-16 -right-16 w-40 h-40 bg-indigo-500/10 rounded-full blur-3xl"></div>
            <div class="absolute -bottom-16 -left-16 w-40 h-40 bg-purple-500/10 rounded-full blur-3xl"></div>
            
            <div class="w-20 h-20 bg-gradient-to-tr from-indigo-500/20 to-purple-500/20 border border-indigo-500/40 rounded-2xl mx-auto flex items-center justify-center text-indigo-400 mb-5 shadow-inner">
                <i class="fa-solid fa-laptop-code text-4xl"></i>
            </div>
            
            <span class="inline-block px-3.5 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/30 text-indigo-400 text-xs font-bold uppercase tracking-wider mb-3">
                Portal Resmi Pembelajaran
            </span>
            
            <h2 class="text-2xl sm:text-4xl font-black text-white mb-3 tracking-tight">
                Selamat Datang di Quiz Interaktif<br>
                <span class="bg-gradient-to-r from-indigo-400 via-purple-400 to-pink-400 bg-clip-text text-transparent">MTs DDI KELURAHAN BARU</span>
            </h2>
            <p class="text-xs sm:text-sm text-slate-400 max-w-lg mx-auto mb-8 leading-relaxed">
                Platform kuis interaktif untuk menguji pemahaman siswa tentang Kecerdasan Buatan (AI) & Teknologi Informasi. Pilih peran untuk masuk.
            </p>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 max-w-xl mx-auto">
                <button onclick="showScreen('studentLoginScreen')" class="p-5 bg-gradient-to-br from-slate-800/80 to-slate-900 hover:from-slate-800 hover:to-indigo-950/40 border border-slate-700/80 hover:border-indigo-500/60 rounded-2xl text-left transition-all group hover:scale-[1.02] cursor-pointer shadow-lg">
                    <div class="flex items-center space-x-4">
                        <div class="w-12 h-12 rounded-xl bg-indigo-500/20 text-indigo-400 border border-indigo-500/30 flex items-center justify-center text-xl group-hover:bg-indigo-500 group-hover:text-white transition">
                            <i class="fa-solid fa-user-graduate"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-white text-base">Masuk Peserta (Siswa)</h3>
                            <p class="text-xs text-slate-400">Kerjakan kuis & uji wawasan kamu</p>
                        </div>
                    </div>
                </button>

                <button onclick="showScreen('adminLoginScreen')" class="p-5 bg-gradient-to-br from-slate-800/80 to-slate-900 hover:from-slate-800 hover:to-purple-950/40 border border-slate-700/80 hover:border-purple-500/60 rounded-2xl text-left transition-all group hover:scale-[1.02] cursor-pointer shadow-lg">
                    <div class="flex items-center space-x-4">
                        <div class="w-12 h-12 rounded-xl bg-purple-500/20 text-purple-400 border border-purple-500/30 flex items-center justify-center text-xl group-hover:bg-purple-500 group-hover:text-white transition">
                            <i class="fa-solid fa-user-gear"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-white text-base">Masuk Admin (Guru)</h3>
                            <p class="text-xs text-slate-400">Kelola soal kuis & rekap nilai</p>
                        </div>
                    </div>
                </button>
            </div>
        </section>

        <!-- 2. LOGIN PESERTA (SISWA) -->
        <section id="studentLoginScreen" class="hidden max-w-md mx-auto w-full bg-slate-900 border border-slate-800 rounded-3xl p-6 sm:p-8 shadow-2xl">
            <div class="text-center mb-6">
                <div class="w-14 h-14 bg-indigo-500/10 border border-indigo-500/30 rounded-2xl mx-auto flex items-center justify-center text-indigo-400 mb-3">
                    <i class="fa-solid fa-id-card text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold text-white">Identitas Peserta Kuis</h3>
                <p class="text-xs text-slate-400 mt-1">Isi identitas diri kamu dengan benar sebelum memulai</p>
            </div>

            <form onsubmit="handleStudentLogin(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1.5">Nama Lengkap Siswa</label>
                    <input type="text" id="studentName" required placeholder="Contoh: Ahmad Rizky" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-indigo-500 transition">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1.5">Kelas</label>
                    <input type="text" id="studentClass" required placeholder="Contoh: VII-A / VIII-B" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-indigo-500 transition">
                </div>

                <div class="pt-2 flex items-center space-x-3">
                    <button type="button" onclick="showScreen('welcomeScreen')" class="w-1/3 py-3 bg-slate-800 hover:bg-slate-700 text-slate-300 font-bold text-xs rounded-xl transition cursor-pointer">
                        <i class="fa-solid fa-arrow-left mr-1"></i> Kembali
                    </button>
                    <button type="submit" class="w-2/3 py-3 bg-gradient-to-r from-indigo-500 to-purple-600 hover:from-indigo-600 hover:to-purple-700 text-white font-extrabold text-xs rounded-xl shadow-lg shadow-indigo-500/25 transition cursor-pointer">
                        Mulai Kuis <i class="fa-solid fa-play ml-1"></i>
                    </button>
                </div>
            </form>
        </section>

        <!-- 3. LOGIN ADMIN (GURU) -->
        <section id="adminLoginScreen" class="hidden max-w-md mx-auto w-full bg-slate-900 border border-slate-800 rounded-3xl p-6 sm:p-8 shadow-2xl">
            <div class="text-center mb-6">
                <div class="w-14 h-14 bg-purple-500/10 border border-purple-500/30 rounded-2xl mx-auto flex items-center justify-center text-purple-400 mb-3">
                    <i class="fa-solid fa-lock text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold text-white">Login Admin Guru</h3>
                <p class="text-xs text-slate-400 mt-1">Masukkan kredensial admin untuk mengelola kuis</p>
            </div>

            <form onsubmit="handleAdminLogin(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1.5">Username</label>
                    <input type="text" id="adminUsername" required value="admin" placeholder="admin" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-purple-500 transition">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1.5">Password Angka</label>
                    <input type="password" id="adminPassword" required value="1234" placeholder="1234" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-purple-500 transition">
                </div>

                <div id="adminLoginAlert" class="hidden p-3 bg-rose-500/10 border border-rose-500/30 rounded-xl text-xs text-rose-400">
                    <i class="fa-solid fa-triangle-exclamation mr-1"></i> <span id="adminAlertText">Username atau Password salah!</span>
                </div>

                <div class="p-3 bg-slate-950 rounded-xl border border-slate-800 text-[11px] text-slate-400 flex justify-between items-center">
                    <span><i class="fa-solid fa-circle-info text-purple-400 mr-1"></i> Login: <strong class="text-white">admin</strong> / <strong class="text-white">1234</strong></span>
                    <button type="button" onclick="bypassAdminLogin()" class="text-[10px] text-purple-400 hover:text-purple-300 underline font-semibold cursor-pointer">
                        Buka Langsung &rarr;
                    </button>
                </div>

                <div class="pt-2 flex items-center space-x-3">
                    <button type="button" onclick="showScreen('welcomeScreen')" class="w-1/3 py-3 bg-slate-800 hover:bg-slate-700 text-slate-300 font-bold text-xs rounded-xl transition cursor-pointer">
                        <i class="fa-solid fa-arrow-left mr-1"></i> Kembali
                    </button>
                    <button type="submit" class="w-2/3 py-3 bg-gradient-to-r from-purple-600 to-indigo-600 hover:from-purple-700 hover:to-indigo-700 text-white font-extrabold text-xs rounded-xl shadow-lg shadow-purple-500/25 transition cursor-pointer">
                        Masuk Dashboard <i class="fa-solid fa-right-to-bracket ml-1"></i>
                    </button>
                </div>
            </form>
        </section>

        <!-- 4. QUIZ PLAY ENGINE (SISWA) -->
        <section id="quizPlayScreen" class="hidden space-y-4 max-w-2xl mx-auto w-full">
            
            <!-- Progress & Info Bar -->
            <div class="bg-slate-900 border border-slate-800 p-4 rounded-2xl shadow-md flex justify-between items-center text-xs font-bold">
                <div>
                    <span class="text-indigo-400">Soal Nomor <span id="currentNum">1</span> dari <span id="totalNum">5</span></span>
                    <p class="text-[10px] text-slate-500 font-normal">Nama: <span id="studentDisplayInfo" class="text-slate-300 font-semibold">-</span></p>
                </div>
                <div id="statusAnsweredBadge" class="px-3 py-1 bg-slate-950 rounded-xl border border-slate-800 text-slate-400 text-[11px]">
                    <i class="fa-solid fa-circle-notch mr-1 text-indigo-400"></i> <span id="answeredStatusText">Belum Menjawab</span>
                </div>
            </div>

            <!-- Question Card -->
            <div class="bg-slate-900 border border-slate-800 rounded-3xl p-6 sm:p-8 shadow-xl relative">
                <p id="questionText" class="text-base sm:text-lg font-bold text-white leading-relaxed mb-6">
                    [Loading Soal...]
                </p>

                <!-- Options List -->
                <div id="optionsContainer" class="space-y-3">
                    <!-- Dynamic Options -->
                </div>
            </div>

            <!-- Quiz Navigation Controls -->
            <div class="flex justify-between items-center pt-2">
                <button id="btnPrev" onclick="prevQuestion()" disabled class="px-5 py-3 bg-slate-800 text-slate-500 font-bold text-xs rounded-xl border border-slate-700 transition opacity-50 cursor-not-allowed">
                    <i class="fa-solid fa-arrow-left mr-1"></i> Soal Sebelumnya
                </button>

                <button id="btnNext" onclick="nextQuestion()" class="px-6 py-3 bg-gradient-to-r from-indigo-500 to-purple-600 hover:from-indigo-600 hover:to-purple-700 text-white font-extrabold text-xs rounded-xl shadow-lg transition-all cursor-pointer">
                    Soal Berikutnya <i class="fa-solid fa-arrow-right ml-1"></i>
                </button>
            </div>
        </section>

        <!-- 5. QUIZ RESULT SCREEN (SISWA) -->
        <section id="quizResultScreen" class="hidden space-y-6 max-w-2xl mx-auto w-full">
            <div class="bg-slate-900 border border-slate-800 rounded-3xl p-6 sm:p-10 text-center shadow-2xl relative overflow-hidden">
                <div id="resultBadgeIcon" class="w-20 h-20 rounded-2xl mx-auto flex items-center justify-center text-3xl mb-4 shadow-xl">
                    <!-- Icon populated dynamically -->
                </div>

                <h2 id="resultTitle" class="text-2xl sm:text-3xl font-extrabold text-white">Hasil Kuis Selesai!</h2>
                <p class="text-xs text-slate-400 mt-1 mb-6">Hasil pengerjaan kuis siswa MTs DDI Kelurahan Baru</p>

                <!-- Score Grid -->
                <div class="grid grid-cols-2 sm:grid-cols-4 gap-3 max-w-lg mx-auto mb-6">
                    <div class="bg-emerald-500/10 border border-emerald-500/30 p-3 rounded-2xl">
                        <p class="text-[10px] font-bold text-emerald-400 uppercase">Jawaban Benar</p>
                        <p id="correctCountText" class="text-2xl font-black text-emerald-400">0</p>
                    </div>
                    <div class="bg-rose-500/10 border border-rose-500/30 p-3 rounded-2xl">
                        <p class="text-[10px] font-bold text-rose-400 uppercase">Jawaban Salah</p>
                        <p id="wrongCountText" class="text-2xl font-black text-rose-400">0</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-2xl border border-slate-800">
                        <p class="text-[10px] font-bold text-slate-400 uppercase">Nilai Akhir</p>
                        <p id="finalScoreText" class="text-2xl font-black text-amber-400">0</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-2xl border border-slate-800">
                        <p class="text-[10px] font-bold text-slate-400 uppercase">Predikat</p>
                        <p id="predicateText" class="text-2xl font-black text-indigo-400">-</p>
                    </div>
                </div>

                <!-- Review Section -->
                <div class="text-left bg-slate-950 p-4 sm:p-6 rounded-2xl border border-slate-800 mb-6 space-y-4 max-h-80 overflow-y-auto">
                    <h4 class="font-bold text-xs text-indigo-400 uppercase tracking-wider mb-2">Evaluasi & Pembahasan Jawaban:</h4>
                    <div id="reviewContainer" class="space-y-4">
                        <!-- Dynamic Question Review -->
                    </div>
                </div>

                <div class="flex justify-center space-x-3">
                    <button onclick="showScreen('welcomeScreen')" class="px-6 py-3 bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-bold rounded-xl transition cursor-pointer">
                        <i class="fa-solid fa-house mr-1"></i> Kembali ke Beranda
                    </button>
                    <button onclick="restartQuiz()" class="px-8 py-3 bg-gradient-to-r from-indigo-500 to-purple-600 hover:from-indigo-600 hover:to-purple-700 text-white text-xs font-extrabold rounded-xl shadow-lg transition cursor-pointer">
                        <i class="fa-solid fa-rotate-right mr-1"></i> Ulangi Kuis
                    </button>
                </div>
            </div>
        </section>

        <!-- 6. ADMIN DASHBOARD (MANAJEMEN SOAL & REKAP) -->
        <section id="adminDashboardScreen" class="hidden space-y-6 max-w-4xl mx-auto w-full">
            
            <!-- Dashboard Header Bar -->
            <div class="bg-slate-900 border border-slate-800 p-6 rounded-3xl shadow-xl flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                <div>
                    <span class="text-xs font-bold text-purple-400 bg-purple-500/10 px-3 py-1 rounded-full border border-purple-500/30">
                        <i class="fa-solid fa-user-shield mr-1"></i> Panel Admin Guru
                    </span>
                    <h2 class="text-xl sm:text-2xl font-black text-white mt-1">Kelola Soal Kuis & Rekap Nilai</h2>
                </div>
                <div class="flex items-center space-x-2">
                    <button onclick="openAddQuestionModal()" class="px-4 py-2.5 bg-gradient-to-r from-emerald-500 to-teal-600 text-white font-bold text-xs rounded-xl shadow-md hover:scale-105 transition cursor-pointer">
                        <i class="fa-solid fa-plus mr-1"></i> Tambah Soal Baru
                    </button>
                </div>
            </div>

            <!-- Tab Navigation -->
            <div class="flex border-b border-slate-800 space-x-4">
                <button onclick="switchAdminTab('questions')" id="tabBtnQuestions" class="pb-3 text-xs font-bold border-b-2 border-purple-500 text-purple-400 flex items-center space-x-2 cursor-pointer">
                    <i class="fa-solid fa-list-check"></i> <span>Daftar Soal Kuis (<span id="questionCountBadge">0</span>)</span>
                </button>
                <button onclick="switchAdminTab('scores')" id="tabBtnScores" class="pb-3 text-xs font-bold border-b-2 border-transparent text-slate-400 hover:text-slate-200 flex items-center space-x-2 cursor-pointer">
                    <i class="fa-solid fa-chart-simple"></i> <span>Rekap Nilai Siswa (<span id="scoreCountBadge">0</span>)</span>
                </button>
            </div>

            <!-- TAB 1: D
