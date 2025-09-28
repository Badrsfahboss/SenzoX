<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>SenzoX — Modern Resource Hub</title>
  <meta name="description" content="A clean, modern hub for resources and information, designed with a sleek, dark glass aesthetic." />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
  <!-- Lucide Icons Library -->
  <script src="https://unpkg.com/lucide@latest"></script> 
  <style>
    /* * Design Variables: The core colors for easy customization 
     * Accent 1: Deep Violet/Amethyst (Primary)
     * Accent 2: Electric Cyan (Secondary)
     */
    :root{
      --bg-dark: #061226; 
      --bg-main: #0b1220;
      --glass: rgba(255,255,255,0.04);
      --muted: rgba(255,255,255,0.65);
      --accent1: #6d28d9; /* Deep Violet/Amethyst (PURPLE) */
      --accent2: #00d4ff; /* Electric Cyan (CYAN) */
      --text-main: #eaf0ff;
    }

    /* Base Styling */
    *{box-sizing:border-box}
    html,body{
      height:100%;
      margin:0;
      font-family:'Inter', system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
      /* Background Gradient (Radial glow + Linear Base) 
         UPDATED: Radial glow color changed to purple tint */
      background:
        radial-gradient(1200px 600px at 10% 10%, rgba(109, 40, 217, 0.3), transparent), 
        linear-gradient(180deg, var(--bg-main), var(--bg-dark));
      color: var(--text-main);
      overflow-x: hidden; /* Prevent horizontal scroll on mobile */
      scroll-behavior: smooth;
    }

    /* Layout Container */
    .wrap{
      min-height:100vh;
      display:flex;
      flex-direction: column; /* Allow content to flow vertically */
      align-items:center;
      padding: 120px 24px 48px; 
      position: relative;
      z-index: 1;
      width: 100%;
    }
    
    /* Global Content Wrapper */
    .content-wrapper {
        width: 100%;
        max-width: 1100px;
        margin: 0 auto;
    }

    /* Header/Nav Bar */
    .header{
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      background: var(--bg-main);
      backdrop-filter: blur(10px);
      padding: 16px 24px;
      z-index: 100;
      border-bottom: 1px solid rgba(255,255,255,0.05);
    }
    .header-content{
      max-width: 1100px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .brand{
      display:flex;
      gap:10px;
      align-items:center;
      font-weight: 800;
      font-size: 20px;
      text-decoration: none;
      color: var(--text-main);
    }
    .brand-logo{
      color: var(--accent1); /* Logo color is now PURPLE */
    }
    .nav a{
      font-size: 15px;
      font-weight: 600;
      color: var(--muted);
      text-decoration: none;
      padding: 8px 12px;
      border-radius: 8px;
      transition: all 0.2s ease;
    }
    .nav a:hover{
      color: var(--text-main);
      background-color: rgba(255,255,255,0.05);
    }

    /* Main Panel/Card Style */
    .panel{
      width:100%;
      max-width:1100px;
      /* Glassmorphism Effect */
      background:linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));
      border-radius:18px;
      padding:36px;
      backdrop-filter:blur(10px);
      box-shadow:0 30px 80px rgba(2,6,23,0.8);
      border:1px solid rgba(255,255,255,0.05);
      margin-bottom: 30px;
    }

    /* Centered Hero Section Styling */
    .hero-section {
        text-align: center;
        padding: 60px 20px 80px;
        width: 100%;
        max-width: 800px;
        margin: 0 auto;
    }
    .main-title{
      font-size: 48px; /* Bigger for hero effect */
      font-weight: 800;
      margin: 0 0 16px;
      line-height: 1.1;
    }
    .main-subtitle{
      color: var(--muted);
      font-size: 18px;
      margin:0;
      max-width: 600px;
      margin: 0 auto 30px;
    }
    .hero-buttons {
        display: flex;
        justify-content: center;
        gap: 16px;
    }

    /* Feature Grid Styling */
    .feature-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr); /* 3 columns for desktop */
        gap: 20px;
        margin-top: 40px;
        padding-bottom: 40px;
    }
    .feature-card {
        background: var(--glass);
        padding: 20px;
        border-radius: 12px;
        border: 1px solid rgba(255,255,255,0.03);
    }
    .feature-card h3 {
        font-size: 18px;
        font-weight: 700;
        margin: 10px 0 6px;
    }
    .feature-card p {
        color: var(--muted);
        font-size: 14px;
        margin: 0;
    }
    .icon-wrapper {
        color: var(--accent1); /* Icon color is now PURPLE */
        display: flex;
        align-items: center;
        justify-content: center;
        width: 36px;
        height: 36px;
        /* UPDATED: icon background now uses a transparent purple tint */
        background-color: rgba(109, 40, 217, 0.1); 
        border-radius: 8px;
    }
    .icon-wrapper span[data-lucide] {
        width: 20px; 
        height: 20px;
    }


    /* Supported Games Section Styling */
    .games-section {
        padding: 60px 0;
        text-align: center; /* Ensures titles and text are centered */
    }
    .game-grid {
        display: flex;
        flex-wrap: wrap;
        justify-content: center; /* Ensures the game cards are centered as a group */
        gap: 20px;
        margin-top: 30px;
    }
    .game-card {
        width: 150px; /* Fixed width for game card */
        text-align: center;
        background: var(--glass);
        padding: 10px 10px 15px 10px;
        border-radius: 12px;
        border: 1px solid rgba(255,255,255,0.03);
        transition: transform 0.2s ease;
    }
    .game-card:hover {
        transform: translateY(-5px);
        border-color: var(--accent2); /* Border hover is now CYAN */
    }
    .game-logo {
        width: 100%;
        height: 90px;
        border-radius: 8px;
        margin-bottom: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 24px;
        font-weight: 800;
        color: white;
    }
    .game-name {
        font-size: 14px;
        font-weight: 600;
        margin: 0;
    }
    .game-support {
        font-size: 12px;
        color: var(--accent2); /* Support text is now CYAN */
        margin-top: 4px;
    }
    
    /* Additional Games Box */
    .additional-games-box {
        background: var(--bg-main);
        padding: 30px;
        border-radius: 18px;
        margin-top: 30px;
        max-width: 600px;
        margin-left: auto; /* Centers the block itself */
        margin-right: auto; /* Centers the block itself */
        border: 1px solid rgba(255,255,255,0.05);
    }
    .additional-games-box h3 {
        font-size: 24px;
        font-weight: 800;
        margin: 0 0 10px;
        color: var(--accent2); /* Title is now CYAN */
    }
    .additional-games-box p {
        color: var(--muted);
        font-size: 14px;
        margin: 0 0 20px;
    }


    /* Download Box & Buttons */
    .download-section {
        padding: 60px 0;
        text-align: center;
    }
    .download-card {
        width: 100%;
        max-width: 400px; /* Make the download card prominent */
        margin: 0 auto;
        padding: 30px;
    }
    .download-card strong{
      font-size: 24px; /* Slightly larger text for prominence */
      display: block;
    }
    .download-card p{
      margin:10px 0 20px;
      color: var(--muted);
      font-size: 15px;
    }
    .btn-group{
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-top: 10px;
    }
    .big-btn, .alt-btn{
      display:inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      padding:16px 20px;
      border-radius:12px;
      text-decoration:none;
      font-weight:700;
      text-align:center;
      transition: all 0.3s ease;
      cursor: pointer;
      border: 2px solid transparent;
    }
    /* NEW: Ensure buttons inside the group take full width to appear centered */
    .btn-group .big-btn, .btn-group .alt-btn {
        width: 100%;
    }
    /* END NEW */

    .big-btn{
      color:#041026; /* Dark text on bright gradient */
      /* UPDATED: Gradient from PURPLE to CYAN */
      background:linear-gradient(90deg,var(--accent1),var(--accent2)); 
      /* UPDATED: Shadow uses PURPLE accent */
      box-shadow: 0 4px 20px rgba(109, 40, 217, 0.3);
    }
    .big-btn:hover{
      opacity: 0.9;
      /* UPDATED: hover shadow uses PURPLE accent */
      box-shadow: 0 4px 25px rgba(109, 40, 217, 0.5);
      transform: translateY(-1px);
    }
    .alt-btn{
      color: var(--text-main);
      background: transparent;
      border-color: rgba(255,255,255,0.2);
    }
    .alt-btn:hover{
      background: var(--glass);
      border-color: var(--accent1); /* Changed hover border to PURPLE */
      color: var(--accent1); /* Changed hover text color to PURPLE */
    }

    /* Requirements Section Styling */
    .requirements-section {
        padding: 60px 20px;
        text-align: center;
    }
    .requirements-title {
        color: var(--muted);
        font-size: 20px;
        font-weight: 600;
        margin-bottom: 30px;
    }
    .requirements-list {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 24px;
        list-style: none;
        padding: 0;
        margin: 0;
    }
    .requirements-list li {
        font-size: 16px;
        font-weight: 500;
        color: var(--text-main);
        display: flex;
        align-items: center;
        gap: 8px;
    }
    .requirements-list li:before {
        content: '\2022'; /* Bullet point */
        color: var(--accent1); /* Bullet is now PURPLE */
        font-weight: bold;
        display: inline-block;
        width: 1em;
        margin-left: -1em;
    }


    /* Footer */
    footer{
      margin-top:24px;
      color:var(--muted);
      font-size:13px;
      padding: 16px 0;
      border-top: 1px solid rgba(255,255,255,0.05);
      width: 100%;
    }
    .footer-content {
        max-width: 1100px;
        margin: 0 auto;
        display:flex;
        justify-content:space-between;
        align-items:center;
        padding: 0 24px;
    }

    /* Responsiveness */
    @media(max-width:1050px) {
        /* Allow game cards to wrap on smaller screens */
        .game-card {
            width: 120px; 
        }
    }
    @media(max-width:920px){
      .main-title{
        font-size: 36px;
      }
      .feature-grid{
        grid-template-columns: repeat(2, 1fr); /* 2 columns on tablet */
      }
      .nav{
        display: none; /* Hide desktop nav on small screens */
      }
      .hero-buttons {
          flex-direction: column;
          gap: 10px;
      }
      .header{
        padding: 12px 24px;
      }
      .wrap{
        padding: 80px 16px 0;
      }
      .hero-section {
        padding: 40px 10px 60px;
      }
      .download-section, .games-section {
        padding: 40px 0;
      }
      .footer-content {
        flex-direction: column;
        gap: 8px;
        text-align: center;
      }
    }

    @media(max-width:550px){
      .feature-grid{
        grid-template-columns: 1fr; /* 1 column on mobile */
      }
      .main-title{
        font-size: 28px;
      }
      .game-card {
        width: 45%; /* Make game cards take up space on mobile */
        max-width: 150px;
      }
    }
  </style>
