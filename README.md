<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>My Blog Website</title>
<style>
  /* Basic Reset & Styling */
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  header {
    background-color: #333;
    padding: 1em;
    color: #fff;
  }

  header h1 {
    margin-bottom: 0.5em;
  }

  nav ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
  }

  nav li {
    margin-right: 1em;
  }

  nav a {
    color: #fff;
    text-decoration: none;
    padding: 0.5em;
  }

  nav a.active,
  nav a:hover {
    background-color: #555;
    border-radius: 4px;
  }

  main {
    flex: 1;
    padding: 1em;
    max-width: 1000px;
    margin: auto;
  }

  section {
    display: none; /* Hidden by default, show via JS */
  }

  section.active {
    display: block;
  }

  .article {
    background-color: #f4f4f4;
    margin-bottom: 1em;
    padding: 1em;
    border-radius: 8px;
  }

  button {
    padding: 0.5em 1em;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  button:hover {
    background-color: #0056b3;
  }

  footer {
    background-color: #333;
    color: #fff;
    text-align: center;
    padding: 1em;
  }

  /* Responsive design */
  @media(max-width: 600px) {
    nav ul {
      flex-direction: column;
    }
    nav li {
      margin-bottom: 0.5em;
    }
  }
</style>
</head>
<body>
<header>
  <h1>My Blog</h1>
  <nav>
    <ul>
      <li><a href="#" id="nav-home" class="active">Home</a></li>
      <li><a href="#" id="nav-blog">Blog</a></li>
      <li><a href="#" id="nav-about">About</a></li>
    </ul>
  </nav>
</header>

<main>
  <!-- Home Page -->
  <section id="home" class="active">
    <h2>Welcome to My Blog</h2>
    <p>This blog started as a personal space to document my coding journey, late nights, early sips, bugs, breakthroughs, and everything in between. whether it's a new framework, a trick bug fix, or just some thoughts on devv life.</p>
    <button id="aboutBtn">Learn More About This Blog</button>
    <div id="aboutInfo" style="margin-top:1em; display:none;">
      <h3>About This Blog</h3>
      <p>This blog is a demo project showcasing multi-page navigation, responsiveness, and interactivity. I share it all here with a dose of caffeine and curiosity. Let's code, learn, and and caffeine together</p>
    </div>
  </section>

  <!-- Blog List Page -->
  <section id="blog">
    <h2>Blog Articles</h2>
    <div class="articles">
      <article class="article">
        <h3>Understanding JavaScript</h3>
        <p>A beginner's guide to JavaScript fundamentals.</p>
        <button class="read-more" data-post="post1">Read More</button>
      </article>
      <article class="article">
        <h3>CSS Tips & Tricks</h3>
        <p>Improve your CSS skills with these helpful tips.</p>
        <button class="read-more" data-post="post2">Read More</button>
      </article>
    </div>
  </section>

  <!-- Blog Post 1 -->
  <section id="post1">
    <h2>Understanding JavaScript</h2>
    <p><em>Published: May 1, 2025</em></p>
    <article>
      <h3>Introduction</h3>
      <p>This article explains the basics of JavaScript programming language, including variables, functions, and events.</p>
    </article>
    <button class="back-to-blog">Back to Blog</button>
  </section>

  <!-- Blog Post 2 -->
  <section id="post2">
    <h2>CSS Tips & Tricks</h2>
    <p><em>Published: March 2, 2024</em></p>
    <article>
      <h3>Styling Tips</h3>
      <p>Discover effective techniques for styling websites with CSS, including flexbox, grid, and responsiveness.</p>
    </article>
    <button class="back-to-blog">Back to Blog</button>
  </section>

  <!-- About Page (optional, could be part of home or separate) -->
  <!-- Not used here separately but can be added if needed -->
</main>

<footer>
  <p>&copy; 2024 My Blog</p>
</footer>

<script>
  // JavaScript for interactivity and navigation

  document.addEventListener('DOMContentLoaded', () => {
    // Navigation links
    const navHome = document.getElementById('nav-home');
    const navBlog = document.getElementById('nav-blog');
    const navAbout = document.getElementById('nav-about');

    // Sections
    const sections = document.querySelectorAll('main section');

    function showSection(id) {
      sections.forEach(sec => {
        sec.classList.toggle('active', sec.id === id);
      });
      // Update active link styling
      document.querySelectorAll('nav a').forEach(link => {
        link.classList.toggle('active', link.id === 'nav-' + id);
      });
    }

    // Navigation event handlers
    document.getElementById('nav-home').addEventListener('click', (e) => {
      e.preventDefault();
      showSection('home');
    });
    document.getElementById('nav-blog').addEventListener('click', (e) => {
      e.preventDefault();
      showSection('blog');
    });
    document.getElementById('nav-about').addEventListener('click', (e) => {
      e.preventDefault();
      showSection('home'); // Or add a dedicated about section
    });

    // 'Learn More' button on Home
    document.getElementById('aboutBtn').addEventListener('click', () => {
      const aboutInfo = document.getElementById('aboutInfo');
      aboutInfo.style.display = aboutInfo.style.display === 'none' ? 'block' : 'none';
    });

    // Handle "Read More" buttons in blog list
    document.querySelectorAll('.read-more').forEach(btn => {
      btn.addEventListener('click', () => {
        const postId = btn.getAttribute('data-post');
        showSection(postId);
      });
    });

    // Back buttons in posts
    document.querySelectorAll('.back-to-blog').forEach(btn => {
      btn.addEventListener('click', () => {
        showSection('blog');
      });
    });
  });
</script>
</body>
</html>
