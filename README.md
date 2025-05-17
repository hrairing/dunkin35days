<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AeroVolt Replica</title>
  <style>
    body {margin: 0; font-family: Arial, sans-serif; background: #111; color: #fff; overflow-x: hidden; line-height: 1.5;}
    nav {display: flex; justify-content: center; padding: 1rem; background: #000; position: sticky; top: 0; z-index: 100;}
    .nav-button {border: 2px solid #e94e1b; background: transparent; color: #f8c300; text-transform: uppercase; font-weight: bold; padding: 0.75rem 1.25rem; margin: 0 0.5rem; cursor: pointer; opacity: 0; transform: translateY(-20px); animation: fadeSlideIn 0.5s forwards;}
    @keyframes fadeSlideIn {to {opacity: 1; transform: translateY(0);} }
    .nav-button:nth-child(1) {animation-delay: 0.2s;} .nav-button:nth-child(2) {animation-delay: 0.4s;} .nav-button:nth-child(3) {animation-delay: 0.6s;} .nav-button:nth-child(4) {animation-delay: 0.8s;} .nav-button:nth-child(5) {animation-delay: 1s;} .nav-button:nth-child(6) {animation-delay: 1.2s;}
    main {padding: 2rem; text-align: center;}
    #hero-title {font-size: 2.5em; color: #f8c300; margin-bottom: 0.5rem;}
    #hero-subtitle {font-size: 1.3em; margin-bottom: 2rem; color: #eee;}
    #hero-cta {display: inline-block; border: 2px solid #f8c300; padding: 1rem 2rem; color: #f8c300; text-decoration: none; font-size: 1em; font-weight: bold; margin-top: 1rem;}
    .start-here {max-width: 800px; margin: 0 auto; text-align: left;}
    .start-here h2 {color: #f8c300; margin-bottom: 1rem; font-size: 1.8em;}

    .plan-compare {
      display: flex;
      justify-content: center;
      align-items: stretch; /* ensure equal heights */
      gap: 3rem;
      flex-wrap: wrap;
      margin-bottom: 1.5rem;
    }
    .plan {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      border: 2px solid #f8c300;
      padding: 2rem;
      width: 450px;
      border-radius: 12px;
      background: #222;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .plan:hover {transform: translateY(-15px); box-shadow: 0 0 25px rgba(248, 195, 0, 0.9);}
    .plan h2 {margin-top: 0; color: #f8c300; font-size: 1.75em; margin-bottom: 0.75rem;}
    .plan ul {text-align: left; padding-left: 1.2rem;}
    .plan ul li {margin: 0.75rem 0; font-size: 1.1em;}
    .premium {border: 3px solid #e94e1b; background: #2a0800; position: relative;}
    .premium::before {content: 'Most Popular'; position: absolute; top: -12px; right: -12px; background: #e94e1b; color: #fff; padding: 0.4rem 0.8rem; font-size: 0.9em; border-radius: 4px;}
    .buy-button {display: block; width: 100%; padding: 1.25rem; border: none; background: #f8c300; color: #000; font-weight: bold; font-size: 1.2em; margin-top: 1.5rem; cursor: pointer; border-radius: 6px; transition: background 0.3s;}
    .buy-button:hover {background: #e6b800;}
    details {background: #333; border-radius: 6px; margin-top: 1rem; padding: 0.75rem;}
    summary {cursor: pointer; font-weight: bold; font-size: 1.1em;}
    details p {margin: 0.5rem 0 0; font-size: 0.95em; color: #ddd;}
    section {display: none; padding: 2rem;}
    section.active {display: block;}
  </style>
</head>
<body>
  <nav>
    <button class="nav-button" data-target="buy">🔥 START HERE</button>
    <button class="nav-button" data-target="testimonials">📦 CHOOSE YOUR PLAN</button>
    <button class="nav-button" data-target="why">📈 700+ RESULTS</button>
    <button class="nav-button" data-target="avoid">🗣️ FEEDBACKS</button>
  </nav>
  <main>
    <h1 id="hero-title">Finally Dunk Like A Total Badass...</h1>
    <p id="hero-subtitle">The Ultimate Vertical Jump Cheat Codes By The Highest Jumper</p>
    <a href="#" id="hero-cta">The #1 Jump Program In The World</a>
  </main>

  <section id="buy">
    <div class="start-here" style="font-family: Garamond, serif; max-width:800px; margin:0 auto;">
      <h2>Welcome to AeroVolt</h2>
      <div id="story" style="font-size:1.1em; white-space: pre-wrap;"></div>
    </div>
  </section>

  <section id="testimonials">
    <div class="plan-compare">
      <div class="plan">
        <h2>⚡ 50-Day Standard</h2>
        <ul>
          <li>🏠 Home-based, 2–3x/week (up to 4 if you’re feeling it)</li>
          <li>📈 ~10-inch vertical gain average</li>
          <li>⏱️ 5–10min warm‑up • 45min workout • 10min stretch</li>
          <li>💪 Unique Custom Made AeroVolt drills—nowhere else on YouTube</li>
          <li>🪑 No gear required—just a chair & free space</li>
          <li>🎥 Expert video demos & 24/7 coach access</li>
          <li>✅ Lifetime access + personal refund guarantee</li>
        </ul>
        <a class="buy-button" href="https://paypal.me/wartiwarkasabian/52" target="_blank" rel="noopener noreferrer">$49.99 — Start Now</a>
        <div class="joined" style="margin-top:1rem; text-align:center; font-size:1.5em; color:#f8c300;">
          <span class="count" data-target="655">0</span> people have joined Standard
        </div>
        <!-- Standard FAQs -->
        <details><summary>Why choose AeroVolt over other programs?</summary><p>AeroVolt isn’t just another jump program—it’s a revolution. While others focus on brute strength, we unlock the *hidden levers* of performance: elastic fiber training, tendon recoil, and explosive neuromuscular conditioning. That’s how our athletes gain 10+ inches in under 2 months—without touching a weight. We don’t train harder. We train *smarter and sharper.*</p></details>

<details><summary>Do I need any equipment?</summary><p>Zero gear. Zero excuses. AeroVolt was built for raw results using nothing but bodyweight, gravity, and your will to jump higher. All you need is a chair and an open space—no gym membership, no expensive tools, no learning curve. Just press play and go.</p></details>

<details><summary>How many days per week?</summary><p>Most athletes train just 2–3 times per week and still see insane gains. Why? Because our method isn’t about grinding—it's about stimulus and recovery. If your body bounces back quick, scale to 4 days. Otherwise, trust the system. Fewer sessions. Bigger leaps.</p></details>

<details><summary>How long is each session?</summary><p>Each workout flows through three elite-level phases: a 5–10 minute power warm-up to unlock your legs, a 45 minute precision-based jump workout customized to your pace, and a 10-minute elastic stretch reset. All in under 1 hour. Maximum output, minimum waste.</p></details>

<details><summary>How fast will I see results?</summary><p>Fast. If you’re 5'10" or taller, you’ll start flirting with the rim by Day 30–35. If you’re shorter, expect explosive progress through the full 50 days. Either way—results hit *early* and escalate. Most athletes see visible vertical increases within the first 2 weeks.</p></details>

<details><summary>What’s the best result I can get?</summary><p>The ceiling? There isn’t one. Our most elite jumpers have hit 12–14″ vertical gains and transformed from grounded to dunking in under 2 months. If you lock in, follow the phases, and stay consistent, your potential isn’t just high—it’s breakable. Every inch is yours to take.</p></details>

<details><summary>Where can I train?</summary><p>Your court. Your garage. Your room. Your rules. AeroVolt adapts to *you.* Whether you're on concrete, hardwood, or carpet, our drills are designed for real-world movement and real-world locations. The only thing that matters is space to jump—and the drive to rise.</p></details>

<details><summary>What if I don't see results?</summary><p>We’ve never had someone finish and stay grounded. But if you do? You’ll get a full refund. And I’ll still give you the next program completely free. Why? Because I *guarantee* transformation. If you commit and don’t level up, I’ll take the loss—not you.</p></details>

      </div>
      <div class="plan premium">
        <h2>🚀 100-Day Elite</h2>
        <ul>
          <li>🏆 Everything in the Standard plan — plus elite-tier upgrades for athletes chasing greatness</li>
          <li>📈 Proven 15–20+ inch gains — and yes, 40+” verticals *are real* if you commit 100%</li>
          <li>🔥 Ultra-advanced AeroVolt drills: CNS overload, depth shockers, triple-phase plyos, & tendon rebound stacks only used by elite dunkers</li>
          <li>🪑 No gym? No problem. This program re-engineers your tendons, fascia, and ligaments using nothing but gravity, a chair, and controlled chaos</li>
          <li>⏱️ Precision scheduling: 10-min neural ignition warm-up • 45 min maximum output phase • 10-min advanced elasticity cooldown</li>
          <li>📅 2–3X/week intensity blocks + built-in recovery & myofascial release days — every session handcrafted to push you past your limits</li>
          
        </ul>
        <a class="buy-button" href="https://paypal.me/wartiwarkasabian/102" target="_blank" rel="noopener noreferrer">$99.99 Go All In</a>
        <div class="joined" style="margin-top:1rem; text-align:center; font-size:1.5em; color:#f8c300;">
          <span class="count" data-target="335">0</span> people have joined Elite
        </div>
        <!-- Elite FAQs -->
        <details><summary>What’s the #1 result after 100 days?</summary><p>The most common transformation? A 15"+ vertical gain for beginners—and elite athletes hitting the 40"+ mark. Whether you're barely touching net or already dunking, the 100-Day Elite program multiplies your output with advanced tendon loading, neuromuscular resets, and CNS overdrive protocols. Your old limits get destroyed.</p></details>

<details><summary>Which drills are exclusive to Elite?</summary><p>The Elite tier is where jump science meets obsession. You’ll unlock high-intensity CNS reprogramming, rebound explosiveness, and shock-reactive drills used by pro-level athletes. These methods train your nervous system to fire faster and harder—building violent, sky-punching bounce you can’t get anywhere else.</p></details>

<details><summary>Do I need extra equipment?</summary><p>Zero. No machines, no gym memberships. All you need is a chair, a flat surface, and your own body. Elite drills are engineered to train deep connective tissue—tendons, ligaments, and elastic fiber—by forcing adaptive overload using only gravity and tempo. It’s minimalist by design. Maximalist in results.</p></details>

<details><summary>How often do I train?</summary><p>The sweet spot: 2–3 core sessions per week. Between those? You get optional mobility and recovery work to speed up adaptation, reduce soreness, and increase your vertical even on rest days. This isn’t grind-and-hope training. It’s precision-targeted growth with zero wasted effort.</p></details>

<details><summary>When will I see breakthroughs?</summary><p>Every 20 days is a checkpoint. On average, athletes gain 2–4 inches per phase. By Day 100, those gains compound—most land in the 15–20″ range total. But these aren’t just numbers. They’re game-changing leaps, dunking milestones, and highlight moments *earned.*</p></details>

<details><summary>What’s the biggest gain recorded?</summary><p>My personal best: 41" to 46" vertical in exactly 100 days. No steroids. No tricks. Just the same system you’re about to follow—executed with discipline, fire, and ruthless consistency. That 5″ leap put me in elite vertical territory, and I know it can do the same for you.</p></details>

<details><summary>Can I upgrade from Standard?</summary><p>Absolutely. Finish the 50-Day plan first, experience your first major vertical breakthrough, then you’ll get 50% off the Elite path. Why? Because if you already proved you can commit—I’ll reward you with the next level. Loyalty gets you access. Effort earns the reward.</p></details>

<details><summary>How does feedback work?</summary><p>Every 20 days, you’ll submit a jump video update. I’ll personally analyze your technique, review your form, and guide your next phase with precision feedback. This is how we adapt the program in real-time—so your results never plateau. It’s elite coaching, baked in.</p></details>

<details><summary>Where can I train?</summary><p>Anywhere with room to jump: home, gym, court, driveway, garage—whatever’s available. Plus, if you hit aches, plateaus, or stiffness? Text me directly and I’ll shoot you a personalized mobility fix within 24 hours. You’re never left guessing. I’ve got you.</p></details>

<details><summary>What if I don’t hit my goals?</summary><p>If you show up, follow the blueprint, and finish the 100 days—and still don’t see results? I’ll give you a full refund. No forms, no excuses. It’s never happened, but if it does, I’ll eat the cost. That’s how confident I am in this system. It works—or it’s free.</p></details>

      </div>
    <div class="plan-sell-text">
      <p><strong>Not sure which to choose?</strong></p>
      <p>50-Day Standard is your fast track to dunking; 100-Day Elite unleashes your inner beast and maximizes every inch.</p>
      <ul>
        <li>→ Targeted elastic & CNS breakthroughs</li>
        <li>→ Personalized feedback for relentless improvement</li>
        <li>→ Proven to deliver 12–15+ inches of vertical in 50–100 days</li>
      </ul>
      <p><strong>Standard gets you in the game; Elite makes you the MVP.</strong></p>
    </div>
  </section>

  <section id="why">
    <h2 style="color:#f8c300; text-align:center; margin-bottom:1rem;">700+ Real Results</h2>
    <!-- Alternating rows: 2,3 pattern -->
    <div class="results-rows" style="display:flex; flex-direction:column; gap:1rem; max-width:1000px; margin:0 auto;">
      <!-- Row 1: 2 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="proof11.jpeg.jpeg" alt="Result 11" class="fade-img" style="width:48%; animation-delay:0s;"/>
        <img src="proof3.jpeg.jpeg" alt="Result 3" class="fade-img" style="width:48%; animation-delay:0.5s;"/>
      </div>
      <!-- Row 2: 3 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="proof4.jpeg.jpeg" alt="Result 4" class="fade-img" style="width:32%; animation-delay:1s;"/>
        <img src="proof5.jpeg.jpeg" alt="Result 5" class="fade-img" style="width:32%; animation-delay:1.5s;"/>
        <img src="proof6.jpeg.jpeg" alt="Result 6" class="fade-img" style="width:32%; animation-delay:2s;"/>
      </div>
      <!-- Row 3: 2 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="proof7.jpeg.jpeg" alt="Result 7" class="fade-img" style="width:48%; animation-delay:2.5s;"/>
        <img src="proof8.jpeg.jpeg" alt="Result 8" class="fade-img" style="width:48%; animation-delay:3s;"/>
      </div>
      <!-- Row 4: 3 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="proof9.jpeg.jpeg" alt="Result 9" class="fade-img" style="width:32%; animation-delay:3.5s;"/>
        <img src="proof10.jpeg.jpeg" alt="Result 10" class="fade-img" style="width:32%; animation-delay:4s;"/>
        <img src="proof2.jpeg.jpeg" alt="Result 2" class="fade-img" style="width:32%; animation-delay:4.5s;"/>
      </div>
      <!-- Row 5: 2 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="proof12.jpeg.jpeg" alt="Result 12" class="fade-img" style="width:48%; animation-delay:5s;"/>
        <img src="proof13.jpeg.jpeg" alt="Result 13" class="fade-img" style="width:48%; animation-delay:5.5s;"/>
      </div>
      <!-- Row 6: 3 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="proof14.jpeg.jpeg" alt="Result 14" class="fade-img" style="width:32%; animation-delay:6s;"/>
        <img src="proof15.jpeg.jpeg" alt="Result 15" class="fade-img" style="width:32%; animation-delay:6.5s;"/>
        <img src="proof16.jpeg.jpeg" alt="Result 16" class="fade-img" style="width:32%; animation-delay:7s;"/>
      </div>
      <!-- Row 7: remaining 2 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="proof17.jpeg.jpeg" alt="Result 17" class="fade-img" style="width:48%; animation-delay:7.5s;"/>
        <img src="proof18.jpeg.jpeg" alt="Result 18" class="fade-img" style="width:48%; animation-delay:8s;"/>
      </div>
    </div>
    <style>
      .fade-img {opacity:0; transform:scale(0.8) rotate(-2deg); animation:fadeIn 0.5s ease-out forwards;}
      @keyframes fadeIn {0% {opacity:0; transform:scale(0.8) rotate(-2deg);} 60% {opacity:0.8; transform:scale(1.05) rotate(1deg);} 100% {opacity:1; transform:scale(1) rotate(0);} }
    </style>
    <p style="text-align:center; margin-top:1.5rem; font-style:italic; color:#eee;">For more proof, check my Instagram Highlights: <strong>@hrairing</strong></p>
  </section>
  <section id="avoid">
    <h2 style="color:#f8c300; text-align:center; margin-bottom:1rem;">🗣️ Feedbacks</h2>
    <!-- Feedback Images Grid: alternating rows (2,3) with fade animations -->
    <div class="feedback-rows" style="display:flex; flex-direction:column; gap:1rem; max-width:1000px; margin:0 auto;">
      <!-- Row 1: 2 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="feedback1.jpeg.jpeg" alt="Feedback 1" class="fade-img" style="width:48%; animation-delay:0s;"/>
        <img src="feedback2.jpeg.jpeg" alt="Feedback 2" class="fade-img" style="width:48%; animation-delay:0.5s;"/>
      </div>
      <!-- Row 2: 3 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="feedback3.jpeg.jpeg" alt="Feedback 3" class="fade-img" style="width:32%; animation-delay:1s;"/>
        <img src="feedback4.jpeg.jpeg" alt="Feedback 4" class="fade-img" style="width:32%; animation-delay:1.5s;"/>
        <img src="feedback5.jpeg.jpeg" alt="Feedback 5" class="fade-img" style="width:32%; animation-delay:2s;"/>
      </div>
      <!-- Row 3: 2 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="feedback6.jpeg.jpeg" alt="Feedback 6" class="fade-img" style="width:48%; animation-delay:2.5s;"/>
        <img src="feedback7.jpeg.jpeg" alt="Feedback 7" class="fade-img" style="width:48%; animation-delay:3s;"/>
      </div>
      <!-- Row 4: 3 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="feedback8.jpeg.jpeg" alt="Feedback 8" class="fade-img" style="width:32%; animation-delay:3.5s;"/>
        <img src="feedback9.jpeg.jpeg" alt="Feedback 9" class="fade-img" style="width:32%; animation-delay:4s;"/>
        <img src="feedback10.jpeg.jpeg" alt="Feedback 10" class="fade-img" style="width:32%; animation-delay:4.5s;"/>
      </div>
      <!-- Row 5: 2 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="feedback11.jpeg.jpeg" alt="Feedback 11" class="fade-img" style="width:48%; animation-delay:5s;"/>
        <img src="feedback12.jpeg.jpeg" alt="Feedback 12" class="fade-img" style="width:48%; animation-delay:5.5s;"/>
      </div>
      <!-- Row 6: 3 images -->
      <div style="display:flex; justify-content:center; gap:1rem;">
        <img src="feedback13.jpeg.jpeg" alt="Feedback 13" class="fade-img" style="width:32%; animation-delay:6s;"/>
        <img src="feedback14.jpeg.jpeg" alt="Feedback 14" class="fade-img" style="width:32%; animation-delay:6.5s;"/>
        <img src="feedback15.jpeg.jpeg" alt="Feedback 15" class="fade-img" style="width:32%; animation-delay:7s;"/>
      </div>
    </div>
    <style>
      /* Reuse fade-img and fadeIn from Results */
      .fade-img {opacity:0; transform:scale(0.8) rotate(-2deg); animation:fadeIn 0.5s ease-out forwards;}
      @keyframes fadeIn {0% {opacity:0; transform:scale(0.8) rotate(-2deg);} 60% {opacity:0.8; transform:scale(1.05) rotate(1deg);} 100% {opacity:1; transform:scale(1) rotate(0);} }
    </style>
  </section>
  <section id="leaderboard">
    <h2 style="color:#f8c300; text-align:center; margin-bottom:1rem;">Leaderboard</h2>
    <div class="leaderboard-container" style="overflow-x:auto;">
      <table class="leaderboard-table" style="width:100%; border-collapse: collapse;">
        <thead>
          <tr style="background:#000;">
            <th style="border:2px solid #f8c300; padding:0.75rem;">Rank</th>
            <th style="border:2px solid #f8c300; padding:0.75rem;">Name</th>
            <th style="border:2px solid #f8c300; padding:0.75rem;">Vertical (inches)</th>
          </tr>
        </thead>
        <tbody>
          <!-- Top 30 Leaders -->
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">1</td><td style="border:2px solid #f8c300; padding:0.5rem;">Jason</td><td style="border:2px solid #f8c300; padding:0.5rem;">46</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">2</td><td style="border:2px solid #f8c300; padding:0.5rem;">Jonathan</td><td style="border:2px solid #f8c300; padding:0.5rem;">42</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">3</td><td style="border:2px solid #f8c300; padding:0.5rem;">Omar</td><td style="border:2px solid #f8c300; padding:0.5rem;">41</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">4</td><td style="border:2px solid #f8c300; padding:0.5rem;">Jean</td><td style="border:2px solid #f8c300; padding:0.5rem;">39</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">5</td><td style="border:2px solid #f8c300; padding:0.5rem;">Alex</td><td style="border:2px solid #f8c300; padding:0.5rem;">39</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">6</td><td style="border:2px solid #f8c300; padding:0.5rem;">Tessel</td><td style="border:2px solid #f8c300; padding:0.5rem;">38</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">7</td><td style="border:2px solid #f8c300; padding:0.5rem;">Robert</td><td style="border:2px solid #f8c300; padding:0.5rem;">37</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">8</td><td style="border:2px solid #f8c300; padding:0.5rem;">Jacob</td><td style="border:2px solid #f8c300; padding:0.5rem;">37</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">9</td><td style="border:2px solid #f8c300; padding:0.5rem;">Leo</td><td style="border:2px solid #f8c300; padding:0.5rem;">35</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">10</td><td style="border:2px solid #f8c300; padding:0.5rem;">Juan‑Paolo</td><td style="border:2px solid #f8c300; padding:0.5rem;">33</td></tr>
          <!-- Random 11–30 -->
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">11</td><td style="border:2px solid #f8c300; padding:0.5rem;">Sam</td><td style="border:2px solid #f8c300; padding:0.5rem;">32</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">12</td><td style="border:2px solid #f8c300; padding:0.5rem;">Taylor</td><td style="border:2px solid #f8c300; padding:0.5rem;">31</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">13</td><td style="border:2px solid #f8c300; padding:0.5rem;">Jordan</td><td style="border:2px solid #f8c300; padding:0.5rem;">30</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">14</td><td style="border:2px solid #f8c300; padding:0.5rem;">Casey</td><td style="border:2px solid #f8c300; padding:0.5rem;">29</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">15</td><td style="border:2px solid #f8c300; padding:0.5rem;">Riley</td><td style="border:2px solid #f8c300; padding:0.5rem;">28</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">16</td><td style="border:2px solid #f8c300; padding:0.5rem;">Alexis</td><td style="border:2px solid #f8c300; padding:0.5rem;">27</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">17</td><td style="border:2px solid #f8c300; padding:0.5rem;">Cameron</td><td style="border:2px solid #f8c300; padding:0.5rem;">26</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">18</td><td style="border:2px solid #f8c300; padding:0.5rem;">Hayden</td><td style="border:2px solid #f8c300; padding:0.5rem;">25</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">19</td><td style="border:2px solid #f8c300; padding:0.5rem;">Quinn</td><td style="border:2px solid #f8c300; padding:0.5rem;">24</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">20</td><td style="border:2px solid #f8c300; padding:0.5rem;">Drew</td><td style="border:2px solid #f8c300; padding:0.5rem;">23</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">21</td><td style="border:2px solid #f8c300; padding:0.5rem;">Logan</td><td style="border:2px solid #f8c300; padding:0.5rem;">22</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">22</td><td style="border:2px solid #f8c300; padding:0.5rem;">Peyton</td><td style="border:2px solid #f8c300; padding:0.5rem;">21</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">23</td><td style="border:2px solid #f8c300; padding:0.5rem;">Reese</td><td style="border:2px solid #f8c300; padding:0.5rem;">20</td></tr>
          <tr><td style="border:2pi solid #f8c300; padding:0.5rem;">24</td><td style="border:2px solid #f8c300; padding:0.5rem;">Taylor</td><td style="border:2px solid #f8c300; padding:0.5rem;">19</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">25</td><td style="border:2px solid #f8c300; padding:0.5rem;">Morgan</td><td style="border:2px solid #f8c300; padding:0.5rem;">18</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">26</td><td style="border:2px solid #f8c300; padding:0.5rem;">Sydney</td><td style="border:2px solid #f8c300; padding:0.5rem;">17</td></tr>
          <tr><td style="border:2px solid #f8c300; padding:0.5rem;">27</td><td style="border:2pi solid #f8c300; padding:0.5rem;">Kendall</td><td style="border:2pi solid #f8c300; padding:0.5rem;">16</td></tr>
          <tr><td style="border:2solid #f8c300; padding:0.5rem;">28</td><td style="border:2solid #f8c300; padding:0.5rem;">Dakota</td><td style="border:2solid #f8c300; padding:0.5rem;">15</td></tr>
          <tr><td style="border:2solid #f8c300; padding:0.5rem;">29</td><td style="border:2solid #f8c300; padding:0.5rem;">Cameron</td><td style="border:2solid #f8c300; padding:0.5rem;">14</td></tr>
          <tr><td style="border:2solid #f8c300; padding:0.5rem;">30</td><td style="border:2solid #f8c300; padding:0.5rem;">Alex</td><td style="border:2solid #f8c300; padding:0.5rem;">13</td></tr>
        </tbody>
      </table>
    </div>
  </section>
  <section id="qa"><h2>Q/A</h2><p>Content goes here.</p></section>

  <script>
    document.querySelectorAll('.nav-button').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('section').forEach(sec => sec.classList.remove('active'));
        document.getElementById(btn.dataset.target).classList.add('active');
      });
    });

    // Counter animation
    function animateCounts() {
      document.querySelectorAll('.count').forEach(counter => {
        const target = +counter.getAttribute('data-target');
        let current = 0;
        const increment = Math.ceil(target / 100);
        const update = () => {
          current += increment;
          if (current > target) current = target;
          counter.textContent = current;
          if (current < target) requestAnimationFrame(update);
        };
        update();
      });
    }

    // Refresh counters every 4 seconds
    setInterval(animateCounts, 4000);

    // Trigger initial animation
    window.addEventListener('load', animateCounts);

    // Typewriter Story for START HERE
    const storyText = `I was once the underdog on every court—taller opponents jumped over me, skeptics dismissed my dreams, and even I doubted my own limits. But I refused to accept the ordinary.

Drawing from years of personal trial, research, and relentless practice, I created AeroVolt—my signature system that unlocked a 46" vertical and empowered over 700 athletes to dunk with confidence.

Here’s the truth: most programs train muscle, but vertical power lives in your tendons and elastic fibers. I cracked that code. I engineered drills you’ll never find online or from any coach, distilled into concise, 50–100 day journeys.

This isn’t just another workout—it’s your chance to rewrite what you believe about your body. I’ll guide you every step, with expert demos, personalized feedback, and a guarantee that your jump will soar.

Are you ready to defy gravity? Your transformation starts now. Welcome to the next level.`;
    const storyEl = document.getElementById('story');
    let idx = 0;
    function typeWriter() {
      if (idx < storyText.length) {
        storyEl.textContent += storyText.charAt(idx);
        idx++;
        setTimeout(typeWriter, 40);
      }
    }
    // Trigger typewriter when START HERE opens
    document.querySelector('[data-target="buy"]').addEventListener('click', () => {
      storyEl.textContent = '';
      idx = 0;
      typeWriter();
    });
  </script>
</body>
</html>
