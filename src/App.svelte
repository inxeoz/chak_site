<script>
  import logo from './assets/logo.svg';
  import { onMount } from "svelte";

  let isMobile = false;
  let activeSection = "home";

  onMount(() => {
    checkMobile();
    window.addEventListener("resize", checkMobile);
    return () => window.removeEventListener("resize", checkMobile);
  });

  function checkMobile() {
    isMobile = window.innerWidth < 768;
  }

  function setActiveSection(section) {
    activeSection = section;
  }

  function downloadFor(platform) {
    alert(`Downloading Chak for ${platform}...`);
    // Actual download functionality would be implemented here
  }
</script>

<main class={isMobile ? "mobile" : "desktop"}>
  <nav>
    <div class="logo">
      <img src={logo} alt="logo" />
      <h1>Chak</h1>
    </div>

    {#if isMobile}
      <button class="menu-button">
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
      </button>
    {:else}
      <ul class="nav-links">
        <li class:active={activeSection === "home"}>
          <button on:click={() => setActiveSection("home")}>Home</button>
        </li>
        <li class:active={activeSection === "features"}>
          <button on:click={() => setActiveSection("features")}>Features</button>
        </li>
        <li class:active={activeSection === "docs"}>
          <button on:click={() => setActiveSection("docs")}>Docs</button>
        </li>
        <li class:active={activeSection === "about"}>
          <button on:click={() => setActiveSection("about")}>About</button>
        </li>
      </ul>
    {/if}
  </nav>

  {#if activeSection === "home"}
    <section class="hero">
      <div class="hero-content">
        <h2>A New Generation <br> Version Control System</h2>
        <p>Crafted with Rust for unparalleled performance and reliability</p>

        <div class="action-buttons">
          <button class="download-button" on:click={() => downloadFor("linux")}>
            <svg viewBox="0 0 24 24" width="18" height="18">
              <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" fill="none" stroke="currentColor" stroke-width="2" />
              <path d="M7 10l5 5 5-5" fill="none" stroke="currentColor" stroke-width="2" />
              <path d="M12 15V3" fill="none" stroke="currentColor" stroke-width="2" />
            </svg>
            Linux
          </button>

          <button class="download-button" on:click={() => downloadFor("windows")}>
            <svg viewBox="0 0 24 24" width="18" height="18">
              <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" fill="none" stroke="currentColor" stroke-width="2" />
              <path d="M7 10l5 5 5-5" fill="none" stroke="currentColor" stroke-width="2" />
              <path d="M12 15V3" fill="none" stroke="currentColor" stroke-width="2" />
            </svg>
            Windows
          </button>

          <a href="https://github.com/chak-vcs/chak" class="github-button" target="_blank" rel="noopener">
            <svg viewBox="0 0 24 24" width="18" height="18">
              <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22" fill="none" stroke="currentColor" stroke-width="1.5" />
            </svg>
            GitHub
          </a>
        </div>
      </div>

      <div class="hero-visual">
        <div class="code-block">
          <pre><code>$ chak init
  Initializing repository...
$ chak branch feature-x
  Branch created: feature-x
$ chak commit -m "Add new features"
  Commit successful: a7d3f...</code></pre>
        </div>
      </div>
    </section>
  {/if}

  {#if activeSection === "features"}
    <section class="features">
      <h2>Features</h2>
      <div class="feature-grid">
        <div class="feature-card">
          <svg viewBox="0 0 24 24" width="32" height="32">
            <path d="M22 12c0-5.5-4.5-10-10-10S2 6.5 2 12s4.5 10 10 10 10-4.5 10-10z" fill="none" stroke="currentColor" stroke-width="1.5" />
            <path d="M16 12l-4 4-2-2" fill="none" stroke="currentColor" stroke-width="1.5" />
          </svg>
          <h3>Lightning Fast</h3>
          <p>Built with Rust for superior performance compared to traditional VCS</p>
        </div>

        <div class="feature-card">
          <svg viewBox="0 0 24 24" width="32" height="32">
            <path d="M12 2L2 7l10 5 10-5-10-5z" fill="none" stroke="currentColor" stroke-width="1.5" />
            <path d="M2 17l10 5 10-5" fill="none" stroke="currentColor" stroke-width="1.5" />
            <path d="M2 12l10 5 10-5" fill="none" stroke="currentColor" stroke-width="1.5" />
          </svg>
          <h3>Distributed</h3>
          <p>Fully distributed architecture for seamless collaboration</p>
        </div>

        <div class="feature-card">
          <svg viewBox="0 0 24 24" width="32" height="32">
            <path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9" fill="none" stroke="currentColor" stroke-width="1.5" />
            <path d="M13.73 21a2 2 0 0 1-3.46 0" fill="none" stroke="currentColor" stroke-width="1.5" />
          </svg>
          <h3>Smart Conflict Resolution</h3>
          <p>Advanced algorithms for intelligent merge conflict handling</p>
        </div>

        <div class="feature-card">
          <svg viewBox="0 0 24 24" width="32" height="32">
            <path d="M12 2a10 10 0 1 0 10 10A10 10 0 0 0 12 2zm0 16a1.5 1.5 0 1 1 1.5-1.5A1.5 1.5 0 0 1 12 18zm1-5.5c0 .5-.5 1-1 1s-1-.5-1-1V8c0-.5.5-1 1-1s1 .5 1 1z" fill="none" stroke="currentColor" stroke-width="1.5" />
          </svg>
          <h3>File-Level Permissions</h3>
          <p>Granular control over file access in collaborative environments</p>
        </div>
      </div>
    </section>
  {/if}

  {#if activeSection === "docs" || activeSection === "about"}
    <section class="placeholder">
      <h2>{activeSection === "docs" ? "Documentation" : "About Chak"}</h2>
      <p>This section is under development. Check back soon!</p>
    </section>
  {/if}

  <footer>
    <div class="footer-content">
      <div class="footer-logo">
        <img src={logo} alt="logo" />
        <span>Chak VCS</span>
      </div>

      <div class="footer-links">
        <a href="#">Privacy</a>
        <a href="#">License</a>
        <a href="#">Contact</a>
      </div>
    </div>
    <div class="copyright">
      © 2025 Chak Project. All rights reserved.
    </div>
  </footer>
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    background-color: #82c0cc;
    color: #001845;
  }

  main {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background-color: #489fb5;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .logo h1 {
    margin: 0;
    font-size: 1.8rem;
    font-weight: 600;
    color: #001845;
  }

  .nav-links {
    display: flex;
    list-style: none;
    gap: 2rem;
    margin: 0;
    padding: 0;
  }

  .nav-links li button {
    background: none;
    border: none;
    font-size: 1rem;
    color: #001845;
    cursor: pointer;
    padding: 0.5rem 0;
    position: relative;
    transition: color 0.3s;
  }

  .nav-links li.active button {
    color: #001845;
    font-weight: 500;
  }

  .nav-links li.active button::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 2px;
    background-color: #001845;
  }

  .menu-button {
    background: none;
    border: none;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    gap: 5px;
    padding: 5px;
  }

  .menu-button .bar {
    width: 24px;
    height: 2px;
    background-color: #001845;
    transition: all 0.3s;
  }

  .hero {
    display: flex;
    padding: 3rem 2rem;
    gap: 2rem;
    background-color: #82c0cc;
    min-height: 60vh;
    align-items: center;
  }

  .hero-content {
    flex: 1;
  }

  .hero-content h2 {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
    line-height: 1.2;
    color: #001845;
  }

  .hero-content p {
    font-size: 1.1rem;
    color: #001845;
    margin-bottom: 2rem;
    max-width: 500px;
  }

  .hero-visual {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .code-block {
    background-color: #001845;
    padding: 1.5rem;
    border-radius: 8px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 500px;
  }

  .code-block pre {
    margin: 0;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
    overflow-x: auto;
  }

  .code-block code {
    color: #82c0cc;
    line-height: 1.6;
  }

  .action-buttons {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .download-button, .github-button {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.75rem 1.5rem;
    border-radius: 6px;
    font-weight: 500;
    font-size: 1rem;
    cursor: pointer;
    transition: all 0.2s;
    text-decoration: none;
  }

  .download-button {
    background-color: #ede7e3;
    color: #001845;
    border: 1px solid #001845;
  }

  .download-button:hover {
    background-color: #001845;
    color: #ede7e3;
  }

  .github-button {
    background-color: #ede7e3;
    color: #001845;
    border: 1px solid #001845;
  }

  .github-button:hover {
    background-color: #001845;
    color: #ede7e3;
  }

  /* Features Section */
  .features {
    padding: 4rem 2rem;
    background-color: #82c0cc;
  }

  .features h2 {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 3rem;
    color: #001845;
  }

  .feature-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .feature-card {
    padding: 2rem;
    background-color: #ede7e3;
    border-radius: 8px;
    transition: transform 0.3s, box-shadow 0.3s;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .feature-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  }

  .feature-card svg {
    margin-bottom: 1.5rem;
    color: #001845;
  }

  .feature-card h3 {
    font-size: 1.3rem;
    margin-bottom: 1rem;
    color: #001845;
  }

  .feature-card p {
    color: #001845;
    line-height: 1.6;
  }

  /* Placeholder Sections */
  .placeholder {
    padding: 4rem 2rem;
    text-align: center;
    background-color: #82c0cc;
    min-height: 50vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .placeholder h2 {
    font-size: 2rem;
    margin-bottom: 1rem;
    color: #001845;
  }

  .placeholder p {
    color: #001845;
    font-size: 1.1rem;
  }

  /* Footer */
  footer {
    background-color: #489fb5;
    padding: 2rem;
    margin-top: auto;
  }

  .footer-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
    padding-bottom: 1.5rem;
    border-bottom: 1px solid #ede7e3;
  }

  .footer-logo {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: #001845;
  }

  .footer-links {
    display: flex;
    gap: 1.5rem;
  }

  .footer-links a {
    color: #001845;
    text-decoration: none;
    transition: color 0.2s;
  }

  .footer-links a:hover {
    color: #001845;
  }

  .copyright {
    text-align: center;
    color: #001845;
    font-size: 0.9rem;
    margin-top: 1.5rem;
  }

  /* Mobile Styles */
  .mobile .hero {
    flex-direction: column;
    padding: 2rem 1rem;
  }

  .mobile .hero-content h2 {
    font-size: 2rem;
  }

  .mobile .feature-grid {
    grid-template-columns: 1fr;
  }

  .mobile .footer-content {
    flex-direction: column;
    gap: 1.5rem;
  }

  .mobile .action-buttons {
    justify-content: center;
  }

  .mobile .code-block {
    font-size: 0.9rem;
  }

  @media (max-width: 768px) {
    nav {
      padding: 1rem;
    }

    .logo h1 {
      font-size: 1.5rem;
    }

    .hero-content h2 {
      font-size: 1.8rem;
    }

    .features, .placeholder {
      padding: 3rem 1rem;
    }

    .footer-content {
      flex-direction: column;
      gap: 1.5rem;
    }

    .footer-links {
      flex-direction: column;
      gap: 0.8rem;
      align-items: center;
    }
  }
</style>