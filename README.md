<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI DSS Dashboard - ระบบสนับสนุนการตัดสินใจคุณภาพน้ำในบ่อกุ้ง</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Chart.js CDN -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <!-- Google Fonts: Sarabun -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Sarabun', sans-serif;
      background-color: #F0F8FF;
    }
    input[type=range] {
      accent-color: #2563eb;
    }
  </style>
</head>
<body class="text-slate-800 min-h-screen flex flex-col justify-between">

  <!-- Top Navbar -->
  <header class="bg-white border-b border-blue-100 shadow-sm sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between">
      <div class="flex items-center space-x-3 cursor-pointer" onclick="navigateTo('view-home')">
        <div class="w-10 h-10 rounded-full bg-blue-600 flex items-center justify-center text-white font-bold text-lg shadow-md">
          💧
        </div>
        <div>
          <h1 class="text-lg md:text-xl font-bold text-blue-950 leading-tight">AI DSS Dashboard</h1>
          <p class="text-xs text-slate-500">ระบบสนับสนุนการตัดสินใจคุณภาพน้ำในบ่อกุ้ง (ZB-5)</p>
        </div>
      </div>
      <div class="flex items-center space-x-2">
        <span class="inline-flex items-center px-2.5 py-1 rounded-full text-xs font-medium bg-emerald-100 text-emerald-800">
          <span class="w-2 h-2 mr-1.5 bg-emerald-500 rounded-full animate-pulse"></span> ออนไลน์
        </span>
        <button id="btn-back-home" onclick="navigateTo('view-home')" class="hidden text-xs bg-slate-100 hover:bg-slate-200 text-slate-700 font-medium px-3 py-1.5 rounded-lg border border-slate-300 transition">
          🏠 เมนูหลัก
        </button>
      </div>
    </div>
  </header>

  <!-- Main Content Container -->
  <main class="max-w-6xl mx-auto px-4 py-6 w-full flex-grow">

    <!-- VIEW 0: MAIN MENU HUB -->
    <section id="view-home" class="space-y-6">
      <div class="text-center md:text-left space-y-1">
        <h2 class="text-2xl font-bold text-blue-950">เลือกฟังก์ชันการทำงาน</h2>
        <p class="text-sm text-slate-600">กรอกค่าคุณภาพน้ำในฟังก์ชันที่ 1 เพื่อซิงค์ข้อมูลคำนวณและทำนายผลทั่วทั้งระบบ</p>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5">
        <!-- Card 1 -->
        <div onclick="navigateTo('view-current')" class="bg-white p-5 rounded-2xl border-2 border-blue-200 shadow-sm hover:shadow-md hover:border-blue-500 transition cursor-pointer flex flex-col justify-between group">
          <div class="flex items-start justify-between mb-4">
            <div class="w-12 h-12 rounded-xl bg-blue-50 text-blue-600 flex items-center justify-center text-2xl group-hover:scale-110 transition">
              🧪
            </div>
            <span class="text-xs font-bold px-2 py-0.5 rounded bg-blue-600 text-white">ฟังก์ชันหลัก</span>
          </div>
          <div>
            <h3 class="text-base font-bold text-slate-800 group-hover:text-blue-600 transition">1. ตรวจวัดและประเมินค่าน้ำ</h3>
            <p class="text-xs text-slate-500 mt-1">กรอก/เลื่อนค่า pH, ขนาดไร่, ความลึกบ่อ และประเมินทันที</p>
          </div>
        </div>

        <!-- Card 2 -->
        <div onclick="navigateTo('view-trends')" class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm hover:shadow-md hover:border-blue-300 transition cursor-pointer flex flex-col justify-between group">
          <div class="flex items-start justify-between mb-4">
            <div class="w-12 h-12 rounded-xl bg-emerald-50 text-emerald-600 flex items-center justify-center text-2xl group-hover:scale-110 transition">
              📈
            </div>
            <span class="text-xs font-semibold px-2 py-0.5 rounded bg-emerald-100 text-emerald-800">ฟังก์ชัน 2</span>
          </div>
          <div>
            <h3 class="text-base font-bold text-slate-800 group-hover:text-emerald-600 transition">2. แนวโน้มคุณภาพน้ำ (6 ชม.)</h3>
            <p class="text-xs text-slate-500 mt-1">AI ทำนายค่าน้ำล่วงหน้าก่อนเกิดวิกฤตกรด</p>
          </div>
        </div>

        <!-- Card 3 -->
        <div onclick="navigateTo('view-dosage')" class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm hover:shadow-md hover:border-blue-300 transition cursor-pointer flex flex-col justify-between group">
          <div class="flex items-start justify-between mb-4">
            <div class="w-12 h-12 rounded-xl bg-indigo-50 text-indigo-600 flex items-center justify-center text-2xl group-hover:scale-110 transition">
              ⚖️
            </div>
            <span class="text-xs font-semibold px-2 py-0.5 rounded bg-indigo-100 text-indigo-800">ฟังก์ชัน 3</span>
          </div>
          <div>
            <h3 class="text-base font-bold text-slate-800 group-hover:text-indigo-600 transition">3. คำแนะนำการใช้สาร ZB-5</h3>
            <p class="text-xs text-slate-500 mt-1">คำนวณปริมาณผงสารแม่นยำ ลดความเหลื่อมล้ำ</p>
          </div>
        </div>

        <!-- Card 4 -->
        <div onclick="navigateTo('view-history')" class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm hover:shadow-md hover:border-blue-300 transition cursor-pointer flex flex-col justify-between group">
          <div class="flex items-start justify-between mb-4">
            <div class="w-12 h-12 rounded-xl bg-amber-50 text-amber-600 flex items-center justify-center text-2xl group-hover:scale-110 transition">
              📅
            </div>
            <span class="text-xs font-semibold px-2 py-0.5 rounded bg-amber-100 text-amber-800">ฟังก์ชัน 4</span>
          </div>
          <div>
            <h3 class="text-base font-bold text-slate-800 group-hover:text-amber-600 transition">4. ประวัติคุณภาพน้ำ</h3>
            <p class="text-xs text-slate-500 mt-1">สถิติย้อนหลัง 7/14/30 วัน และเปรียบเทียบรอบเลี้ยง</p>
          </div>
        </div>

        <!-- Card 5 -->
        <div onclick="navigateTo('view-warning')" class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm hover:shadow-md hover:border-blue-300 transition cursor-pointer flex flex-col justify-between group">
          <div class="flex items-start justify-between mb-4">
            <div class="w-12 h-12 rounded-xl bg-rose-50 text-rose-600 flex items-center justify-center text-2xl group-hover:scale-110 transition">
              🚨
            </div>
            <span class="text-xs font-semibold px-2 py-0.5 rounded bg-rose-100 text-rose-800">ฟังก์ชัน 5</span>
          </div>
          <div>
            <h3 class="text-base font-bold text-slate-800 group-hover:text-rose-600 transition">5. การแจ้งเตือน EMS Risk</h3>
            <p class="text-xs text-slate-500 mt-1">คะแนนเสี่ยง 0-100 พร้อมระดับความปลอดภัย</p>
          </div>
        </div>

        <!-- Card 6 -->
        <div onclick="navigateTo('view-summary')" class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm hover:shadow-md hover:border-blue-300 transition cursor-pointer flex flex-col justify-between group">
          <div class="flex items-start justify-between mb-4">
            <div class="w-12 h-12 rounded-xl bg-teal-50 text-teal-600 flex items-center justify-center text-2xl group-hover:scale-110 transition">
              📋
            </div>
            <span class="text-xs font-semibold px-2 py-0.5 rounded bg-teal-100 text-teal-800">ฟังก์ชัน 6</span>
          </div>
          <div>
            <h3 class="text-base font-bold text-slate-800 group-hover:text-teal-600 transition">6. สรุปสถานะบ่อประจำวัน</h3>
            <p class="text-xs text-slate-500 mt-1">ภาพรวม 4 มิติ และคำแนะนำสิ่งที่ต้องทำวันนี้</p>
          </div>
        </div>
      </div>
    </section>

    <!-- VIEW 1: CURRENT QUALITY (INPUT & EVALUATION HUB) -->
    <section id="view-current" class="hidden space-y-6">
      <div class="flex items-center justify-between border-b border-blue-100 pb-3">
        <h2 class="text-xl font-bold text-blue-950 flex items-center">🧪 1. ตรวจวัดและประเมินคุณภาพน้ำ</h2>
        <span class="text-xs bg-blue-100 text-blue-800 font-medium px-2.5 py-1 rounded-md">ศูนย์กลางการคำนวณ</span>
      </div>

      <div class="bg-white p-6 rounded-2xl border border-blue-100 shadow-sm space-y-6">
        <!-- Form Inputs: Size & Depth -->
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pb-4 border-b border-slate-100">
          <div>
            <label class="block text-xs font-bold text-slate-700 mb-1">ขนาดพื้นที่บ่อกุ้ง (ไร่)</label>
            <input id="input-area" type="number" step="0.1" value="2.0" oninput="updateAllCalculations()" class="w-full px-3 py-2 border rounded-xl font-semibold text-slate-800 focus:ring-2 focus:ring-blue-400 outline-none bg-slate-50">
          </div>
          <div>
            <label class="block text-xs font-bold text-slate-700 mb-1">ความลึกน้ำเฉลี่ย (เมตร)</label>
            <input id="input-depth" type="number" step="0.1" value="1.5" oninput="updateAllCalculations()" class="w-full px-3 py-2 border rounded-xl font-semibold text-slate-800 focus:ring-2 focus:ring-blue-400 outline-none bg-slate-50">
          </div>
        </div>

        <!-- Slider & Big pH Display (Design matching the reference image) -->
        <div class="space-y-4">
          <div class="text-center">
            <span class="text-xs font-semibold text-slate-500 uppercase">ค่าพีเอช (pH)</span>
            <div id="ph-display" class="text-6xl font-black text-blue-600 my-1">4.8</div>
          </div>

          <!-- Interactive Range Slider -->
          <div class="px-2">
            <input id="input-ph-slider" type="range" min="0" max="10" step="0.1" value="4.8" oninput="syncPhInput(this.value)" class="w-full h-2 bg-slate-200 rounded-lg cursor-pointer">
            <div class="flex justify-between text-[11px] text-slate-400 font-medium mt-1">
              <span>0.0</span>
              <span>2.0</span>
              <span>4.0</span>
              <span>6.0</span>
              <span>8.0</span>
              <span>10.0</span>
            </div>
          </div>
        </div>

        <!-- Dynamic EMS Risk Box (Matching Reference Image) -->
        <div id="risk-banner" class="p-4 rounded-2xl bg-rose-100 border border-rose-200 transition-all duration-300">
          <span class="text-xs font-medium text-rose-800 block">ความเสี่ยงจาก EMS</span>
          <div id="risk-banner-title" class="text-2xl font-bold text-rose-900 mt-0.5">ความเสี่ยงสูง</div>
          <span class="text-xs text-rose-700 font-medium">ความเชื่อมั่น: 95%</span>
        </div>

        <div class="text-center pt-2">
          <p class="text-xs text-slate-500">ข้อมูลนี้เชื่อมโยงและคำนวณผลอัตโนมัติไปยังฟังก์ชันที่ 2, 3, 4, 5 และ 6 เรียบร้อยแล้ว</p>
        </div>
      </div>
    </section>

    <!-- VIEW 2: WATER QUALITY TRENDS (6 HOURS AHEAD) -->
    <section id="view-trends" class="hidden space-y-6">
      <div class="flex items-center justify-between border-b border-blue-100 pb-3">
        <h2 class="text-xl font-bold text-blue-950">📈 2. แนวโน้มคุณภาพน้ำ (AI ทำนายล่วงหน้า 6 ชม.)</h2>
        <span class="text-xs bg-emerald-100 text-emerald-800 font-medium px-2.5 py-1 rounded-md">ไม่ต้องรอน้ำแกว่ง</span>
      </div>

      <div class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm space-y-4">
        <h3 class="text-sm font-bold text-slate-700">การพยากรณ์ค่า pH ล่วงหน้า 6 ชั่วโมงตามปริมาณชีวมวลและแสงแดด</h3>
        <div class="h-64">
          <canvas id="trendsChart"></canvas>
        </div>
        <div id="trends-insight" class="p-3.5 bg-blue-50 rounded-xl border border-blue-100 text-xs text-blue-900 leading-relaxed">
          <!-- Populated by JS -->
        </div>
      </div>
    </section>

    <!-- VIEW 3: SMART DOSAGE RECOMMENDATION -->
    <section id="view-dosage" class="hidden space-y-6">
      <div class="flex items-center justify-between border-b border-blue-100 pb-3">
        <h2 class="text-xl font-bold text-blue-950">⚖️ 3. คำแนะนำการใช้สาร ZB-5 (ลดความเหลื่อมล้ำ)</h2>
        <span class="text-xs bg-indigo-100 text-indigo-800 font-medium px-2.5 py-1 rounded-md">สูตรแม่นยำรายบ่อ</span>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-5">
        <div class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm flex flex-col justify-between">
          <span class="text-xs font-semibold text-slate-500">ผงสารนาโนคอมโพสิต ZB-5</span>
          <div id="dosage-zb5" class="text-4xl font-black text-blue-600 my-2">0.50 <span class="text-sm font-normal text-slate-500">กก.</span></div>
          <span class="text-[11px] text-blue-700">คำนวณตามปริมาตรน้ำจริง</span>
        </div>

        <div class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm flex flex-col justify-between">
          <span class="text-xs font-semibold text-slate-500">สารปรับสมดุลเสริม (Buffer)</span>
          <div id="dosage-buffer" class="text-4xl font-black text-slate-700 my-2">0.30 <span class="text-sm font-normal text-slate-500">กก.</span></div>
          <span class="text-[11px] text-slate-500">ช่วยพยุงสมดุลระบบ</span>
        </div>

        <div class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm flex flex-col justify-between">
          <span class="text-xs font-semibold text-slate-500">ปริมาตรน้ำในบ่อทั้งหมด</span>
          <div id="dosage-volume" class="text-3xl font-black text-slate-800 my-2">4,800,000 <span class="text-xs font-normal text-slate-500">ลิตร</span></div>
          <span class="text-[11px] text-emerald-600 font-medium">คำนวณจากขนาดบ่อและความลึก</span>
        </div>
      </div>

      <div class="bg-white p-5 rounded-2xl border border-blue-100 text-xs text-slate-600 space-y-2">
        <h4 class="font-bold text-slate-800">จุดเด่นสำคัญของโครงงาน ZB-5:</h4>
        <p>ช่วยให้เกษตรกรรายย่อยใส่สารได้ถูกต้องแม่นยำเทียบเท่ากับฟาร์มขนาดใหญ่ที่มีนักวิจัยคอยควบคุม ป้องกันการสูญเสียต้นทุนจากเคมีภัณฑ์เกินความจำเป็น และหยุดทำงานเองอัตโนมัติที่ pH 7.79</p>
      </div>
    </section>

    <!-- VIEW 4: HISTORICAL DATA & ANALYTICS -->
    <section id="view-history" class="hidden space-y-6">
      <div class="flex items-center justify-between border-b border-blue-100 pb-3">
        <h2 class="text-xl font-bold text-blue-950">📅 4. ประวัติคุณภาพน้ำ (ย้อนหลัง 7/14/30 วัน)</h2>
        <div class="flex space-x-1">
          <button class="px-3 py-1 text-xs font-bold bg-blue-600 text-white rounded-lg">7 วัน</button>
          <button class="px-3 py-1 text-xs font-medium bg-white text-slate-600 border rounded-lg">14 วัน</button>
          <button class="px-3 py-1 text-xs font-medium bg-white text-slate-600 border rounded-lg">30 วัน</button>
        </div>
      </div>

      <div class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm space-y-4">
        <h3 class="text-sm font-bold text-slate-700">กราฟความเสถียรของคุณภาพน้ำเทียบกับจุดสมดุล ZB-5 (pH 7.79)</h3>
        <div class="h-64">
          <canvas id="historyChart"></canvas>
        </div>
        <p class="text-xs text-slate-500 text-center">ช่วยให้เกษตรกรใช้วางแผนการจัดการคุณภาพน้ำล่วงหน้าและเปรียบเทียบผลผลิตแต่ละรอบการเลี้ยง</p>
      </div>
    </section>

    <!-- VIEW 5: SMART EARLY WARNING (EMS RISK SCORE) -->
    <section id="view-warning" class="hidden space-y-6">
      <div class="flex items-center justify-between border-b border-blue-100 pb-3">
        <h2 class="text-xl font-bold text-blue-950">🚨 5. การแจ้งเตือน EMS Risk (คะแนนเสี่ยง 0-100)</h2>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <!-- Big Score Card -->
        <div id="risk-score-card" class="bg-white p-6 rounded-2xl border border-rose-200 shadow-sm text-center flex flex-col justify-center items-center">
          <span class="text-xs font-bold text-slate-500 uppercase">EMS Risk Score</span>
          <div id="risk-score-number" class="text-6xl font-black text-rose-600 my-2">88</div>
          <span id="risk-score-badge" class="px-3 py-1 bg-rose-100 text-rose-800 font-bold text-xs rounded-full">อันตราย (High Risk)</span>
          <p class="text-[11px] text-slate-400 mt-3">ระดับ 0-30: ปลอดภัย | 31-70: เฝ้าระวัง | 71-100: อันตราย</p>
        </div>

        <div class="md:col-span-2 bg-white p-5 rounded-2xl border border-blue-100 shadow-sm space-y-3 flex flex-col justify-between">
          <div>
            <h3 class="text-sm font-bold text-slate-800 mb-2">คำแนะนำตามระดับความเสี่ยง:</h3>
            <div id="risk-advice" class="p-3 rounded-xl bg-slate-50 text-xs text-slate-700 leading-relaxed">
              <!-- Populated by JS -->
            </div>
          </div>
          <div class="p-3 bg-blue-50 rounded-xl border border-blue-100 text-[11px] text-blue-800">
            🛡️ <strong>กลไก ZB-5:</strong> สามารถยับยั้งเชื้อแบคทีเรีย <em>Vibrio</em> spp. ได้ถึง 99.38% ภายใน 120 นาที เมื่อทำการเติมสารตามที่ระบบแนะนำ
          </div>
        </div>
      </div>
    </section>

    <!-- VIEW 6: EXECUTIVE SUMMARY -->
    <section id="view-summary" class="hidden space-y-6">
      <div class="flex items-center justify-between border-b border-blue-100 pb-3">
        <h2 class="text-xl font-bold text-blue-950">📋 6. สรุปภาพรวมสถานะบ่อ (วันนี้ต้องทำอะไร)</h2>
        <span class="text-xs bg-teal-100 text-teal-800 font-medium px-2 py-1 rounded">Daily Summary</span>
      </div>

      <!-- 4 Dimensions Grid -->
      <div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
        <div class="bg-white p-4 rounded-xl border border-blue-100 shadow-sm text-center">
          <span class="text-xs text-slate-500 block mb-1">1. สถานะบ่อ</span>
          <span id="sum-pond-status" class="px-2.5 py-1 bg-rose-100 text-rose-800 font-bold text-xs rounded-full">วิกฤตกรด</span>
        </div>
        <div class="bg-white p-4 rounded-xl border border-blue-100 shadow-sm text-center">
          <span class="text-xs text-slate-500 block mb-1">2. ความเสี่ยง EMS</span>
          <span id="sum-ems-risk" class="px-2.5 py-1 bg-rose-100 text-rose-800 font-bold text-xs rounded-full">สูง</span>
        </div>
        <div class="bg-white p-4 rounded-xl border border-blue-100 shadow-sm text-center">
          <span class="text-xs text-slate-500 block mb-1">3. สุขภาพกุ้ง</span>
          <span id="sum-shrimp-health" class="px-2.5 py-1 bg-amber-100 text-amber-800 font-bold text-xs rounded-full">มีความเครียด</span>
        </div>
        <div class="bg-white p-4 rounded-xl border border-blue-100 shadow-sm text-center">
          <span class="text-xs text-slate-500 block mb-1">4. การใช้สาร ZB-5</span>
          <span id="sum-dosage-need" class="px-2.5 py-1 bg-blue-100 text-blue-800 font-bold text-xs rounded-full">ต้องเติมทันที</span>
        </div>
      </div>

      <!-- Actionable Checklist Card -->
      <div class="bg-white p-5 rounded-2xl border border-blue-100 shadow-sm space-y-3">
        <h3 class="text-sm font-bold text-slate-800 flex items-center">
          🎯 สิ่งที่เกษตรกรต้องทำในวันนี้:
        </h3>
        <ul id="sum-actions-list" class="text-xs text-slate-700 space-y-2 list-disc list-inside bg-slate-50 p-4 rounded-xl">
          <!-- Populated by JS -->
        </ul>
      </div>
    </section>

  </main>

  <!-- Bottom Navigation Bar (Mobile Friendly) -->
  <nav class="bg-white border-t border-blue-100 sticky bottom-0 z-40 py-2 px-4 shadow-md md:hidden">
    <div class="flex justify-around items-center text-center">
      <button onclick="navigateTo('view-home')" class="text-xs text-slate-600 flex flex-col items-center">
        <span class="text-base">🏠</span> หน้าแรก
      </button>
      <button onclick="navigateTo('view-current')" class="text-xs text-blue-600 font-bold flex flex-col items-center">
        <span class="text-base">🧪</span> ประเมิน pH
      </button>
      <button onclick="navigateTo('view-dosage')" class="text-xs text-slate-600 flex flex-col items-center">
        <span class="text-base">⚖️</span> ปริมาณสาร
      </button>
      <button onclick="navigateTo('view-summary')" class="text-xs text-slate-600 flex flex-col items-center">
        <span class="text-base">📋</span> สรุปบ่อ
      </button>
    </div>
  </nav>

  <!-- Footer -->
  <footer class="bg-white border-t border-slate-200 py-3 text-center text-xs text-slate-400 hidden md:block">
    AI DSS Dashboard © 2026 โครงงานนวัตกรรม ZB-5 Nanocomposite เพื่อการเพาะเลี้ยงสัตว์น้ำ
  </footer>

  <!-- Core JavaScript Logic -->
  <script>
    // State Store
    let currentPh = 4.8;
    let pondArea = 2.0;
    let pondDepth = 1.5;

    // View Navigation Router
    const views = ['view-home', 'view-current', 'view-trends', 'view-dosage', 'view-history', 'view-warning', 'view-summary'];

    function navigateTo(targetId) {
      views.forEach(id => {
        const el = document.getElementById(id);
        if (el) el.classList.add('hidden');
      });

      const target = document.getElementById(targetId);
      if (target) target.classList.remove('hidden');

      const backBtn = document.getElementById('btn-back-home');
      if (targetId === 'view-home') {
        backBtn.classList.add('hidden');
      } else {
        backBtn.classList.remove('hidden');
      }

      if (targetId === 'view-trends') renderTrendsChart();
      if (targetId === 'view-history') renderHistoryChart();
    }

    // Sync Slider and Inputs
    function syncPhInput(val) {
      currentPh = parseFloat(val);
      document.getElementById('ph-display').innerText = currentPh.toFixed(1);
      updateAllCalculations();
    }

    // Main Centralized Calculation Engine
    function updateAllCalculations() {
      pondArea = parseFloat(document.getElementById('input-area').value) || 1.0;
      pondDepth = parseFloat(document.getElementById('input-depth').value) || 1.0;

      // 1. Water Volume (Liters): 1 Rai = 1,600 sq.m.
      const volumeLiters = pondArea * 1600 * pondDepth * 1000;
      
      // 2. Dosage Calculation for ZB-5
      const deltaH = Math.max(0, 7.79 - currentPh);
      const zb5Kg = ((volumeLiters / 1000000) * deltaH * 0.45).toFixed(2);
      const bufferKg = (zb5Kg * 0.6).toFixed(2);

      // 3. EMS Risk Score Calculation (0-100)
      let riskScore = 15;
      let riskTitle = "ความเสี่ยงต่ำ";
      let bannerBg = "bg-emerald-100 border-emerald-200 text-emerald-900";
      let badgeClass = "bg-emerald-100 text-emerald-800";

      if (currentPh < 6.5) {
        riskScore = Math.min(95, Math.round(85 + (6.5 - currentPh) * 6));
        riskTitle = "ความเสี่ยงสูง";
        bannerBg = "bg-rose-100 border-rose-200 text-rose-900";
        badgeClass = "bg-rose-100 text-rose-800";
      } else if (currentPh < 7.5 || currentPh > 8.5) {
        riskScore = 48;
        riskTitle = "เฝ้าระวัง";
        bannerBg = "bg-amber-100 border-amber-200 text-amber-900";
        badgeClass = "bg-amber-100 text-amber-800";
      }

      // Update Function 1 Banner
      const riskBanner = document.getElementById('risk-banner');
      riskBanner.className = `p-4 rounded-2xl border transition-all duration-300 ${bannerBg}`;
      document.getElementById('risk-banner-title').innerText = riskTitle;

      // Update Function 3 (Dosage)
      document.getElementById('dosage-zb5').innerHTML = `${zb5Kg} <span class="text-sm font-normal text-slate-500">กก.</span>`;
      document.getElementById('dosage-buffer').innerHTML = `${bufferKg} <span class="text-sm font-normal text-slate-500">กก.</span>`;
      document.getElementById('dosage-volume').innerHTML = `${volumeLiters.toLocaleString()} <span class="text-xs font-normal text-slate-500">ลิตร</span>`;

      // Update Function 5 (Risk)
      const scoreNumber = document.getElementById('risk-score-number');
      scoreNumber.innerText = riskScore;
      scoreNumber.className = `text-6xl font-black my-2 ${currentPh < 6.5 ? 'text-rose-600' : currentPh < 7.5 ? 'text-amber-600' : 'text-emerald-600'}`;
      
      const badge = document.getElementById('risk-score-badge');
      badge.className = `px-3 py-1 font-bold text-xs rounded-full ${badgeClass}`;
      badge.innerText = riskTitle;

      const riskAdvice = document.getElementById('risk-advice');
      if (riskScore >= 70) {
        riskAdvice.innerHTML = `⚠️ <strong>วิกฤตน้ำเป็นกรดเฉียบพลัน:</strong> ค่าน้ำ pH ${currentPh.toFixed(1)} เร่งการเพิ่มจำนวนของแบคทีเรีย <em>Vibrio</em> spp. แนะนำโปรยผง ZB-5 ปริมาณ <strong>${zb5Kg} กิโลกรัม</strong> ทันที เพื่อปรับสมดุลสู่ pH 7.79 ภายใน 120 นาที`;
      } else if (riskScore >= 35) {
        riskAdvice.innerHTML = `⚠️ <strong>สภาวะเฝ้าระวัง:</strong> ค่าน้ำเริ่มแกว่งตัว แนะนำตรวจวัดออกซิเจนและเปิดเครื่องตีน้ำ`;
      } else {
        riskAdvice.innerHTML = `✓ <strong>สภาวะปกติสมบูรณ์:</strong> ค่าน้ำมีความเสถียร กุ้งไม่เกิดความเครียด อัตราการเกิดโรคน้อยมาก`;
      }

      // Update Function 6 (Summary)
      document.getElementById('sum-pond-status').innerText = currentPh < 6.5 ? "วิกฤตกรด" : (currentPh > 8.5 ? "ด่างเกิน" : "ปกติ");
      document.getElementById('sum-pond-status').className = `px-2.5 py-1 font-bold text-xs rounded-full ${badgeClass}`;
      
      document.getElementById('sum-ems-risk').innerText = riskTitle;
      document.getElementById('sum-ems-risk').className = `px-2.5 py-1 font-bold text-xs rounded-full ${badgeClass}`;
      
      document.getElementById('sum-shrimp-health').innerText = currentPh < 6.5 ? "มีความเครียดสูง" : "สมบูรณ์แข็งแรง";
      document.getElementById('sum-dosage-need').innerText = zb5Kg > 0 ? `เติม ZB-5 ${zb5Kg} กก.` : "ไม่ต้องเติมสาร";

      // Update Function 6 Action List
      const actionsList = document.getElementById('sum-actions-list');
      if (currentPh < 6.5) {
        actionsList.innerHTML = `
          <li><strong>เร่งด่วน:</strong> เติมสารผง ZB-5 จำนวน ${zb5Kg} กก. บริเวณหน้าแนวเครื่องตีน้ำ</li>
          <li>เปิดเครื่องตีน้ำเต็มระบบเพื่อกระจายมวลสารให้ครอบคลุมทั้งบ่อ (${volumeLiters.toLocaleString()} ลิตร)</li>
          <li>ระบบจะปรับสมดุลสู่ pH 7.79 อัตโนมัติใน 120 นาที ไม่ต้องเติมปูนขาวซ้ำ</li>
        `;
      } else {
        actionsList.innerHTML = `
          <li>สภาพน้ำสมดุลดี ไม่จำเป็นต้องเติมสารเคมีหรือผง ZB-5 ในวันนี้</li>
          <li>ให้อาหารกุ้งตามรอบปกติ และตรวจวัดค่า pH ซ้ำอีกครั้งเวลา 18:00 น.</li>
        `;
      }

      // Update Insight text for Function 2
      const trendsInsight = document.getElementById('trends-insight');
      trendsInsight.innerHTML = currentPh < 6.5 
        ? `🚨 <strong>AI ตรวจพบวิกฤต:</strong> คาดการณ์ว่าหากไม่เติม ZB-5 ในอีก 6 ชม. ค่า pH จะลดลงต่อเนื่องจนส่งผลให้กุ้งตายด่วน (EMS) แนะนำให้ปฏิบัติตามฟังก์ชันที่ 3 ทันที`
        : `💡 <strong>AI พยากรณ์:</strong> สภาพน้ำมีแนวโน้มทรงตัวในเกณฑ์ปลอดภัยตลอด 6 ชั่วโมงข้างหน้า`;
    }

    // Chart.js Handlers
    let trendsChartInstance = null;
    let historyChartInstance = null;

    function renderTrendsChart() {
      const ctx = document.getElementById('trendsChart').getContext('2d');
      const predictedPhs = [
        currentPh, 
        Math.max(4.0, currentPh - 0.1), 
        Math.max(4.0, currentPh - 0.15), 
        (currentPh < 6.5 ? currentPh + 0.3 : 7.65), 
        7.75, 
        7.79
      ];

      if (trendsChartInstance) {
        trendsChartInstance.data.datasets[0].data = predictedPhs;
        trendsChartInstance.update();
        return;
      }

      trendsChartInstance = new Chart(ctx, {
        type: 'line',
        data: {
          labels: ['ปัจจุบัน', '+1 ชม.', '+2 ชม.', '+3 ชม.', '+4 ชม.', '+6 ชม.'],
          datasets: [{
            label: 'แนวโน้มค่า pH ที่ทำนาย (AI Simulation)',
            data: predictedPhs,
            borderColor: '#2563eb',
            backgroundColor: 'rgba(37, 99, 235, 0.1)',
            fill: true,
            tension: 0.3
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: { y: { min: 4.0, max: 9.0 } }
        }
      });
    }

    function renderHistoryChart() {
      if (historyChartInstance) return;
      const ctx = document.getElementById('historyChart').getContext('2d');
      historyChartInstance = new Chart(ctx, {
        type: 'line',
        data: {
          labels: ['Day 1', 'Day 2', 'Day 3', 'Day 4', 'Day 5', 'Day 6', 'วันนี้'],
          datasets: [
            {
              label: 'ค่า pH ที่บันทึก',
              data: [7.8, 7.6, 7.7, 7.5, 7.8, 7.6, currentPh],
              borderColor: '#059669',
              tension: 0.2
            },
            {
              label: 'จุดสมดุลปลอดภัย ZB-5 (pH 7.79)',
              data: [7.79, 7.79, 7.79, 7.79, 7.79, 7.79, 7.79],
              borderColor: '#94a3b8',
              borderDash: [5, 5],
              fill: false
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: { y: { min: 4.0, max: 9.0 } }
        }
      });
    }

    // Initial Execution
    window.onload = () => {
      updateAllCalculations();
    };
  </script>
</body>
</html>