</head>
<body>
  
  <!-- Header / Navigation -->
  <header class="header">
    <div class="header-content">
      <a href="#" class="brand">
        <span class="brand-logo" data-lucide="infinity"></span>
        SenzoX
      </a>
      <!-- Navigation Links -->
      <nav class="nav">
        <a href="#features-section">Features</a>
        <a href="#games-section">Games</a>
        <a href="#download-section">Download</a>
        <a href="#requirements-section">Requirements</a> 
      </nav>
      <!-- "Download Now" Button in the Header -->
      <a class="big-btn" href="#download-section" style="padding: 10px 18px; font-size: 15px; margin-left: 20px;">
        <span data-lucide="download" style="width: 16px; height: 16px;"></span>
        Download Now
      </a>
    </div>
  </header>

  <div class="wrap">
    <div class="content-wrapper">

      <!-- 1. Centered Hero Content -->
      <section class="hero-section">
        <p class="pill" style="margin: 0 auto 20px; width: fit-content;">Advanced Digital Resource Platform</p>
        <h1 class="main-title">Unleash Your <span style="color: var(--accent2);">Digital Potential</span></h1>
        <p class="main-subtitle">
          SenzoX is the ultimate game enhancement client, offering powerful tools and features to elevate your gaming experience across multiple platforms.
        </p>
        
        <div class="hero-buttons">
            <a class="big-btn" href="#download-section" style="padding: 14px 30px;">
                <span data-lucide="download" style="width: 20px; height: 20px;"></span>
                Download SenzoX
            </a>
            <!-- Button links to the requirements section -->
            <a class="alt-btn" href="#requirements-section" style="padding: 14px 30px;">
                <span data-lucide="cpu" style="width: 20px; height: 20px;"></span>
                View System Requirements
            </a>
        </div>
      </section>

      <!-- 2. Feature Grid Section -->
      <section id="features-section" style="margin-top: 40px;">
        <h2 style="text-align: center; font-size: 32px; font-weight: 800; margin-bottom: 8px;">Powerful Features</h2>
        <p style="text-align: center; color: var(--muted); margin-bottom: 30px;">
            Everything you need to succeed with cutting-edge digital resources.
        </p>
        <div class="feature-grid">
            
            <div class="feature-card">
                <span class="icon-wrapper"><span data-lucide="bolt"></span></span>
                <h3>Lightning Fast</h3>
                <p>Optimized delivery system with minimal performance impact on your workflow.</p>
            </div>
            
            <div class="feature-card">
                <span class="icon-wrapper"><span data-lucide="shield"></span></span>
                <h3>Secure & Reliable</h3>
                <p>Advanced security protocols ensure your data and downloads are safe and verified.</p>
            </div>

            <div class="feature-card">
                <span class="icon-wrapper"><span data-lucide="target"></span></span>
                <h3>Precision Tools</h3>
                <p>Accurate and focused resources for a competitive edge in your projects.</p>
            </div>

            <div class="feature-card">
                <span class="icon-wrapper"><span data-lucide="layers"></span></span>
                <h3>Fully Customizable</h3>
                <p>Extensive configuration options to tailor features and content to your needs.</p>
            </div>

            <div class="feature-card">
                <span class="icon-wrapper"><span data-lucide="users"></span></span>
                <h3>Active Community</h3>
                <p>Join thousands of users with regular updates and dedicated support channels.</p>
            </div>

            <div class="feature-card">
                <span class="icon-wrapper"><span data-lucide="lock"></span></span>
                <h3>Protected Platform</h3>
                <p>Industry-standard protection safeguards your content and information.</p>
            </div>
        </div>
      </section>

      <!-- 3. Supported Games Section (New Content) -->
      <section id="games-section" class="games-section">
        <!-- The text is centered via the .games-section style -->
        <h2 style="font-size: 32px; font-weight: 800; margin-bottom: 8px;">Supported <span style="color: var(--accent2);">Games</span></h2>
        <p style="color: var(--muted); margin-bottom: 30px;">
            SenzoX supports all popular games with regular updates.
        </p>
        
        <!-- The grid items are centered via the .game-grid style -->
        <div class="game-grid">
            <!-- Game Card 1: Counter-Strike 2 (Simulated Logo) -->
            <div class="game-card">
                <div class="game-logo" style="background-color: #2c4273; color: #ff9900;">CS</div>
                <p class="game-name">Counter-Strike 2</p>
                <p class="game-support">Fully Supported</p>
            </div>
            
            <!-- Game Card 2: Valorant (Simulated Logo) -->
            <div class="game-card">
                <div class="game-logo" style="background-color: #ff4655;">V</div>
                <p class="game-name">Valorant</p>
                <p class="game-support">Fully Supported</p>
            </div>
            
            <!-- Game Card 3: Apex Legends (Simulated Logo) -->
            <div class="game-card">
                <div class="game-logo" style="background-color: #000; color: #d42028;">APEX</div>
                <p class="game-name">Apex Legends</p>
                <p class="game-support">Fully Supported</p>
            </div>
            
            <!-- Game Card 4: Fortnite (Simulated Logo) -->
            <div class="game-card">
                <div class="game-logo" style="background-color: #6300c8;">F</div>
                <p class="game-name">Fortnite</p>
                <p class="game-support">Fully Supported</p>
            </div>

            <!-- Game Card 5: Call of Duty (Simulated Logo) -->
            <div class="game-card">
                <div class="game-logo" style="background-color: #333333; font-size: 18px;">CoD</div>
                <p class="game-name">Call of Duty</p>
                <p class="game-support">Fully Supported</p>
            </div>
            
            <!-- Game Card 6: PUBG (Simulated Logo) -->
            <div class="game-card">
                <div class="game-logo" style="background-color: #f7a800;">PUBG</div>
                <p class="game-name">PUBG</p>
                <p class="game-support">Fully Supported</p>
            </div>
        </div>

        <!-- Additional Games Box is centered via its margin properties -->
        <div class="additional-games-box">
            <h3 style="color: var(--accent2); margin-top: 0;">+ 50+</h3>
            <p style="font-weight: 600;">Additional games</p>
            <p>
                We are constantly adding support for new games. Can't find your game? 
                Contact us and we will add it in the next update!
            </p>
            <a class="alt-btn" href="#" style="padding: 10px 20px; border-color: var(--accent2);">
                <span data-lucide="eye" style="width: 16px; height: 16px;"></span>
                View all games
            </a>
        </div>
      </section>
      <!-- END Supported Games Section -->


      <!-- 4. Downloads/CTA Section (Final Panel) -->
      <section id="download-section" class="download-section">
        <div class="panel download-card">
          <strong style="font-size:24px; display: block; margin-bottom: 20px;">Ready to Get Started?</strong>
          <p>
            Download the complete, single-file template to launch your own hub.
          </p>

          <div class="btn-group">
            <!-- Primary Button (Download) -->
            <a class="big-btn" href="/files/senzox-template.zip" download id="downloads">
              <span data-lucide="download" style="width: 20px; height: 20px;"></span>
              Download SenzoX Free
            </a>

            <!-- Secondary Button (View Requirements/Pro) - Now links to the requirements section -->
            <a class="alt-btn" href="#requirements-section" style="padding: 16px 20px;">
              <span data-lucide="cpu" style="width: 20px; height: 20px;"></span>
              View System Requirements
            </a>
          </div>

          <div style="display:flex;justify-content:space-between;align-items:center; margin-top: 15px;">
            <small class="muted">Version: 2.0</small>
            <small class="muted">Updated: Sep 2025</small>
          </div>
        </div>
      </section>

      <!-- 5. System Requirements Section (Anchored for scrolling) -->
      <section id="requirements-section" class="requirements-section">
        <div class="content-wrapper" style="max-width: 800px; padding: 20px;">
          <h2 class="requirements-title">System Requirements</h2>
          
          <!-- Requirements List (mimicking the horizontal layout from the image) -->
          <ul class="requirements-list">
            <li><span style="font-weight: 700; color: var(--accent2);">OS:</span> Windows 10/11 64-bit</li>
            <li><span style="font-weight: 700; color: var(--accent2);">RAM:</span> 4GB Minimum</li>
            <li><span style="font-weight: 700; color: var(--accent2);">Graphics:</span> DirectX 11+ Compatible</li>
            <li><span style="font-weight: 700; color: var(--accent2);">Storage:</span> 500MB Free Space</li>
          </ul>

          <h3 class="requirements-title" style="margin-top: 50px;">Supported Platforms</h3>
          
          <ul class="requirements-list">
              <li>PC / Desktop</li>
              <li>Chrome OS</li>
              <li>Modern Browsers</li>
          </ul>

          <p style="color: var(--muted); font-size: 14px; margin-top: 40px;">
            Note: Performance may vary based on individual hardware and network conditions.
          </p>
        </div>
      </section>
      <!-- END System Requirements Section -->

    </div>
  </div>

  <footer>
    <div class="footer-content">
      <div class="muted">© 2025 SenzoX. All Rights Reserved.</div>
      <div class="muted">Built for modern digital consumption.</div>
    </div>
  </footer>

  <script>
    // Initialize Lucide icons on the page
    lucide.createIcons();

    // Example of a custom function for the download link (optional)
    document.getElementById('downloads').addEventListener('click', () => {
        console.log('Download initiated for SenzoX Template.');
        // Add analytics or state tracking here
    });
  </script>
</body>
</html>
