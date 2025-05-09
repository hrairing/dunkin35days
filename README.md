<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>AeroVolt – Locked Access</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap" rel="stylesheet"/>
  <style>
    /* ========== OVERLAY STYLES ========== */
    #login-overlay {
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
  background: rgba(0,0,0,0.95);
  display: flex;
  justify-content: center;
  align-items: flex-start;        /* push it toward top so you can scroll */
  overflow-y: auto;               /* enable vertical scrolling */
  padding: 2rem 0;                /* give a little breathing room */
  z-index: 9999;
}

.login-box {
  background: #111;
  padding: 2rem;
  border: 2px solid #f1c40f;
  border-radius: 12px;
  width: 90%;
  max-width: 420px;
  max-height: 90vh;               /* never exceed viewport height */
  overflow-y: auto;               /* scroll its contents if needed */
  text-align: center;
  font-family: 'Montserrat', sans-serif;
  color: #fff;
}

    .login-box h2 {
      margin-bottom: 1rem;
      font-size: 1.75rem;
      color: #f1c40f;
    }
    .login-box input {
      width: 100%;
      padding: 0.75rem;
      margin: 0.5rem 0;
      border: 1px solid #444;
      border-radius: 6px;
      background: #222;
      color: #fff;
      font-size: 1rem;
    }
    .login-box button,
    .login-box .pay-button {
      width: 100%;
      padding: 0.75rem;
      margin-top: 1rem;
      border: none;
      border-radius: 6px;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.2s ease-in-out;
    }
    .login-box button {
      background: #e74c3c;
      color: #fff;
    }
    .login-box button:hover {
      background: #c0392b;
    }
    .login-box .pay-button {
      background: #3498db;
      color: #fff;
      text-decoration: none;
      display: inline-block;
    }
    .login-box .pay-button:hover {
      background: #2980b9;
    }
    .login-box .detail {
      margin-top: 1rem;
      font-size: 0.9rem;
      opacity: 0.85;
    }
    .package-list-horizontal {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 0.5rem;
      margin-top: 1rem;
    }
    .package-item {
      background: #222;
      padding: 0.5rem 1rem;
      border: 1px solid #444;
      border-radius: 6px;
      font-size: 0.875rem;
    }
    /* ========== END OVERLAY STYLES ========== */
  </style>

  <style>
    /* ========== ORIGINAL AEROVOLT STYLES ========== */
    * { box-sizing: border-box; margin:0; padding:0; }
    body {
      font-family:'Montserrat',sans-serif;
      background:#111; color:#fff;
      margin:20px; border:2px solid orange;
      min-height:100vh;
    }
    .container { max-width:800px; margin:auto; padding:2rem; }
    .header h1 { font-size:2.5rem; margin-bottom:.5rem; }
    .header p { font-size:1rem; opacity:.85; margin-bottom:1.5rem; }
    h2.section-title {
      font-size:1.5rem; margin:2rem 0 1rem; color:#f1c40f;
    }
    .package-list { display:flex; flex-direction:column; gap:1rem; }
    .package {
      border:2px solid; border-radius:8px;
      padding:1rem; transition:.3s; cursor:pointer;
    }
    .package:hover {
      background:rgba(255,255,255,0.1);
      transform:translateY(-3px);
    }
    .title { font-weight:600; font-size:1.125rem; }
    .stats {
      font-size:.875rem; opacity:.8;
      margin-top:.25rem;
    }
    .package:nth-child(4n+1){ border-color:#27ae60; }
    .package:nth-child(4n+2){ border-color:#e74c3c; }
    .package:nth-child(4n+3){ border-color:#3498db; }
    .package:nth-child(4n+4){ border-color:#f1c40f; }
    .details {
      display:none; margin-top:.75rem;
      padding-top:.75rem; border-top:1px solid #444;
    }
    .buttons {
      display:flex; gap:.5rem; margin-bottom:.5rem;
    }
    .buttons button {
      background:#e74c3c; color:#fff;
      border:none; border-radius:4px;
      padding:.5rem 1rem; cursor:pointer;
      flex:1; min-width:100px;
      transition:opacity .2s;
    }
    .buttons button:hover { opacity:.8; }
    .content {
      background:#222; padding:1rem;
      border-radius:4px; white-space:pre-line;
    }
    .schedule-container {
      width:100%; height:400px;
      border:1px solid #fff; padding:1rem;
      border-radius:6px; background:#111;
      margin-top:.5rem; overflow-y:auto;
    }
    .schedule-grid {
      display:grid;
      grid-template-columns:repeat(3,1fr);
      gap:.75rem;
    }
    .day-square {
      height:60px; border:1px solid #fff;
      display:flex; align-items:center;
      justify-content:center; font-size:.875rem;
      cursor:pointer; border-radius:4px;
      transition:background .2s;
    }
    .day-square:hover { background:rgba(255,255,255,0.1); }
    .counter {
      text-align:center; margin-top:2rem;
    }
    .number {
      font-size:2rem; font-weight:600;
      border:2px solid #fff; padding:.5rem 1rem;
      border-radius:4px;
    }
    .counter p { opacity:.85; margin-top:.5rem; }
    /* ========== END ORIGINAL STYLES ========== */
  </style>
</head>
<body>

  <!-- ========== LOGIN OVERLAY ========== -->
  <div id="login-overlay">
    <div class="login-box">
      <h2>Access AeroVolt</h2>
      <input type="text" id="username" placeholder="Username" />
      <input type="password" id="password" placeholder="Password" />
      <button id="login-btn">Log In</button>
      <div class="detail">Unlock all <strong>10</strong> AeroVolt packs for just <strong>$99</strong>:</div>
      <div class="package-list-horizontal">
        <div class="package-item">50-Day Jumping Program</div>
        <div class="package-item">Elite Warm-Up Package</div>
        <div class="package-item">Jump Technique Breakdown</div>
        <div class="package-item">Core Stability System</div>
        <div class="package-item">In-Season Maintenance</div>
        <div class="package-item">Gain Height Stretching</div>
        <div class="package-item">Posterior Chain Plan</div>
        <div class="package-item">Recovery Protocol</div>
        <div class="package-item">Hip Mobility to Fly</div>
        <div class="package-item">Personal Guidance from Me</div>
      </div>
      <a href="https://www.paypal.me/wartiwarkasabian/99" target="_blank" class="pay-button">
        🔒 Unlock Now 💸
      </a>
    </div>
  </div>

  <script>
    // Login logic: password must match
    document.getElementById('login-btn').addEventListener('click', function() {
      const pwd = document.getElementById('password').value;
      if (pwd === 'jumpwithaerovolt') {
        document.getElementById('login-overlay').style.display = 'none';
      } else {
        alert('Wrong password. Purchase first to get access.');
      }
    });
  </script>
  <!-- ========== END LOGIN OVERLAY ========== -->


  <!-- ========== ORIGINAL AEROVOLT CONTENT ========== -->
  <div class="container">
    <header class="header">
      <h1>Welcome to AeroVolt!</h1>
      <p>🚀 Welcome to <strong>AeroVolt</strong> — the ultimate vertical jump system that’s transforming athletes worldwide.</p>
      <p>
        Personally crafted and tested on over <strong>600 athletes</strong>,
        <strong>AeroVolt</strong> delivers proven systems to skyrocket your vertical leap.
        I’m living proof — with a <strong>48.5"</strong> vertical achieved without a traditional PT —
        this program <strong>crushes the competition</strong>.
      </p>
      <p>
        ❌ No gimmicks. ❌ No recycled workouts. ❌ No expensive equipment. <br/>
        ✅ Just smart training, elite protocols, and a complete system built for real, explosive results.
      </p>
      <p>
        Inside <strong>AeroVolt</strong>, you’ll get:
        <ul>
          <li>🔹 The 50-Workout Jump Program to unlock raw vertical explosion</li>
          <li>🔹 Warm-Up & Recovery Plans for safe, consistent progress</li>
          <li>🔹 Gain Height with my proven 1000+ people stretching methods</li>
          <li>🔹 Hip Unlock & Mobility Flows to remove hidden jump blockers</li>
          <li>🔹 Technique Breakdowns based on real science and pro mechanics</li>
        </ul>
      </p>
      <p>
        Whether you're chasing your first dunk or trying to dominate your sport, this system adapts to YOU.
      </p>
      <p>
        <strong>AeroVolt</strong> is more than a program — it's a transformation engine. <br/>
        <strong>Train smart. Jump high. Become the athlete you were built to be.</strong>
      </p>
    </header>

    <h2 class="section-title">Main Packs to Dominate the Rim and Dunk</h2>
    <div class="package-list">
      <div class="package">
        <div class="title">50-Day Jumping Program</div>
        <div class="stats">✓ Completed by 877 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
      <div class="package">
        <div class="title">Elite Warm-Up Package</div>
        <div class="stats">✓ Completed by 732 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
      <div class="package">
        <div class="title">Jump Technique Breakdown</div>
        <div class="stats">✓ Completed by 523 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
      <div class="package">
        <div class="title">Core Stability System</div>
        <div class="stats">✓ Completed by 578 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
    </div>

    <h2 class="section-title">Additional Bonus Packs</h2>
    <div class="package-list">
      <div class="package">
        <div class="title">In-Season Jump Maintenance Plan</div>
        <div class="stats">✓ Completed by 689 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
      <div class="package">
        <div class="title">Gain Height with Stretching</div>
        <div class="stats">✓ Completed by 1095 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
      <div class="package">
        <div class="title">Posterior Chain Strength Plan</div>
        <div class="stats">✓ Completed by 612 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
      <div class="package">
        <div class="title">Recovery Protocol</div>
        <div class="stats">✓ Completed by 550 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
      <div class="package">
        <div class="title">Unlock Your Hips to Unlock Your Vertical</div>
        <div class="stats">✓ Completed by 489 people</div>
        <div class="details">
          <div class="buttons">
            <button data-type="overview">Overview</button>
            <button data-type="schedule">Schedule</button>
          </div>
          <div class="content"></div>
        </div>
      </div>
    </div>

    <div class="counter">
      <span class="number" id="counter">0</span>
      <p>People have joined AeroVolt so far</p>
    </div>
  </div>

  <script>
    // Counter animation
    const counterEl = document.getElementById('counter');
    let count = 0, target = 746, step = Math.ceil(target/100);
    (function anim() {
      count = Math.min(count + step, target);
      counterEl.textContent = count;
      if (count < target) setTimeout(anim, 20);
    })();

    // Overview texts
    const overviewTexts = {
      "50-Day Jumping Program":
       "• 🔥 The foundation of the AeroVolt system — 50 hyper-focused workouts engineered to maximize your vertical.\n\n• ✅ This is not a 50-day calendar — it's 50 workouts that adapt to your schedule, letting you train 2–3x/week with full flexibility.\n\n• 🏋️‍♂️ 100% bodyweight — no equipment needed. Built for home, gym, or outdoor grind.\n\n• 💥 Each session targets a unique combination of tendon elasticity, joint stiffness, CNS activation, and reactive force.\n\n• 📈 Athletes who complete all workouts consistently gain 20–30cm (7–12 inches) in vertical leap.\n\n• 🧠 Based on isometrics, eccentrics, and elastic training phases to build jump-specific athleticism.\n\n• 📅 Every workout can be scratched off for visual motivation. Watch yourself rise — literally.\n\n• 🏀 Whether you’re aiming to dunk, dominate volleyball, or just out-jump the competition — this program is your blueprint.",
      "Elite Warm-Up Package":
        "• 🔥 Instantly unlock 4–5 inches of vertical jump potential by doing what 90% of athletes ignore — proper warm-up.\n\n• ⚠️ If your legs feel heavy or slow when jumping, it’s usually not strength — it’s poor activation.\n\n• 🎯 This package ignites your nervous system, tendons, and jump mechanics BEFORE you train.\n\n• 📦 Includes 4 key flows:\n   - DAILY PREP FLOW: A fluid, no-excuse sequence to activate everything from ankles to shoulders.\n   - HIP & KNEE IGNITION: Joint-based circuits that prep elastic power zones.\n   - LOWER BODY SNAP: Targeted tendon work to make your legs feel spring-loaded.\n   - GAME-READY PRIMER: A condensed activation for pickup games or dunk sessions.\n\n• 🕒 Each sequence is 6–10 minutes max.\n\n• ✅ You’ll feel lighter, faster, and bouncier before even touching the court.",
      "Jump Technique Breakdown":
        "• ⚡ Strength means nothing if your jump form is broken. This breakdown teaches the movement secrets elite jumpers know — and most athletes ignore.\n\n• 🚫 Stop losing inches to poor mechanics. Fix your penultimate step and your jump transforms instantly.\n\n• 📉 80% of vertical loss happens during the 3 steps leading into your jump — not during takeoff.\n\n• 🎯 Learn:\n   - How to use the penultimate step to load your legs like a spring.\n   - Correct body lean, arm motion, and hip-timing.\n   - Mistakes that kill momentum — and how to fix them fast.\n\n• 🎥 Visual learners? Every angle is broken down in video so you can mirror perfect technique.\n\n• ✅ Whether you’re a one-foot or two-foot jumper, this gives you technical inches without adding weight or training time.",
      "Core Stability System":
        "• 🧱 Your core is your engine room. Without it, your legs can't transfer power — and your jump suffers.\n\n• 🔥 This program builds deep, functional core strength that keeps you stable, explosive, and injury-free.\n\n• 📦 Includes high-performance movements like:\n   - Anti-rotation planks\n   - Hip-to-rib coordination drills\n   - Deep abdominal activation\n\n• 🧠 We’re not doing crunches. These are strength patterns used by elite sprinters and dunkers.\n\n• 🕒 Each session is just 10–15 minutes and designed to be added after any workout.\n\n• ✅ Results? Cleaner takeoffs. Mid-air balance. Better landings. Real athleticism.",
      "In-Season Jump Maintenance Plan":
        "• 📦 Built for the grind of in-season performance — where you can’t afford to lose your hard-earned bounce.\n\n• 🏀 This is your weekly checklist to KEEP your vertical active while staying fresh for games.\n\n• 📌 Includes:\n   - 1–2 weekly jump sessions (short & explosive, not fatiguing).\n   - 3–4 sprint drills to keep CNS sharp.\n   - Tendon-friendly isometric holds (wall sits, lunge freezes, calf pulses).\n   - Mini core & hip flows (5–8 mins) to maintain stability.\n\n• 🧠 Bonus strategies include: Bounce tracking, mental reps, hydration habits, sleep optimization.\n\n• ✅ Precision over grind. Stay sharp while others plateau.",
      "Gain Height with Stretching":
        "• 📏 Stretch to grow? YES — if you do it right.\n\n• 🧠 Your spine compresses from sitting, jumping, lifting — and it’s costing you 1–3 cm of height (sometimes more).\n\n• 🚀 This daily plan helps you decompress, realign, and optimize posture for taller standing height and more efficient jumping.\n\n• 📦 You’ll learn:\n   - Spinal decompression drills (daily 8–10 mins).\n   - Hip & pelvic alignment flows to fix your base.\n   - Neck & shoulder mobility to open posture fully.\n   - Breathing patterns that help decompress your spine naturally.\n\n• 🛌 Most effective when done after waking or before sleep.\n\n• ✅ Looks better. Feels better. Moves better. Gain vertical AND height.",
      "Posterior Chain Strength Plan":
        "• 💣 You can't launch forward if your backside is weak. This plan powers up the glutes, hamstrings, and calves — the true engines of vertical jump.\n\n• 🦵 A strong posterior chain gives you stiffness, snap, and joint protection.\n\n• 📦 Includes elite-level bodyweight work like:\n   - Hamstring sliders & bridge variations.\n   - Calf pop-up drills and isometric holds.\n   - Glute medius activation and hip thrusts.\n\n• ✅ Built for home — no equipment needed.\n\n• 🏋️‍♂️ Use 2–3x/week as a standalone power module or add to your jump days.\n\n• 💥 Expect stronger takeoffs, reduced knee stress, and more control mid-air.",
      "Recovery Protocol":
        "• 🛡️ This is the most important package in AeroVolt. Why? Because you don’t grow from training — you grow from RECOVERY.\n\n• ❗ Without recovery, your nervous system crashes. Your joints stiffen. Your gains disappear.\n\n• 📦 You’ll learn how to recover like a pro athlete:\n   - Post-session cooldown flows to reset tension.\n   - Deep tendon therapy for knees, hips, and ankles.\n   - Mobility routines that unlock tight areas from training.\n   - Sleep + hydration systems to build muscle while resting.\n   - Ice, heat, and contrast protocols to kill soreness.\n\n• ✅ Recovery is a habit — not a luxury. Master it.",
      "Unlock Your Hips to Unlock Your Vertical":
        "• 🌀 No matter how strong your legs are, tight hips are limiting your bounce.\n\n• 🔓 This package is the secret weapon used by Kadour Ziani — the man with a 60” vertical.\n\n• 📦 Inside:\n   - Deep hip mobility sequences.\n   - Isometric glute and psoas activations.\n   - Rotational power drills to unlock hidden range.\n   - Daily rituals to improve hip posture and flexibility.\n\n• 🧘‍♂️ Use it as warm-up, cooldown, or standalone mobility work.\n\n• ✅ Most athletes feel 10x more fluid within days. Open your hips — and fly."
    };

    document.querySelectorAll(".package").forEach(pkg => {
      const details = pkg.querySelector(".details");
      const content = pkg.querySelector(".content");
      const title   = pkg.querySelector(".title").textContent.trim();

      pkg.addEventListener("click", () => {
        details.style.display =
          details.style.display === "block" ? "none" : "block";
      });

      pkg.querySelectorAll("button").forEach(btn => {
        btn.addEventListener("click", e => {
          e.stopPropagation();
          details.style.display = "block";

          if (btn.dataset.type === "overview") {
            content.textContent = overviewTexts[title] || "";
          } else {
            let vid;
            switch (title) {
              case "In-Season Jump Maintenance Plan":       vid = "10238942598"; break;
              case "Jump Technique Breakdown":               vid = "1025286378"; break;
              case "Gain Height with Stretching":            vid = "1025286916"; break;
              case "Recovery Protocol":                      vid = "1025286916"; break;
              case "Posterior Chain Strength Plan":          vid = "10589845612"; break;
              case "Unlock Your Hips to Unlock Your Vertical":
              case "Core Stability System":                  vid = "10598449425"; break;
              case "Elite Warm-Up Package":                  vid = "10598449550"; break;
              default:                                      vid = null;
            }
            if (vid) {
              content.innerHTML = `
                <div class="schedule-container" style="display:flex;justify-content:center;align-items:center;height:400px;">
                  <iframe
                    src="https://player.vimeo.com/video/${vid}"
                    style="width:100%;height:100%;border:none;border-radius:5px;"
                    allow="autoplay; fullscreen; picture-in-picture"
                    allowfullscreen>
                  </iframe>
                </div>`;
            } else {
              const days = title.includes("50-Day") ? 50 : 30;
              let html = '<div class="schedule-container"><div class="schedule-grid">';
              for (let d = 1; d <= days; d++) {
                html += `<div class="day-square" data-day="${d}">Day ${d}</div>`;
              }
              html += '</div></div>';
              content.innerHTML = html;
              content.querySelectorAll(".day-square").forEach(el =>
  el.addEventListener("click", ev => {
    const day = el.dataset.day;

    if (day === '1') {
      content.innerHTML = `
        <div class="cycle">
          <h3>1. Depth Jumps (3 × 5 reps)</h3>
          <iframe
            src="https://player.vimeo.com/video/1025264414"
            title="Depth Jumps"
            style="width:100%;height:300px;border:none;border-radius:5px;">
          </iframe>
          <p><strong>Description:</strong> Stand on a 12–18″ box. Step off, land softly, then explode straight up—minimize ground contact to train your stretch-shortening cycle.</p>
          <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, Achilles tendon.</p>
          <p><strong>Impact:</strong> 9/10</p>
        </div>
        <div class="cycle">
  <h3>2. split jumps × sprints (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286652" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. single-leg box jumps (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102527245298" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.lateral hurdles into lateral bounds(3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635387" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;
    }
    else if (day === '2') {
      content.innerHTML = `
        <div class="cycle">
          <h3>1. Tuck Jumps (3 × 5 reps)</h3>
          <iframe 
            src="https://player.vimeo.com/video/1025274226" 
            title="Tuck Jumps" 
            style="width:100%; height:300px; border:none; border-radius:5px;">
          </iframe>
          <p><strong>Description:</strong> From standing, explode straight up, tucking your knees to your chest at the peak, then land softly with bent knees. Emphasize rapid knee drive and minimal ground contact.</p>
          <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hip flexors, calves, and core stabilizers.</p>
          <p><strong>Goal:</strong> Enhance reactive force, core-to-leg sequencing, and maximum vertical height.</p>
          <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 9/10</p>
        </div>
        <div class="cycle">
          <h3>2. Lateral Bounds (3 × 8 reps)</h3>
          <iframe 
            src="https://player.vimeo.com/video/1025274630" 
            title="Lateral Bounds" 
            style="width:100%; height:300px; border:none; border-radius:5px;">
          </iframe>
          <p><strong>Description:</strong> Bound explosively side-to-side over an imaginary line, landing on one leg with a soft knee bend, then immediately rebound back. Control your landing and use arm swing for momentum.</p>
          <p><strong>Muscles Worked:</strong> Glute medius, hip abductors/adductors, quadriceps, and calves.</p>
          <p><strong>Goal:</strong> Develop lateral explosiveness, hip stability, and single-leg power transfer.</p>
          <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
        </div>
        <div class="cycle">
          <h3>3. Single-Leg Butt Kicks (3 × 5 reps each leg)</h3>
          <iframe 
            src="https://player.vimeo.com/video/1025275298" 
            title="Single-Leg Butt Kicks" 
            style="width:100%; height:300px; border:none; border-radius:5px;">
          </iframe>
          <p><strong>Description:</strong> Stand on one leg and perform quick heel-to-glute kicking motions with the opposite leg, landing softly and immediately repeating. Switch legs after completing the set.</p>
          <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, and hip flexors.</p>
          <p><strong>Goal:</strong> Improve hamstring elasticity, knee flexion speed, and unilateral leg power.</p>
          <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
        </div>
        <div class="cycle">
          <h3>4. Single-Leg Tuck Outs (3 × 6 reps each leg)</h3>
          <iframe 
            src="https://player.vimeo.com/video/1025278218" 
            title="Single-Leg Tuck Outs" 
            style="width:100%; height:300px; border:none; border-radius:5px;">
          </iframe>
          <p><strong>Description:</strong> Jump up on one leg, drive the knee toward your chest mid-air, then land softly on the same leg and immediately repeat. Switch legs after each set.</p>
          <p><strong>Muscles Worked:</strong> Quadriceps, hip flexors, glutes, core stabilizers, and calves.</p>
          <p><strong>Goal:</strong> Build unilateral explosive strength, coordination, and core-to-leg power for sport-specific movements.</p>
          <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
        </div>`;
    } 
    else if (day === '3') {
                  // Day 3 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Sprints x Broad Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278512" 
    title="Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Begin with an explosive 10–15 meter sprint to build momentum, then immediately transition into a maximal effort broad jump off two feet. Stick the landing with control. Emphasize powerful hip extension during the jump and full acceleration during the sprint. Reset and repeat.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quadriceps, calves, hip flexors, and core.</p>
  <p><strong>Goal:</strong> Build explosive horizontal power, improve sprint-to-jump transition, and enhance speed-strength for real-world athletic movements.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Seated Squat Jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start seated on a box or bench with your knees at 90 degrees. Keep your chest tall and hands in front. Without using momentum or rocking, explode straight up into a vertical jump. Land softly, reset fully between reps, and repeat. Focus on maximal force from a static position.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, and core stabilizers.</p>
  <p><strong>Goal:</strong> To build raw concentric strength and acceleration from a dead stop. This enhances vertical jump by training explosive force without a pre-stretch.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>3. Kneeling Jumps into High Knees(3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video.1025283600" 
    title="Kneeling Jumps into High Knees" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Start on your knees with your torso upright. Explode upward to your feet using hip thrust and swing, immediately transitioning into 3–5 fast, high-knee sprints in place. Focus on landing softly and keeping rapid, explosive knee drive after the jump.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hip flexors, quadriceps, hamstrings, calves, and core.</p>
  <p><strong>Goal:</strong> Build explosive hip extension, reactive power, and high-speed coordination. Great for transitioning ground power into sprint-phase leg action.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7/10</p>
  </div>
<div class="cycle">
  <h3>4. Mini Steps into Squat Jumps (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025284525" 
    title="Mini Steps into Squat Jumps " 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start with 3–4 fast, shallow steps in place (mini steps) to activate your nervous system, then immediately drop into a deep squat and explode into a vertical jump. Land softly and repeat. Focus on maintaining rhythm and maximum lift after the steps.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, and core.</p>
  <p><strong>Goal:</strong>Train explosive transition from quick foot activity to powerful vertical force. Enhances reactivity, rhythm, and jump efficiency off rapid movement.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>`;
}
else if (day === '4') {
                  // Day 4 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Sprints x Broad Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278512" 
    title="Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Begin with an explosive 10–15 meter sprint to build momentum, then immediately transition into a maximal effort broad jump off two feet. Stick the landing with control. Emphasize powerful hip extension during the jump and full acceleration during the sprint. Reset and repeat.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quadriceps, calves, hip flexors, and core.</p>
  <p><strong>Goal:</strong> Build explosive horizontal power, improve sprint-to-jump transition, and enhance speed-strength for real-world athletic movements.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Seated Squat Jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="Seated squat jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Sit on a bench or box with knees bent at 90 degrees. Without using any momentum, explode straight up into a vertical jump. Land under control and return to the seated position for the next rep. Emphasize maximum force from a dead stop.</p>
  <p><strong>Muscles Worked:</strong> Glutes, quadriceps, hamstrings, calves, and core.</p>
  <p><strong>Goal:</strong> Develop raw concentric power and acceleration from a static position — crucial for improving vertical takeoff without a counter-movement.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>3. Single-Leg Butt Kicks (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025275298" 
    title="Single-Leg Butt Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and perform quick heel-to-glute kicking motions with the opposite leg, landing softly and immediately repeating. Switch legs after completing the set.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, and hip flexors.</p>
  <p><strong>Goal:</strong> Improve hamstring elasticity, knee flexion speed, and unilateral leg power.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 9/10</p>
  </div>
<div class="cycle">
  <h3>4. Single-Leg Tuck Outs (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278218" 
    title="Single-Leg Tuck Outs" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump up on one leg, drive the knee toward your chest mid-air, then land softly on the same leg and immediately repeat. Switch legs after each set.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, hip flexors, glutes, core stabilizers, and calves.</p>
  <p><strong>Goal:</strong> Build unilateral explosive strength, coordination, and core-to-leg power for sport-specific movements.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>`;
}  else if (day === '5') {
                  // Day 5 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Drops into Tuck Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. split jumps × sprints (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286652" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. single-leg box jumps (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102527245298" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.lateral hurdles into lateral bounds(3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635387" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '6') {
                  // Day 6 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Seated squat jumps into foot fire (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027634965" 
    title="Seated squat jumps into foot fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Lateral bound into a tuck jump (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635616" 
    title="Lateral bound into a tuck jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. Kneeling broad jumps into foot fire (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283869" 
    title="Kneeling broad jumps into foot fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.lateral hurdles into lateral bounds(3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635387" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '7') {
                  // Day 7 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Kneeling tuck jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025279450" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Single leg butt kick into Squat jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025279791" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. Kneeling lateral hurdles (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286459" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.Slingshot kicks (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '8') {
                  // Day 8 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Kneeling one leg surge(3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844810" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Toe coil tuck(3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845612" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. Lateral hurdle into lateral bound (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635387" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.Sprints into squat jumps(3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025285759" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '9') {
                  // Day 5 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Kneeling broad jumps into foot fire (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283869" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Seated squat jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. Tornado tucks(3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/10598444258" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.Snap twitch tuck (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '10') {
                  // Day 5 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Vortex kick ups (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/vimeo/1059845936" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. split jumps × sprints (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286652" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. Full power broad jumps (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635928" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.Mini steps into squat jumps (3 × 6 reps each leg)</h3>
  <iframe  
    src="https://player.vimeo.com/video/1025284525" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '11') {
                  // Day 5 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Drops into Tuck Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Kneeling lateral bounds (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025285979" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. Depth broad jumps (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635757" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.lateral hurdles into lateral bounds(3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635387" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '12') {
                  // Day 5 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Kneeling tendon snap kicks (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059846136" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Meteor tuck blast (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. single-leg box jumps (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102527245298" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4.Depth jump into sprints (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635519" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '13') {
                  // Day 5 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Shockwave toe reach (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Step off a low platform (12–18 inches), land softly with bent knees, and immediately explode into a vertical tuck jump by pulling both knees to the chest mid-air. Focus on fast ground contact and maximum lift.</p>
  <p><strong>Muscles Worked:</strong>Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive strength, reduce ground contact time, and build elastic power essential for explosive vertical takeoff.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 10/10</p>
  </div>
<div class="cycle">
  <h3>2. Tornado tuck (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/vimeo/1059844425" 
    title="split jumps × sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Start in a lunge position and perform 3–4 explosive alternating split jumps. Immediately transition into a short, max-effort sprint (10–15 meters). Focus on explosive leg switch during jumps and full speed during the sprint phase.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, hip flexors, core.</p>
  <p><strong>Goal:</strong>Combine vertical power with sprint acceleration. Builds explosive transition from vertical to horizontal force — essential for real-game jump and sprint demands.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8/10</p>
  </div>
<div class="cycle">
  <h3>3. Kneeling tendon snap kicks (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059846136" 
    title="single-leg box jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong>Stand on one leg and explode upward onto a low, stable platform or box. Stick the landing with control and balance. Focus on vertical height and stability.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, hamstrings, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance unilateral explosiveness, balance, and coordination — helping translate single-leg power into vertical jump height.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 8.5/10</p>
  </div>
<div class="cycle">
  <h3>4. Maximum effort jumps (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025285561" 
    title="lateral hurdles into lateral bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 2–3 quick lateral hurdle hops over low hurdles (or imagined ones), staying light and reactive on your feet. On the final hop, explode into a single large lateral bound off one leg, landing with balance and control. Focus on speed during the hurdles and maximum distance on the bound.</p>
  <p><strong>Muscles Worked:</strong>Glutes (especially glute medius), hip abductors/adductors, quadriceps, hamstrings, calves, core, ankle stabilizers.</p>
  <p><strong>Goal:</strong> Enhance lateral force absorption and redirection into horizontal explosiveness. Builds coordination, hip control, and elastic energy transfer — indirectly boosts vertical jump by strengthening lateral loading patterns and joint support.</p>
 <p><strong style="color: red;">How much this exercise can improve your vertical jump:</strong> 7.5/10</p>
  </div>`;

                }
                else if (day === '14') {
                  // Day 14 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Kneeling Tendon Snap Kicks (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059846136" 
    title="Kneeling Tendon Snap Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From a kneeling position, snap your front leg forward explosively, driving through the tendon. Land softly back on your knees and repeat on the same side before switching.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, hamstrings, hip flexors, Achilles tendon.</p>
  <p><strong>Goal:</strong> Prime tendon recoil and reactive power for maximal vertical spring.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.5/10</p>
</div>
<div class="cycle">
  <h3>2. Vortex Kick Ups (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Vortex Kick Ups" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Execute continuous high kick-ups in a circular “vortex” motion, driving heels towards glutes and using momentum to flip legs forward.</p>
  <p><strong>Muscles Worked:</strong> Calves, quadriceps, glutes, core stabilizers.</p>
  <p><strong>Goal:</strong> Develop dynamic calf-to‐hip chain coordination for richer elastic energy transfer.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.5/10</p>
</div>
<div class="cycle">
  <h3>3. Squat Jump into Foot Fire (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027634965" 
    title="Seated Squat Jumps into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform a squat jump, land softly, then immediately execute rapid feet-fire hops in place before the next rep.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Boost transition speed from explosive jump to rapid foot turnover.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>4. Slingshot Kicks (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Propel your leg forward in a slingshot motion, snapping the heel down aggressively, then immediately switch and repeat on the opposite side.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Amplify rapid leg snap and improve explosive hip drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>`;
                }
                else if (day === '15') {
                  // Day 15 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Shockwave Toe Reach (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From standing, jump up and reach to touch your toes mid-air, landing softly with full hip extension before repeating.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Combine vertical power with trunk-to-leg coordination for higher peak reach.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>2. Depth Drops into Tuck Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop off a box, land softly, then immediately explode into a tuck jump, tucking knees to chest at peak.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Train stress-absorb-explode sequence for maximal rebound height.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.7/10</p>
</div>
<div class="cycle">
  <h3>3. Lateral Bound into Tuck Jump (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635616" 
    title="Lateral Bound into Tuck Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Bound laterally off one leg, land softly, then transition immediately into a tuck jump.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, quads, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Merge lateral spring with vertical knee drive for multi‐vector power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Single-Leg Tuck Outs (3 × 7 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278218" 
    title="Single-Leg Tuck Outs" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump on one leg, tuck knee to chest, land softly, repeat before switching legs.</p>
  <p><strong>Muscles Worked:</strong> Quads, hip flexors, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Refine unilateral drive and landing control under fatigue.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.4/10</p>
</div>`;
                }
                else if (day === '16') {
                  // Day 16 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Squat Jump into Foot Fire (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027634965" 
    title="Squat Jump into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform a squat jump, then immediately execute rapid alternating foot hops in place before the next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Enhance reactive jump-to-hop transition speed.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Broad Jumps into Foot Fire (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283869" 
    title="Kneeling Broad Jumps into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, explode into a broad jump, then perform rapid foot-fire hops on landing.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Combine horizontal explosiveness with reactive foot speed.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>3. Vortex Kick Ups (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Vortex Kick Ups" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Continuous circular kick-ups to prime calf-to-hip elastic chain.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, glutes, core.</p>
  <p><strong>Goal:</strong> Maximize lower-leg reactive rebound under volume.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.3/10</p>
</div>
<div class="cycle">
  <h3>4. Slingshot Kicks (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Aggressively snap your leg in a slingshot motion, alternating sides each rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Boost explosive hip snap for higher take-off.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>`;
                }
                else if (day === '17') {
                  // Day 17 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Shockwave Toe Reach (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and reach for toes mid-air, emphasizing full extension and torso-to-leg coordination.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Integrate full-body extension for peak reach.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.4/10</p>
</div>
<div class="cycle">
  <h3>2. Vortex Kick ups (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Squat Jump into Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Combine a squat jump with a toe reach at peak for maximum triple-load extension.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, hamstrings, core.</p>
  <p><strong>Goal:</strong> Amplify concentric power transfer through full-body chain.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.8/10</p>
</div>
<div class="cycle">
  <h3>3. Lateral Bound into Tuck Jump (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635616" 
    title="Lateral Bound into Tuck Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Bound laterally, land softly, then explode straight into a tuck jump.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, quads, calves, core.</p>
  <p><strong>Goal:</strong> Merge lateral and vertical power under higher intensity.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>4. Single-Leg Tuck Outs (3 × 8 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278218" 
    title="Single-Leg Tuck Outs" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> One-leg jumps with knee tuck at top, alternating legs per set.</p>
  <p><strong>Muscles Worked:</strong> Quads, hip flexors, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build advanced unilateral explosiveness and neuromuscular control.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>`;
                }
                else if (day === '18') {
                  // Day 18 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Squat Jump into Foot Fire (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027634965" 
    title="Squat Jump into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Squat jump followed by rapid alternating foot hops before next rep.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Sharpen jump-to-agility transition under volume.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>2. Vortex Kick Ups (3 × 10 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Vortex Kick Ups" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Continuous full-range circular kick motion for calf-to-hip activation.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, glutes, core.</p>
  <p><strong>Goal:</strong> Maximize elastic chain performance.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>3. Shockwave Toe Reach (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump+toe touch combo emphasizing full extension.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Integrate explosive reach into vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.4/10</p>
</div>
<div class="cycle">
  <h3>4. Slingshot Kicks (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Explosive leg snap alternating sides rapidly for reactive hip drive.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Heighten hip snap for superior take-off velocity.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '19') {
                  // Day 19 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From a standing start, perform a maximal broad jump, landing softly with bent knees. Focus on full hip extension and rebounding forward.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, quadriceps, calves, core.</p>
  <p><strong>Goal:</strong> Build horizontal power to translate into vertical explosiveness.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling One-Leg Surge (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844810" 
    title="Kneeling One-Leg Surge" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> On one knee, explosively drive the opposite shin up until thigh is parallel to floor. Land back on knee and repeat before switching sides.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quadriceps, glutes, core stabilizers.</p>
  <p><strong>Goal:</strong> Prime hip flexor–quad chain for rapid knee drive in jump.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>3. Toe Coil Tuck (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845612" 
    title="Toe Coil Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump up, coil toes toward shins mid-air, then tuck both knees to chest before landing softly.</p>
  <p><strong>Muscles Worked:</strong> Calves, hip flexors, core, quadriceps.</p>
  <p><strong>Goal:</strong> Enhance calf-to-hip elastic chain and core-to-leg sequencing.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Snap Twitch Tuck (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="Snap Twitch Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump off one leg and rapidly tuck that knee to chest, landing back on the same leg. Alternate legs per set.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, hip flexors, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Develop unilateral reactive power and coordination.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>`;
                }
                else if (day === '20') {
                  // Day 20 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title=" Depth Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Stand off a box facing backward, step down, then reverse-rotate to land forward into a vertical jump.</p>
  <p><strong>Muscles Worked:</strong> Glutes, quadriceps, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Challenge coordination and eccentric control for improved rebound.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Tornado Tuck (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844425" 
    title="Tornado Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump up, rotate 180° mid-air while tucking knees, land facing opposite direction.</p>
  <p><strong>Muscles Worked:</strong> Core, hip flexors, quadriceps, glutes, calves.</p>
  <p><strong>Goal:</strong> Build rotational power and hip drive under plyo stress.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Lateral Bounds (3 × 6 reps each side)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286459" 
    title="Kneeling Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From a kneeling stance, bound laterally onto feet, land softly, return to kneeling for next rep.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, hip abductors, quadriceps, calves, core.</p>
  <p><strong>Goal:</strong> Train lateral spring and tendon snap under unconventional posture.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.4/10</p>
</div>
<div class="cycle">
  <h3>4. Meteor Blast (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump as high as possible, throw arms overhead violently like a meteor, and land softly on balls of feet.</p>
  <p><strong>Muscles Worked:</strong> Shoulders, core, glutes, calves, quadriceps.</p>
  <p><strong>Goal:</strong> Integrate full-body drive into vertical lift.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>`;
                }
                else if (day === '21') {
                  // Day 21 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Step-Up Jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278512" 
    title="Depth Step-Up Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, land with one foot on box, then explode upward into a two-foot jump.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Combine eccentric loading with concentric drive for powerful rebound.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Hurdles (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025265470" 
    title="Kneeling Hurdles" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, bound over low hurdles using only hip drive and arm swing.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Amplify hip snap under compromised base for jump carryover.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.5/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283869" 
    title="Kneeling Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From a kneeling position, explode forward into a broad jump, land softly and reset on knees.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Develop horizontal reactive power from unconventional posture.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>
<div class="cycle">
  <h3>4. Depth Drop to Squat Jump (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Drop to Squat Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop off a box, land softly into a squat, then immediately explode into a vertical jump.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Challenge rapid transition from eccentric to concentric power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>`;
                }
                else if (day === '22') {
                  // Day 22 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Tuck Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, then explode into a tuck jump, pulling knees to chest at peak.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Maximize reactive shortening cycle for peak height.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.4/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Tuck Jumps (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025267994" 
    title="Kneeling Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, explode to feet and tuck knees, land softly, return to knees.</p>
  <p><strong>Muscles Worked:</strong> Hip extensors, quads, core, calves.</p>
  <p><strong>Goal:</strong> Refine knee-tuck explosiveness under varied posture.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Squat Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844810" 
    title="Kneeling Squat Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, drop to feet in squat then immediately jump vertically, land softly and reset.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Train rapid squat-to-jump conversion for maximal takeoff.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Shockwave Toe Reach (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump high and reach for toes mid-air, land softly with full hip extension.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Integrate full-body extension into vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>`;
                }
                else if (day === '23') {
                  // Day 23 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Multi-Level Depth Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Multi-Level Depth Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform depth jumps off progressively higher boxes (12, 16, 20") in sequence, minimizing ground contact.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Gradually overload stretch-shortening cycle for maximal reactive strength.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.5/10</p>
</div>
<div class="cycle">
  <h3>2. Split Jump into Meteor Blast (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Split Jump into Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From lunge, explode into a split jump, land, then immediately perform a Meteor Blast overhead.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, shoulders, core.</p>
  <p><strong>Goal:</strong> Fuse lower-body explosion with full-body extension.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>3. Snap Switch Tuck (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="Snap Switch Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump off one leg, switch mid-air to land on the other, while tucking the knee to chest.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, calves, core.</p>
  <p><strong>Goal:</strong> Train fast unilateral switching and knee drive for dynamic takeoff.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Depth Plyo Burst (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="Depth Plyo Burst" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop from box, land, then immediately perform three quick squat jumps in place before next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build rapid-fire reactive sequence under fatigue.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>`;
                }
                else if (day === '24') {
                  // Day 24 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Box Plyos (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Box Plyos" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From ground, jump onto a box, step down, and immediately repeat.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Combine concentric and eccentric overload for vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.4/10</p>
</div>
<div class="cycle">
  <h3>2. Toe Coil Tuck into Squat Jump (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845612" 
    title="Toe Coil Tuck into Squat Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform a Toe Coil Tuck then land into immediate deep squat jump.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, glutes, core.</p>
  <p><strong>Goal:</strong> Fuse calf recoil with raw squat power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Tendon Snap Kicks (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059846136" 
    title="Kneeling Tendon Snap Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Snap kicks from kneeling—drive heel down with max tendon recoil.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, hamstrings, Achilles tendon, core.</p>
  <p><strong>Goal:</strong> Sharpen tendon-driven spring for takeoff.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>4. Tornado Tuck into Lateral Bound (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844425" 
    title="Tornado Tuck into Lateral Bound" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform a Tornado Tuck, land, then immediately bound laterally off either leg.</p>
  <p><strong>Muscles Worked:</strong> Core, glutes, quads, calves, hip abductors.</p>
  <p><strong>Goal:</strong> Combine rotational power with lateral explosiveness.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>`;
                }
                else if (day === '25') {
                  // Day 25 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Multi-Level Depth Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Multi-Level Depth Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform broad jumps off increasing heights (12→16→20") in sequence, focusing on maximal forward distance each rep.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, quads, calves, core.</p>
  <p><strong>Goal:</strong> Overload horizontal power and hip drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling One-Leg Surge into Foot Fire (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844810" 
    title="Kneeling One-Leg Surge into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> One-leg surge from kneeling, land on foot, then perform rapid foot-fire hops before switching.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, calves, core.</p>
  <p><strong>Goal:</strong> Merge single-leg tendon snap with rapid reactive footwork.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>3. Snap Twitch Tuck into Depth Drop (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="Snap Twitch Tuck into Depth Drop" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform Snap Twitch Tuck, land, then immediately drop off a low box into next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, hip flexors, calves, glutes, core.</p>
  <p><strong>Goal:</strong> Challenge reactive power both up and down.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>4. Meteor Blast into Tuck Jump (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Meteor Blast into Tuck Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Execute Meteor Blast, then immediately tuck knees mid-air on landing.</p>
  <p><strong>Muscles Worked:</strong> Shoulders, core, quads, glutes, calves.</p>
  <p><strong>Goal:</strong> Integrate explosive arm-drive with knee-tuck power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>`;
                }
                else if (day === '26') {
                  // Day 26 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Stand on a 12–18″ box, step off, land softly, then immediately explode into a vertical jump. Minimize ground contact time.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Build reactive lower-body power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>2. Lateral Hurdles (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025265470" 
    title="Lateral Hurdles" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Set up 6 hurdles and bound laterally over each, landing softly and rebounding immediately.</p>
  <p><strong>Muscles Worked:</strong> Glute medius/abductors, quads, calves, core.</p>
  <p><strong>Goal:</strong> Enhance lateral reactive strength and stability.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>
<div class="cycle">
  <h3>3. Slingshot Kicks (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Propel your leg forward explosively in a slingshot motion, alternating sides.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, hamstrings, calves.</p>
  <p><strong>Goal:</strong> Amplify hip snap and knee drive for higher takeoff.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Single-Leg Butt Kicks (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025275298" 
    title="Single-Leg Butt Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Stand on one leg and rapidly kick heel to glute, landing softly and repeating before switching.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Improve hamstring elasticity and knee drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.5/10</p>
</div>`;
                }
                else if (day === '27') {
                  // Day 27 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Seated Squat Jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="Seated Squat Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Sit at 90° on a bench, explode up without counter‐movement, land softly and reset.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Build raw concentric power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>2. Single-Leg Tuck Outs (3 × 7 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278218" 
    title="Single-Leg Tuck Outs" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump on one leg, tuck knee to chest, land softly on same leg, repeat before switching.</p>
  <p><strong>Muscles Worked:</strong> Quads, hip flexors, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Advance unilateral drive and control.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>3. Lateral Bounds (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025274630" 
    title="Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Bound side-to-side over an imaginary line, landing softly each rep.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, quads, calves, core.</p>
  <p><strong>Goal:</strong> Develop lateral power transfer.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>4. Kneeling Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025267994" 
    title="Kneeling Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, drive through hips and arms to explode up, land softly and return to knees.</p>
  <p><strong>Muscles Worked:</strong> Glutes, quads, core, calves.</p>
  <p><strong>Goal:</strong> Enhance hip extension power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>`;
                }
                else if (day === '28') {
                  // Day 28 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Sprints × Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278512" 
    title="Sprints × Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Sprint 10–15m, immediately transition into a maximal broad jump. Stick the landing.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quads, calves, core.</p>
  <p><strong>Goal:</strong> Fuse speed and jump power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>2. Split Jumps (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025266253" 
    title="Split Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From lunge, explode up and switch legs mid-air, landing softly.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Improve unilateral coordination under volume.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>3. Toe Coil Tuck (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845612" 
    title="Toe Coil Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump up, coil toes toward shins mid-air, then tuck knees before landing softly.</p>
  <p><strong>Muscles Worked:</strong> Calves, hip flexors, quads, core.</p>
  <p><strong>Goal:</strong> Prime elastic chain for optimal rebound.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>4. Depth Drops into Tuck Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a low box, land softly, immediately explode into a tuck jump.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Maximize reactive amplitude.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.5/10</p>
</div>`;
                }
                else if (day === '29') {
                  // Day 29 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Split Jumps × Sprints (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286652" 
    title="Split Jumps × Sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Alternate split jumps, then immediately sprint 10m at max effort.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Combine vertical and horizontal explosive power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>2. Single-Leg Box Jumps (3 × 5 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102527245298" 
    title="Single-Leg Box Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump onto a box using one leg, land softly, switch legs each set.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build unilateral stability and power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>3. Shockwave Toe Reach (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and reach for toes mid-air, emphasizing full-body extension.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Integrate trunk extension into vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>4. Kneeling One-Leg Surge (3 × 7 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844810" 
    title="Kneeling One-Leg Surge" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> On one knee, drive opposite thigh to parallel instantly, land softly and repeat.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, core.</p>
  <p><strong>Goal:</strong> Elevate hip drive speed under volume.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>`;
                }
                else if (day === '30') {
                  // Day 30 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Mini Steps into Squat Jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025284525" 
    title="Mini Steps into Squat Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 4 mini steps, then drop into a squat jump. Land softly and reset.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Train rapid transition from foot-speed to jump power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>2. Snap Twitch Tuck (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="Snap Twitch Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump off one leg, tuck knee to chest rapidly, land on same leg. Alternate legs per set.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, core.</p>
  <p><strong>Goal:</strong> Enhance unilateral reactive knee drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>3. Tornado Tuck (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844425" 
    title="Tornado Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Rotate 180° mid-air while tucking knees. Land softly and repeat.</p>
  <p><strong>Muscles Worked:</strong> Core, hip flexors, glutes, calves.</p>
  <p><strong>Goal:</strong> Train multi-vector explosive control.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Meteor Blast (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Explosively drive arms overhead like a meteor while jumping, then land softly.</p>
  <p><strong>Muscles Worked:</strong> Shoulders, core, quads, glutes.</p>
  <p><strong>Goal:</strong> Integrate upper-body drive with vertical lift.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '31') {
                  // Day 31 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Step-Up Jumps (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278512" 
    title="Depth Step-Up Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, land with one foot on box, then explode into a two-foot jump.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, core.</p>
  <p><strong>Goal:</strong> Blend eccentric loading with concentric spring.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Hurdles (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025265470" 
    title="Kneeling Hurdles" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, bound over low hurdles using hip snap and arm drive.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, glutes, core.</p>
  <p><strong>Goal:</strong> Challenge reactive hip extension.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>
<div class="cycle">
  <h3>3. Depth Plyo Burst (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635757" 
    title="Depth Plyo Burst" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop from box, land and immediately perform three squat jumps in place.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build rapid reactive sequences.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>4. Slingshot Kicks (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Explosive leg snap forward, alternating sides each rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Sharpen hip drive for jump.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>`;
                }
                else if (day === '32') {
                  // Day 32 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Box Plyos (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Box Plyos" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump onto box, step down, then repeat, focusing on soft landings.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Combine concentric and eccentric loads.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Vortex Kick Ups (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Vortex Kick Ups" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Continuous circular kick-ups to activate calf-hip chain.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, core.</p>
  <p><strong>Goal:</strong> Prime tendon recoil for spring.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283869" 
    title="Kneeling Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, explode forward into a broad jump and land softly on feet.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Train horizontal power from kneel.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Tuck Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025274226" 
    title="Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and pull knees to chest, land softly and repeat without pause.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hip flexors, core.</p>
  <p><strong>Goal:</strong> Enhance reactive vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '33') {
                  // Day 33 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Multi-Level Depth Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Multi-Level Depth Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop from increasing heights (12→16→20"), executing a vertical jump each time.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Overload stretch-shortening for peak reactive strength.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.5/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Lateral Bounds (3 × 6 reps each side)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286459" 
    title="Kneeling Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, bound laterally onto feet, land softly, return to knees.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, quads, calves, core.</p>
  <p><strong>Goal:</strong> Train lateral spring from kneel.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>
<div class="cycle">
  <h3>3. Split Jump into Meteor Blast (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Split Jump into Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From lunge, explode into split jump, then perform a Meteor Blast overhead.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, shoulders, core.</p>
  <p><strong>Goal:</strong> Combine lower-body explosion with full-body extension.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>4. Single-Leg Box Jumps (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102527245298" 
    title="Single-Leg Box Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump onto a box with one leg, land softly and switch legs next set.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Advance unilateral jump stability.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>`;
                }
                else if (day === '34') {
                  // Day 34 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Tuck Jumps (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, then explode into a tuck jump, pulling knees under chest.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, core, calves.</p>
  <p><strong>Goal:</strong> Maximize stretch-shortening amplitude.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.4/10</p>
</div>
<div class="cycle">
  <h3>2. Split Jumps × Sprints (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286652" 
    title="Split Jumps × Sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Alternate split jumps, then immediately sprint 10m at full speed.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Sync vertical output with horizontal acceleration.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>3. Shockwave Toe Reach (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and reach toes mid-air, land softly with full hip extension.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Integrate full-body extension into vertical drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>4. Slingshot Kicks (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Snap leg forward explosively, alternating sides for each rep.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, hamstrings, calves.</p>
  <p><strong>Goal:</strong> Heighten reactive hip snap.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>`;
                }
                else if (day === '35') {
                  // Day 35 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Squat Jumps (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Squat Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From a low squat position, explode straight up, focus on full hip extension, land softly, and reset immediately.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Build raw concentric power from a deep start.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Lateral Bounds (3 × 6 reps each side)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286459" 
    title="Kneeling Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, bound laterally off one leg, land softly, then return to kneeling before the next rep.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, hip abductors/adductors, calves, core.</p>
  <p><strong>Goal:</strong> Train lateral reactive power under an unstable base.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>
<div class="cycle">
  <h3>3. Tornado Tuck (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844425" 
    title="Tornado Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump, rotate 180° mid-air while tucking knees to chest, and land softly facing the opposite direction.</p>
  <p><strong>Muscles Worked:</strong> Core, hip flexors, quadriceps, glutes, calves.</p>
  <p><strong>Goal:</strong> Develop rotational explosiveness and control.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Meteor Blast (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Launch arms overhead like a meteor while jumping, then land softly with bent knees.</p>
  <p><strong>Muscles Worked:</strong> Shoulders, core, glutes, calves, quadriceps.</p>
  <p><strong>Goal:</strong> Integrate upper-body drive for maximal vertical thrust.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '36') {
                  // Day 36 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Kneeling Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283869" 
    title="Kneeling Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, explode forward into a broad jump, land softly on feet, then reset to knees.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Combine horizontal power with reactive landing.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>2. Shockwave Toe Reach (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump up and reach to touch your toes mid-air, then land softly with full hip extension.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Enhance trunk-to-leg coordination at peak height.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>3. Snap Switch Tuck (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="Snap Switch Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump off one leg and tuck that knee to chest, land on same leg. Alternate legs each set.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, hip flexors, calves, core.</p>
  <p><strong>Goal:</strong> Build unilateral reactive knee drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Depth Drop to Sprint (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635519" 
    title="Depth Drop to Sprint" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, land softly, then immediately sprint 10m as fast as possible.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quads, calves, core.</p>
  <p><strong>Goal:</strong> Fuse reactive jump with acceleration power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>`;
                }
                else if (day === '37') {
                  // Day 37 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Kneeling One-Leg Surge (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844810" 
    title="Kneeling One-Leg Surge" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> On one knee, drive the opposite thigh parallel to the floor explosively, then return to kneeling.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quadriceps, glutes, core.</p>
  <p><strong>Goal:</strong> Enhance hip flexor-tendon coordination for faster knee drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>2. Toe Coil Tuck into Squat Jump (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845612" 
    title="Toe Coil Tuck into Squat Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump up and coil toes toward shins, land into a deep squat, then explode back up.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, glutes, core.</p>
  <p><strong>Goal:</strong> Fuse elastic recoil with raw concentric power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>3. Vortex Kick Ups into Lateral Bounds (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Vortex Kick Ups into Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 8 vortex kick-ups, then bound laterally off one leg. Alternate sides each rep.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, glutes, hip abductors, core.</p>
  <p><strong>Goal:</strong> Develop multi-vector elastic power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Depth Plyo Burst (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="Depth Plyo Burst" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop from a box, land softly, then perform three rapid squat jumps in place before the next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build rapid reactive sequences under fatigue.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>`;
                }
                else if (day === '38') {
                  // Day 38 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Jumps into Foot Fire (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027634965" 
    title="Depth Jumps into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, land softly, then perform rapid alternating foot hops before next jump.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Enhance jump-to-agility transition.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Hurdles (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286459" 
    title="Kneeling Hurdles" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, bound over low hurdles using hip snap and arm drive.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, glutes, quads, core.</p>
  <p><strong>Goal:</strong> Amplify hip extension under unusual posture.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>3. Slingshot Kicks (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Explosively snap your leg forward, alternating sides, focusing on tendon recoil.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Sharpen hip snap for takeoff.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Squat Jump into Meteor Blast (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Squat Jump into Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform a squat jump, then at peak launch arms overhead like a meteor before landing softly.</p>
  <p><strong>Muscles Worked:</strong> Quads, shoulders, glutes, core.</p>
  <p><strong>Goal:</strong> Integrate upper-body drive with vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '39') {
                  // Day 39 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, then perform a maximal horizontal broad jump. Stick the landing.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, quads, calves, core.</p>
  <p><strong>Goal:</strong> Translate horizontal power gains into vertical improvements.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Tuck Jumps (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025267994" 
    title="Kneeling Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, explode to feet and tuck knees to chest, land softly, then return to kneeling.</p>
  <p><strong>Muscles Worked:</strong> Hip extensors, quads, calves, core.</p>
  <p><strong>Goal:</strong> Refine reactive hip extension and knee drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>3. Tornado Tuck (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844425" 
    title="Tornado Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and rotate 180° mid-air while tucking knees, land softly facing opposite way.</p>
  <p><strong>Muscles Worked:</strong> Core, hip flexors, glutes, calves.</p>
  <p><strong>Goal:</strong> Enhance multi-planar explosiveness.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Single-Leg Box Jumps (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102527245298" 
    title="Single-Leg Box Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump onto a box using one leg, land softly and switch legs next set.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build unilateral stability and power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>`;
                }
                else if (day === '40') {
                  // Day 40 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Drops into Lateral Bounds (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Drops into Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, land softly into a lateral bound, then reset on the box for next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, abductors, calves, core.</p>
  <p><strong>Goal:</strong> Merge vertical reactive drop with lateral spring.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling Tendon Snap Kicks (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059846136" 
    title="Kneeling Tendon Snap Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From kneeling, snap your leg forward with max tendon recoil. Land back on knees and repeat.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, hamstrings, Achilles tendon, core.</p>
  <p><strong>Goal:</strong> Sharpen reactive tendon-driven spring.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>3. Split Jump into Snap Twitch Tuck (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025274630" 
    title="Split Jump into Snap Twitch Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform a split jump, land, then immediately snap into a unilateral tuck on the opposite leg.</p>
  <p><strong>Muscles Worked:</strong> Quadriceps, glutes, hip flexors, core.</p>
  <p><strong>Goal:</strong> Combine unilateral power switch with explosive knee drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>4. Shockwave Toe Reach into Squat Jump (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach into Squat Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and touch toes mid-air, land into a deep squat and explode up again.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quads, core.</p>
  <p><strong>Goal:</strong> Integrate elastic reach with squat power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '41') {
                  // Day 41 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Drops into Tuck Jumps (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Drops into Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a low box, land softly, then immediately explode into a tuck jump, tucking knees to chest at peak.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Maximize reactive rebound height.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.5/10</p>
</div>
<div class="cycle">
  <h3>2. Squat Jump into Foot Fire (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027634965" 
    title="Squat Jump into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform a squat jump, land softly, then execute rapid alternating foot-fire hops before the next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Sharpen jump-to-agility transition.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Tendon Snap Kicks (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059846136" 
    title="Kneeling Tendon Snap Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From kneeling, snap the front leg forward explosively, driving through the tendon. Land back on knees and repeat.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, Achilles tendon, core.</p>
  <p><strong>Goal:</strong> Prime tendon recoil for superior takeoff.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>4. Shockwave Toe Reach (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump high, reach for your toes mid-air, then land softly with full hip extension.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Integrate trunk-to-leg coordination at peak.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>`;
                }
                else if (day === '42') {
                  // Day 42 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Multi-Level Depth Jumps (3 × 5 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Multi-Level Depth Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform depth jumps off progressively higher boxes (12", 16", 20") with minimal ground contact.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Overload stretch-shortening cycle for maximal reactive strength.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.5/10</p>
</div>
<div class="cycle">
  <h3>2. Tornado Tuck (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844425" 
    title="Tornado Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump up, rotate 180° mid-air while tucking knees, then land softly facing the opposite direction.</p>
  <p><strong>Muscles Worked:</strong> Core, hip flexors, glutes, calves.</p>
  <p><strong>Goal:</strong> Develop rotational power and control.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>3. Meteor Blast (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Launch arms overhead like a meteor while jumping, then land softly with bent knees.</p>
  <p><strong>Muscles Worked:</strong> Shoulders, core, glutes, calves.</p>
  <p><strong>Goal:</strong> Integrate upper-body drive with vertical thrust.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>4. Split Jumps × Sprints (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286652" 
    title="Split Jumps × Sprints" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform alternating split jumps, then immediately sprint 10m at max speed.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Combine vertical and horizontal power for game-specific explosiveness.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>`;
                }
                else if (day === '43') {
                  // Day 43 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Tuck Jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a low box, then explode into a tuck jump, tucking knees under chest.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Maximize reactive stretch-shortening cycle.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.4/10</p>
</div>
<div class="cycle">
  <h3>2. Lateral Bound into Tuck Jump (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635616" 
    title="Lateral Bound into Tuck Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Bound laterally off one leg, land softly, then transition immediately into a tuck jump.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, quads, calves, core.</p>
  <p><strong>Goal:</strong> Merge lateral spring with vertical drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>3. Single-Leg Box Jumps (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102527245298" 
    title="Single-Leg Box Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump onto a box using one leg, land softly and balance, then switch legs next set.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build unilateral stability and power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Vortex Kick Ups (3 × 10 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Vortex Kick Ups" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Execute continuous circular kick-ups to prime calf-to-hip elastic chain.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, glutes, core.</p>
  <p><strong>Goal:</strong> Maximize tendon-driven rebound under volume.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>`;
                }
                else if (day === '44') {
                  // Day 44 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Sprints × Broad Jumps (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278512" 
    title="Sprints × Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Sprint 10–15m, then immediately perform a maximal broad jump. Stick the landing.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quads, calves, core.</p>
  <p><strong>Goal:</strong> Fuse speed with jump power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>
<div class="cycle">
  <h3>2. Depth Plyo Burst (3 × 10 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="Depth Plyo Burst" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop from a box, land softly, then perform three rapid squat jumps in place before next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Build rapid reactive sequences under fatigue.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>3. Slingshot Kicks (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Snap leg forward explosively, alternating sides, for rapid hip drive.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, hamstrings, calves.</p>
  <p><strong>Goal:</strong> Hone explosive hip snap.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>4. Kneeling Jumps into High Knees (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283600" 
    title="Kneeling Jumps into High Knees" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, explode to feet then immediately perform high-knee hops in place.</p>
  <p><strong>Muscles Worked:</strong> Glutes, quads, calves, core.</p>
  <p><strong>Goal:</strong> Develop reactive hip extension followed by rapid knee drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 7.5/10</p>
</div>`;
                }
                else if (day === '45') {
                  // Day 45 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Reverse Depth Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Reverse Depth Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Stand off a box facing away, step down, then rotate to land forward into a vertical jump.</p>
  <p><strong>Muscles Worked:</strong> Glutes, quads, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Challenge coordination and eccentric control.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Snap Switch Tuck (3 × 8 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="Snap Switch Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump off one leg and tuck that knee to chest, land on the same leg, then switch.</p>
  <p><strong>Muscles Worked:</strong> Quads, hip flexors, calves, core.</p>
  <p><strong>Goal:</strong> Advance unilateral reactive power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>3. Mini Steps into Squat Jumps (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025284525" 
    title="Mini Steps into Squat Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform 4 mini steps, then drop into a deep squat and explode into a jump.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Enhance foot-speed-to-power transition.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Single-Leg Tuck Outs (3 × 8 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278218" 
    title="Single-Leg Tuck Outs" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump on one leg, drive knee to chest, land softly, then switch legs next set.</p>
  <p><strong>Muscles Worked:</strong> Quads, hip flexors, calves, core.</p>
  <p><strong>Goal:</strong> Peak unilateral jump performance.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 7.7/10</p>
</div>`;
                }
                else if (day === '46') {
                  // Day 46 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Squat Jumps (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Squat Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From a deep squat, explode up into a vertical jump, land softly and reset.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Refine concentric power from low start.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Depth Plyo Burst (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025278875" 
    title="Depth Plyo Burst" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drop off a box, land softly, then perform three quick squat jumps before next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Train rapid reactive jump sequences.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Lateral Bounds (3 × 7 reps each side)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025286459" 
    title="Kneeling Lateral Bounds" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, bound laterally off one leg and return to kneeling.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, quads, calves, core.</p>
  <p><strong>Goal:</strong> Perfect lateral spring from unstable base.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.6/10</p>
</div>
<div class="cycle">
  <h3>4. Shockwave Toe Reach into Squat Jump (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach into Squat Jump" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and reach toes mid-air, land into a deep squat and explode up again.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quads, core.</p>
  <p><strong>Goal:</strong> Combine elastic recoil with squat power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '47') {
                  // Day 47 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Multi-Level Depth Broad Jumps (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Multi-Level Depth Broad Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform broad jumps off 12", then 16", then 20", focusing on max distance.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, quads, calves, core.</p>
  <p><strong>Goal:</strong> Overload horizontal power to boost vertical spring.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>2. Kneeling One-Leg Surge into Foot Fire (3 × 6 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844810" 
    title="Kneeling One-Leg Surge into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Drive thigh up powerfully from kneel, land on foot, then rapid foot-fire hops before switching.</p>
  <p><strong>Muscles Worked:</strong> Hip flexors, quads, calves, core.</p>
  <p><strong>Goal:</strong> Fuse single-leg drive with reactive foot turnover.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>3. Tornado Tuck into Lateral Bound (3 × 7 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844425" 
    title="Tornado Tuck into Lateral Bound" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform Tornado Tuck, land softly, then bound laterally off either leg.</p>
  <p><strong>Muscles Worked:</strong> Core, glutes, abductors, calves.</p>
  <p><strong>Goal:</strong> Combine rotational and lateral power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Slingshot Kicks (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845255" 
    title="Slingshot Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Rapidly snap leg forward in slingshot motion, alternating sides each rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Maximize hip snap speed.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
                else if (day === '48') {
                  // Day 48 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Box Plyos (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025264414" 
    title="Depth Box Plyos" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump onto box, step down, then repeat, focusing on soft landings.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Blend concentric and eccentric loading for vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Lateral Hurdles (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025265470" 
    title="Lateral Hurdles" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Bound laterally over 6 hurdles, landing softly and rebounding immediately.</p>
  <p><strong>Muscles Worked:</strong> Glute medius, quads, calves, core.</p>
  <p><strong>Goal:</strong> Enhance lateral spring under higher volume.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>3. Vortex Kick Ups (3 × 10 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845936" 
    title="Vortex Kick Ups" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Perform continuous circular kick-ups to prime elastic chain.</p>
  <p><strong>Muscles Worked:</strong> Calves, quads, glutes, core.</p>
  <p><strong>Goal:</strong> Maximize tendon rebound under fatigue.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.7/10</p>
</div>
<div class="cycle">
  <h3>4. Snap Twitch Tuck (3 × 8 reps each leg)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845786" 
    title="Snap Twitch Tuck" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump off one leg, tuck knee to chest, land on same leg, then switch.</p>
  <p><strong>Muscles Worked:</strong> Quads, hip flexors, calves, core.</p>
  <p><strong>Goal:</strong> Peak unilateral reactive drive.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>`;
                }
                else if (day === '49') {
                  // Day 49 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Split Jumps (3 × 10 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025266253" 
    title="Split Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From lunge stance, explode up switching legs mid-air, land softly.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, hamstrings, calves, hip flexors.</p>
  <p><strong>Goal:</strong> Peak single-leg coordination and power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.8/10</p>
</div>
<div class="cycle">
  <h3>2. Seated Squat Jumps into Foot Fire (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027634965" 
    title="Seated Squat Jumps into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Sit at 90°, explode up, then perform rapid foot-fire hops before next rep.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Integrate static start power with agility.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.2/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Broad Jumps into Foot Fire (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1025283869" 
    title="Kneeling Broad Jumps into Foot Fire" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From knees, broad jump to feet then immediate foot-fire hops.</p>
  <p><strong>Muscles Worked:</strong> Glutes, hamstrings, calves, core.</p>
  <p><strong>Goal:</strong> Fuse horizontal power with reactive foot speed.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 8.9/10</p>
</div>
<div class="cycle">
  <h3>4. Shockwave Toe Reach (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059845057" 
    title="Shockwave Toe Reach" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Jump and reach for toes mid-air, land softly with full hip extension.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Maximize trunk-to-leg synchronicity.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.3/10</p>
</div>`;
                }
                else if (day === '50') {
                  // Day 50 cycles
                  content.innerHTML = `
<div class="cycle">
  <h3>1. Depth Drops into Sprint (3 × 6 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1027635519" 
    title="Depth Drops into Sprint" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a box, land softly, then immediately sprint 10m at max effort.</p>
  <p><strong>Muscles Worked:</strong> Hamstrings, glutes, quads, calves, core.</p>
  <p><strong>Goal:</strong> Fuse reactive jump with acceleration power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.1/10</p>
</div>
<div class="cycle">
  <h3>2. Depth Tuck Jumps (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/102435274226" 
    title="Depth Tuck Jumps" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Step off a low box, then tuck knees to chest at peak of jump.</p>
  <p><strong>Muscles Worked:</strong> Quads, glutes, calves, core.</p>
  <p><strong>Goal:</strong> Max out reactive rebound height.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.4/10</p>
</div>
<div class="cycle">
  <h3>3. Kneeling Tendon Snap Kicks (3 × 8 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059846136" 
    title="Kneeling Tendon Snap Kicks" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> From kneel, snap leg forward with max tendon recoil, land back on knees and repeat.</p>
  <p><strong>Muscles Worked:</strong> Quads, hamstrings, Achilles tendon, core.</p>
  <p><strong>Goal:</strong> Hone tendon-driven explosive spring.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>
<div class="cycle">
  <h3>4. Meteor Blast (3 × 9 reps)</h3>
  <iframe 
    src="https://player.vimeo.com/video/1059844259" 
    title="Meteor Blast" 
    style="width:100%; height:300px; border:none; border-radius:5px;">
  </iframe>
  <p><strong>Description:</strong> Propel arms overhead like a meteor while jumping, then land softly.</p>
  <p><strong>Muscles Worked:</strong> Shoulders, core, glutes, calves.</p>
  <p><strong>Goal:</strong> Integrate upper-body drive with peak vertical power.</p>
  <p><strong style="color:red;">Jump-gain impact:</strong> 9.0/10</p>
</div>`;
                }
     else {
                    alert(`Clicked Day ${day}`);
                  }
                })
              );
            }
          }
        });
      });
    });
  </script>
</body>
</html>


<!--
  ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~
  End of file (over 400 lines including comments & blanks)
  ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~
-->
