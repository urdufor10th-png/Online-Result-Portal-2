# Online-Result-Portal-2
<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LUCENT COACHING CENTRE | Online Examination Portal</title>
  <style>
    :root {
      --gov-navy: #0b2545;
      --gov-gold: #c59b27;
      --gov-blue: #134074;
      --gov-light: #eef4f8;
      --gov-border: #cbd5e1;
      --gov-text: #0f172a;
      --gov-green: #15803d;
      --gov-red: #b91c1c;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Arial, sans-serif; }
    body {
      background-color: #f1f5f9;
      color: var(--gov-text);
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    /* Government / Board Style Official Header */
    .top-strip {
      background: var(--gov-gold);
      color: #000;
      font-size: 0.75rem;
      padding: 4px 20px;
      display: flex;
      justify-content: space-between;
      font-weight: 600;
      letter-spacing: 0.5px;
    }
    .main-header {
      background: var(--gov-navy);
      color: white;
      padding: 16px 20px;
      border-bottom: 4px solid var(--gov-gold);
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 15px;
    }
    .brand-wrap {
      display: flex;
      align-items: center;
      gap: 15px;
    }
    .logo-badge {
      width: 58px;
      height: 58px;
      background: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.8rem;
      border: 3px solid var(--gov-gold);
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    }
    .brand-title h1 {
      font-size: 1.5rem;
      font-weight: 800;
      letter-spacing: 1px;
      color: #ffffff;
    }
    .brand-title p {
      font-size: 0.8rem;
      color: #cbd5e1;
      margin-top: 2px;
    }
    .header-details {
      font-size: 0.78rem;
      color: #e2e8f0;
      text-align: right;
      line-height: 1.4;
    }

    /* Notification Marquee */
    .notice-bar {
      background: #ffffff;
      border-bottom: 1px solid var(--gov-border);
      padding: 6px 15px;
      display: flex;
      align-items: center;
      font-size: 0.82rem;
    }
    .notice-tag {
      background: var(--gov-red);
      color: white;
      padding: 2px 8px;
      font-weight: bold;
      border-radius: 3px;
      font-size: 0.72rem;
      margin-right: 12px;
      white-space: nowrap;
    }

    /* Container */
    .portal-container {
      max-width: 900px;
      margin: 25px auto;
      padding: 0 15px;
      flex: 1;
      width: 100%;
    }

    /* Search Dashboard Card */
    .dashboard-card {
      background: #ffffff;
      border-radius: 8px;
      box-shadow: 0 4px 18px rgba(11, 37, 69, 0.08);
      border: 1px solid var(--gov-border);
      overflow: hidden;
      margin-bottom: 25px;
    }
    .card-top {
      background: var(--gov-blue);
      color: white;
      padding: 12px 20px;
      font-weight: 700;
      font-size: 0.95rem;
      letter-spacing: 0.5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .card-body {
      padding: 24px;
    }
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 16px;
      margin-bottom: 20px;
    }
    .form-field {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    .form-field label {
      font-size: 0.85rem;
      font-weight: 700;
      color: #334155;
    }
    .form-field select, .form-field input {
      padding: 10px 12px;
      border: 1.5px solid #cbd5e1;
      border-radius: 6px;
      font-size: 0.92rem;
      outline: none;
      transition: all 0.2s;
    }
    .form-field select:focus, .form-field input:focus {
      border-color: var(--gov-blue);
      box-shadow: 0 0 0 3px rgba(19, 64, 116, 0.15);
    }
    .captcha-row {
      display: flex;
      gap: 10px;
      align-items: center;
    }
    .captcha-code {
      background: #e2e8f0;
      color: var(--gov-navy);
      font-family: 'Courier New', Courier, monospace;
      font-size: 1.35rem;
      font-weight: 800;
      letter-spacing: 5px;
      padding: 7px 15px;
      border-radius: 6px;
      border: 1px dashed #64748b;
      user-select: none;
      text-decoration: line-through;
    }
    .btn-refresh {
      background: #64748b;
      color: white;
      border: none;
      padding: 9px 12px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 0.85rem;
    }
    .action-panel {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-top: 15px;
    }
    .btn-submit {
      background: var(--gov-navy);
      color: #ffffff;
      border: 1px solid var(--gov-gold);
      padding: 11px 32px;
      font-size: 0.95rem;
      font-weight: 700;
      border-radius: 6px;
      cursor: pointer;
      box-shadow: 0 2px 6px rgba(0,0,0,0.15);
      transition: opacity 0.2s;
    }
    .btn-submit:hover { opacity: 0.92; }
    .btn-reset {
      background: #64748b;
      color: white;
      border: none;
      padding: 11px 22px;
      font-size: 0.95rem;
      border-radius: 6px;
      cursor: pointer;
    }
    .error-box {
      margin-top: 14px;
      padding: 10px;
      background: #fef2f2;
      border-left: 4px solid var(--gov-red);
      color: var(--gov-red);
      font-size: 0.88rem;
      font-weight: 600;
      display: none;
    }

    /* Official Marksheet Styling */
    .marksheet-wrapper {
      display: none;
      background: white;
      border: 2px solid var(--gov-navy);
      box-shadow: 0 4px 20px rgba(0,0,0,0.15);
      position: relative;
      padding: 30px;
      margin-bottom: 30px;
    }
    .marksheet-border {
      border: 2px dashed var(--gov-gold);
      padding: 25px;
      position: relative;
      background: #fff;
    }
    /* Watermark */
    .watermark {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) rotate(-30deg);
      font-size: 4rem;
      color: rgba(11, 37, 69, 0.04);
      font-weight: 900;
      pointer-events: none;
      white-space: nowrap;
      z-index: 1;
    }
    .ms-header {
      text-align: center;
      border-bottom: 2px solid var(--gov-navy);
      padding-bottom: 12px;
      margin-bottom: 16px;
      position: relative;
      z-index: 2;
    }
    .ms-header h2 {
      font-size: 1.65rem;
      color: var(--gov-navy);
      letter-spacing: 1px;
      font-weight: 900;
    }
    .ms-header p {
      font-size: 0.85rem;
      color: #475569;
      margin: 3px 0;
    }
    .doc-pill {
      background: var(--gov-navy);
      color: var(--gov-gold);
      display: inline-block;
      padding: 4px 18px;
      font-size: 0.82rem;
      font-weight: bold;
      border-radius: 4px;
      margin-top: 6px;
      letter-spacing: 0.8px;
    }
    .student-details {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px 25px;
      margin-bottom: 18px;
      font-size: 0.9rem;
      position: relative;
      z-index: 2;
    }
    .detail-item {
      border-bottom: 1px solid #e2e8f0;
      padding-bottom: 4px;
    }
    .detail-item span.label {
      color: #64748b;
      font-size: 0.82rem;
      display: inline-block;
      width: 120px;
      font-weight: 600;
    }
    .detail-item span.val {
      font-weight: 700;
      color: #0f172a;
    }

    /* Marksheet Table */
    .ms-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.88rem;
      position: relative;
      z-index: 2;
    }
    .ms-table th, .ms-table td {
      border: 1px solid #cbd5e1;
      padding: 9px 8px;
      text-align: center;
    }
    .ms-table th {
      background: #f8fafc;
      color: #1e293b;
      font-weight: 700;
    }
    .text-left { text-align: left !important; padding-left: 12px !important; }
    .badge-first { color: #15803d; font-weight: bold; background: #dcfce7; padding: 2px 10px; border-radius: 4px; }
    .badge-second { color: #0369a1; font-weight: bold; background: #e0f2fe; padding: 2px 10px; border-radius: 4px; }
    .badge-third { color: #b45309; font-weight: bold; background: #fef3c7; padding: 2px 10px; border-radius: 4px; }

    .ms-footer {
      margin-top: 50px;
      display: flex;
      justify-content: space-between;
      text-align: center;
      font-size: 0.82rem;
      font-weight: 700;
      position: relative;
      z-index: 2;
    }
    .sig-slot {
      border-top: 1.5px solid #334155;
      width: 28%;
      padding-top: 6px;
    }

    /* Print toolbar */
    .print-strip {
      text-align: center;
      margin-top: 20px;
    }
    .btn-print-doc {
      background: var(--gov-green);
      color: white;
      border: none;
      padding: 10px 24px;
      font-size: 0.95rem;
      font-weight: 700;
      border-radius: 6px;
      cursor: pointer;
    }

    /* Official Footer */
    footer {
      background: var(--gov-navy);
      color: #94a3b8;
      text-align: center;
      padding: 16px;
      font-size: 0.78rem;
      line-height: 1.5;
      border-top: 3px solid var(--gov-gold);
    }

    @media print {
      body * { visibility: hidden; }
      #printableArea, #printableArea * { visibility: visible; }
      #printableArea {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        margin: 0;
        padding: 0;
        border: none;
      }
      .no-print { display: none !important; }
    }
  </style>
</head>
<body>

  <!-- Official Top Navigation -->
  <div class="top-strip no-print">
    <span>GOVERNMENT OF BIHAR STANDARD COGNIZANT PORTAL</span>
    <span>HELPLINE: +91 8789524958 | MON - SAT (08:00 AM - 06:00 PM)</span>
  </div>

  <header class="main-header no-print">
    <div class="brand-wrap">
      <div class="logo-badge">🏛️</div>
      <div class="brand-title">
        <h1>LUCENT COACHING CENTRE</h1>
        <p>CENTRE FOR ACADEMIC EXCELLENCE & BOARD EXAMINATIONS</p>
      </div>
    </div>
    <div class="header-details">
      <div><b>Near Mithila Eye Hospital, Musrigharari, Samastipur (Bihar)</b></div>
      <div>Director: <b>Md Mahfooz Alam</b> (B.Sc Phy, B.Ed, CTET, STET)</div>
      <div>M.D.: <b>MD Nazir</b> (B.Sc Maths, B.Ed)</div>
    </div>
  </header>

  <div class="notice-bar no-print">
    <span class="notice-tag">ANNOUNCEMENT</span>
    <marquee scrollamount="6" style="color: #334155; font-weight: 600;">
      Official Annual Terminal Results (Class 9th Section A) Session 2026-27 have been published. Enter your valid Roll Number to view and download your digital scorecard.
    </marquee>
  </div>

  <!-- Main Container -->
  <div class="portal-container">

    <!-- Official Search Dashboard -->
    <div class="dashboard-card no-print">
      <div class="card-top">
        <span>ONLINE RESULT VERIFICATION PORTAL</span>
        <span style="font-size: 0.8rem; font-weight: normal; color: var(--gov-gold);">● ENCRYPTED & SECURED</span>
      </div>
      <div class="card-body">
        <div class="form-grid">
          
          <div class="form-field">
            <label>Select Examination</label>
            <select id="examSelect">
              <option value="T1">Terminal Evaluation 2026-27</option>
              <option value="M1">Annual Board Mock Exam</option>
            </select>
          </div>

          <div class="form-field">
            <label>Select Class & Section</label>
            <select id="classSelect">
              <option value="9A">Class 9th (Section A)</option>
              <option value="10A">Class 10th (Regular)</option>
            </select>
          </div>

          <div class="form-field">
            <label>Candidate Roll Number *</label>
            <input type="number" id="rollInput" placeholder="Enter Roll No (e.g. 1, 2, 3...)">
          </div>

          <div class="form-field">
            <label>Security Captcha Code *</label>
            <div class="captcha-row">
              <span id="captchaDisplay" class="captcha-code">----</span>
              <button type="button" class="btn-refresh" onclick="refreshCaptcha()" title="Reload Captcha">🔄</button>
            </div>
            <input type="text" id="captchaInput" placeholder="Type Code Here" style="text-transform: uppercase; margin-top: 4px;" onkeypress="if(event.key==='Enter') verifyAndFetch()">
          </div>

        </div>

        <div class="action-panel">
          <button class="btn-submit" onclick="verifyAndFetch()">VIEW RESULT</button>
          <button class="btn-reset" onclick="resetForm()">RESET</button>
        </div>

        <div id="errorAlert" class="error-box"></div>
      </div>
    </div>

    <!-- Official Marksheet Card -->
    <div id="marksheetView" class="marksheet-wrapper">
      <div class="marksheet-border" id="printableArea">
        <div class="watermark">LUCENT COACHING</div>

        <div class="ms-header">
          <h2>LUCENT COACHING CENTRE</h2>
          <p>NEAR MITHILA EYE HOSPITAL, MUSRIGHARARI, SAMASTIPUR (BIHAR)</p>
          <p>Helpline: +91 8789524958 | Affiliated Standard: Bihar School Examination Board (BSEB)</p>
          <div class="doc-pill">ANNUAL PROGRESS REPORT / MARKS STATEMENT</div>
        </div>

        <div class="student-details">
          <div class="detail-item"><span class="label">Candidate Name:</span> <span class="val" id="dispName">-</span></div>
          <div class="detail-item"><span class="label">Roll Number:</span> <span class="val" id="dispRoll">-</span></div>
          <div class="detail-item"><span class="label">Class & Stream:</span> <span class="val">Class 9th (Section A)</span></div>
          <div class="detail-item"><span class="label">Session:</span> <span class="val">2026-2027</span></div>
          <div class="detail-item"><span class="label">Director:</span> <span class="val">Md Mahfooz Alam</span></div>
          <div class="detail-item"><span class="label">Managing Director:</span> <span class="val">MD Nazir</span></div>
        </div>

        <table class="ms-table">
          <thead>
            <tr>
              <th class="text-left">Subject Description</th>
              <th>Full Marks</th>
              <th>Pass Marks</th>
              <th>Marks Obtained</th>
              <th>Status / Remarks</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td class="text-left">Mathematics (गणित)</td>
              <td>100</td>
              <td>30</td>
              <td id="mMath" style="font-weight: bold;"></td>
              <td id="rMath">Pass</td>
            </tr>
            <tr>
              <td class="text-left">Science (विज्ञान)</td>
              <td>100</td>
              <td>30</td>
              <td id="mSci" style="font-weight: bold;"></td>
              <td id="rSci">Pass</td>
            </tr>
            <tr>
              <td class="text-left">Social Science (सामाजिक विज्ञान)</td>
              <td>100</td>
              <td>30</td>
              <td id="mSst" style="font-weight: bold;"></td>
              <td id="rSst">Pass</td>
            </tr>
            <tr>
              <td class="text-left">English (अंग्रेजी)</td>
              <td>100</td>
              <td>30</td>
              <td id="mEng" style="font-weight: bold;"></td>
              <td id="rEng">Pass</td>
            </tr>
            <tr>
              <td class="text-left">Hindi (हिंदी / मातृभाषा)</td>
              <td>100</td>
              <td>30</td>
              <td id="mHindi" style="font-weight: bold;"></td>
              <td id="rHindi">Pass</td>
            </tr>
          </tbody>
          <tfoot>
            <tr style="font-weight: bold; background: #f8fafc;">
              <td colspan="3" class="text-left" style="font-weight: 800;">AGGREGATE TOTAL & PERCENTAGE:</td>
              <td id="mGrandTotal" style="font-size: 1rem; color: var(--gov-navy);"></td>
              <td id="mPercentage" style="font-size: 1rem; color: var(--gov-navy);"></td>
            </tr>
            <tr style="font-weight: bold; background: #eef4f8;">
              <td colspan="3" class="text-left" style="font-weight: 800;">FINAL PERFORMANCE DIVISION:</td>
              <td colspan="2" id="mFinalDiv"></td>
            </tr>
          </tfoot>
        </table>

        <div class="ms-footer">
          <div class="sig-slot">Checked By (Teacher)</div>
          <div class="sig-slot">Controller of Examinations</div>
          <div class="sig-slot">Director / M.D. Seal</div>
        </div>
      </div>

      <div class="print-strip no-print">
        <button class="btn-print-doc" onclick="window.print()">🖨️ PRINT OFFICIAL MARKSHEET</button>
      </div>
    </div>

  </div>

  <footer class="no-print">
    <p>© 2026-2027 LUCENT COACHING CENTRE, MUSRIGHARARI. All Rights Reserved.</p>
    <p>Official Examination Database & Web Result Publication Engine | Designed for Academic Transparency</p>
  </footer>

  <script>
    let activeCaptcha = "";

    function refreshCaptcha() {
      const chars = "23456789ABCDEFGHJKLMNPQRSTUVWXYZ";
      let code = "";
      for(let i = 0; i < 5; i++) {
        code += chars.charAt(Math.floor(Math.random() * chars.length));
      }
      activeCaptcha = code;
      document.getElementById('captchaDisplay').textContent = code;
      document.getElementById('captchaInput').value = "";
    }

    // PDF se verified 38 records
    const studentRecords = [
      { roll: 1, name: "MD Sartaj", math: 87, sci: 81, sst: 94, eng: 94, hindi: 87, total: 443, pct: "88.6%", result: "First" },
      { roll: 2, name: "kulsum Nishat", math: 86, sci: 88, sst: 92, eng: 96, hindi: 94, total: 456, pct: "91.2%", result: "First" },
      { roll: 3, name: "Sonali Kumari", math: 81, sci: 74, sst: 90, eng: 93, hindi: 94, total: 432, pct: "86.4%", result: "First" },
      { roll: 4, name: "Akshay Kumar", math: 73, sci: 51, sst: 62, eng: 65, hindi: 81, total: 332, pct: "66.4%", result: "First" },
      { roll: 5, name: "rahamati Parveen", math: 69, sci: 55, sst: 62, eng: 64, hindi: 84, total: 334, pct: "66.8%", result: "First" },
      { roll: 6, name: "Raj Gaurav", math: 80, sci: 67, sst: 76, eng: 80, hindi: 88, total: 391, pct: "78.2%", result: "First" },
      { roll: 8, name: "Suraj Kumar", math: 83, sci: 52, sst: 68, eng: 72, hindi: 83, total: 358, pct: "71.6%", result: "First" },
      { roll: 9, name: "MD Okil", math: 63, sci: 54, sst: 56, eng: 60, hindi: 80, total: 313, pct: "62.6%", result: "First" },
      { roll: 10, name: "Kumkum Kumari", math: 67, sci: 60, sst: 68, eng: 70, hindi: 81, total: 346, pct: "69.2%", result: "First" },
      { roll: 11, name: "Anish Kumar", math: 59, sci: 32, sst: 40, eng: 45, hindi: 49, total: 225, pct: "45.0%", result: "Second" },
      { roll: 12, name: "Shashi Kumar", math: 45, sci: 34, sst: 60, eng: 62, hindi: 48, total: 249, pct: "49.8%", result: "Second" },
      { roll: 13, name: "bhakti Priya", math: 63, sci: 52, sst: 56, eng: 60, hindi: 84, total: 315, pct: "63.0%", result: "First" },
      { roll: 14, name: "Aditya Kumar", math: 62, sci: 31, sst: 56, eng: 58, hindi: 61, total: 268, pct: "53.6%", result: "Second" },
      { roll: 17, name: "Ramesh Kumar", math: 55, sci: 34, sst: 57, eng: 60, hindi: 58, total: 264, pct: "52.8%", result: "Second" },
      { roll: 19, name: "Rajveer Kumar", math: 49, sci: 31, sst: 52, eng: 55, hindi: 40, total: 227, pct: "45.4%", result: "Second" },
      { roll: 21, name: "Ankit Kumar", math: 55, sci: 42, sst: 60, eng: 63, hindi: 79, total: 299, pct: "59.8%", result: "Second" },
      { roll: 22, name: "Ayush Kumar", math: 61, sci: 43, sst: 52, eng: 55, hindi: 63, total: 274, pct: "54.8%", result: "Second" },
      { roll: 23, name: "najmeen Parveen", math: 68, sci: 51, sst: 58, eng: 62, hindi: 81, total: 320, pct: "64.0%", result: "First" },
      { roll: 25, name: "Sonu Kumar", math: 62, sci: 45, sst: 58, eng: 60, hindi: 58, total: 283, pct: "56.6%", result: "Second" },
      { roll: 26, name: "Tanu Kumari", math: 63, sci: 32, sst: 52, eng: 55, hindi: 69, total: 271, pct: "54.2%", result: "Second" },
      { roll: 27, name: "Priya Kumari", math: 55, sci: 31, sst: 40, eng: 45, hindi: 81, total: 252, pct: "50.4%", result: "Second" },
      { roll: 28, name: "Alia Parveen", math: 59, sci: 32, sst: 40, eng: 46, hindi: 81, total: 258, pct: "51.6%", result: "Second" },
      { roll: 29, name: "Sonam Kumari", math: 68, sci: 32, sst: 40, eng: 45, hindi: 43, total: 228, pct: "45.6%", result: "Second" },
      { roll: 30, name: "Sushma Kumari", math: 58, sci: 34, sst: 42, eng: 48, hindi: 45, total: 227, pct: "45.4%", result: "Second" },
      { roll: 31, name: "Aditya Kumar", math: 55, sci: 34, sst: 48, eng: 52, hindi: 40, total: 229, pct: "45.8%", result: "Second" },
      { roll: 32, name: "Avinash Kumar", math: 53, sci: 45, sst: 56, eng: 60, hindi: 62, total: 276, pct: "55.2%", result: "Second" },
      { roll: 33, name: "ganita Kumari", math: 52, sci: 37, sst: 56, eng: 58, hindi: 57, total: 260, pct: "52.0%", result: "Second" },
      { roll: 35, name: "ladli Kumari", math: 69, sci: 40, sst: 42, eng: 48, hindi: 50, total: 249, pct: "49.8%", result: "Second" },
      { roll: 36, name: "Rupam Kumari", math: 63, sci: 31, sst: 53, eng: 58, hindi: 50, total: 255, pct: "51.0%", result: "Second" },
      { roll: 37, name: "MD Arman", math: 43, sci: 34, sst: 52, eng: 55, hindi: 18, total: 202, pct: "40.4%", result: "Third" },
      { roll: 38, name: "Sujit Kumar", math: 54, sci: 32, sst: 45, eng: 50, hindi: 34, total: 215, pct: "43.0%", result: "Third" },
      { roll: 40, name: "sada Afreen", math: 53, sci: 32, sst: 48, eng: 52, hindi: 30, total: 215, pct: "43.0%", result: "Third" },
      { roll: 41, name: "Ruby Kumari", math: 53, sci: 34, sst: 42, eng: 56, hindi: 59, total: 244, pct: "48.8%", result: "Second" },
      { roll: 42, name: "Abda Parveen", math: 56, sci: 34, sst: 39, eng: 44, hindi: 63, total: 236, pct: "47.2%", result: "Second" },
      { roll: 43, name: "Draksha Praveen", math: 62, sci: 33, sst: 38, eng: 42, hindi: 61, total: 236, pct: "47.2%", result: "Second" },
      { roll: 44, name: "sakina Parveen", math: 48, sci: 48, sst: 40, eng: 45, hindi: 89, total: 270, pct: "54.0%", result: "Second" },
      { roll: 45, name: "shagufta naaj", math: 62, sci: 35, sst: 48, eng: 50, hindi: 50, total: 245, pct: "49.0%", result: "Second" },
      { roll: 46, name: "Aditya Kumar", math: 63, sci: 34, sst: 51, eng: 53, hindi: 62, total: 263, pct: "52.6%", result: "Second" }
    ];

    function verifyAndFetch() {
      const roll = parseInt(document.getElementById('rollInput').value);
      const userCaptcha = document.getElementById('captchaInput').value.trim().toUpperCase();
      const err = document.getElementById('errorAlert');
      const view = document.getElementById('marksheetView');

      if (!roll) {
        err.textContent = "कृपया छात्र का रोल नंबर दर्ज करें।";
        err.style.display = "block";
        view.style.display = "none";
        return;
      }

      if (!userCaptcha || userCaptcha !== activeCaptcha) {
        err.textContent = "अमान्य कैप्चा कोड! कृपया सही सुरक्षा कोड दर्ज करें।";
        err.style.display = "block";
        view.style.display = "none";
        refreshCaptcha();
        return;
      }

      const s = studentRecords.find(item => item.roll === roll);

      if (!s) {
        err.textContent = `रोल नंबर ${roll} का परीक्षा परिणाम डेटाबेस में नहीं मिला।`;
        err.style.display = "block";
        view.style.display = "none";
        return;
      }

      err.style.display = "none";

      // Fill Official Marksheet
      document.getElementById('dispName').textContent = s.name.toUpperCase();
      document.getElementById('dispRoll').textContent = s.roll;
      document.getElementById('mMath').textContent = s.math;
      document.getElementById('mSci').textContent = s.sci;
      document.getElementById('mSst').textContent = s.sst;
      document.getElementById('mEng').textContent = s.eng;
      document.getElementById('mHindi').textContent = s.hindi;

      // Remarks
      document.getElementById('rMath').textContent = s.math >= 75 ? 'Distinction' : (s.math >= 30 ? 'Passed' : 'Needs Imp.');
      document.getElementById('rSci').textContent = s.sci >= 75 ? 'Distinction' : (s.sci >= 30 ? 'Passed' : 'Needs Imp.');
      document.getElementById('rSst').textContent = s.sst >= 75 ? 'Distinction' : (s.sst >= 30 ? 'Passed' : 'Needs Imp.');
      document.getElementById('rEng').textContent = s.eng >= 75 ? 'Distinction' : (s.eng >= 30 ? 'Passed' : 'Needs Imp.');
      document.getElementById('rHindi').textContent = s.hindi >= 75 ? 'Distinction' : (s.hindi >= 30 ? 'Passed' : 'Needs Imp.');

      document.getElementById('mGrandTotal').textContent = `${s.total} / 500`;
      document.getElementById('mPercentage').textContent = s.pct;

      let badgeClass = s.result === 'First' ? 'badge-first' : (s.result === 'Second' ? 'badge-second' : 'badge-third');
      document.getElementById('mFinalDiv').innerHTML = `<span class="${badgeClass}">${s.result.toUpperCase()} DIVISION</span>`;

      view.style.display = "block";
      view.scrollIntoView({ behavior: 'smooth' });
    }

    function resetForm() {
      document.getElementById('rollInput').value = "";
      document.getElementById('captchaInput').value = "";
      document.getElementById('errorAlert').style.display = "none";
      document.getElementById('marksheetView').style.display = "none";
      refreshCaptcha();
    }

    window.onload = refreshCaptcha;
  </script>
</body>
</html>
