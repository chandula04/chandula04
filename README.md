<div align="center">
  <div class="glass-container">
    <h1>🌸 Welcome to My GitHub Profile 🌸</h1>
    <p>A passionate developer crafting elegant solutions with code.</p>
    
    <!-- Animated Coding Languages -->
    <div class="skills">
      <span class="skill">Python</span>
      <span class="skill">JavaScript</span>
      <span class="skill">TypeScript</span>
      <span class="skill">React</span>
      <span class="skill">Node.js</span>
    </div>
    
    <!-- Social Links -->
    <div class="social-links">
      <a href="https://twitter.com/yourusername" target="_blank">Twitter</a> |
      <a href="https://linkedin.com/in/yourusername" target="_blank">LinkedIn</a> |
      <a href="https://yourwebsite.com" target="_blank">Portfolio</a>
    </div>
  </div>

  <!-- Cherry Blossom Effect -->
  <canvas id="blossomCanvas"></canvas>
</div>

<style>
  body {
    margin: 0;
    padding: 0;
    background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
    font-family: 'Arial', sans-serif;
    overflow-x: hidden;
  }

  .glass-container {
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(10px);
    border-radius: 15px;
    padding: 40px;
    margin: 20px auto;
    max-width: 600px;
    box-shadow: 0 8px 32px rgba(31, 38, 135, 0.37);
    border: 1px solid rgba(255, 255, 255, 0.18);
    text-align: center;
    position: relative;
    z-index: 1;
  }

  h1 {
    color: #333;
    font-size: 2.5em;
    margin-bottom: 10px;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  p {
    color: #555;
    font-size: 1.2em;
    margin-bottom: 20px;
  }

  .skills {
    display: flex;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;
    margin: 20px 0;
  }

  .skill {
    background: rgba(255, 255, 255, 0.2);
    padding: 10px 20px;
    border-radius: 20px;
    color: #333;
    font-weight: bold;
    transition: transform 0.3s ease, background 0.3s ease;
    animation: float 3s ease-in-out infinite;
  }

  .skill:nth-child(2) { animation-delay: 0.5s; }
  .skill:nth-child(3) { animation-delay: 1s; }
  .skill:nth-child(4) { animation-delay: 1.5s; }
  .skill:nth-child(5) { animation-delay: 2s; }

  .skill:hover {
    transform: scale(1.1);
    background: rgba(255, 255, 255, 0.3);
  }

  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
  }

  .social-links a {
    color: #007bff;
    text-decoration: none;
    margin: 0 10px;
    font-size: 1.1em;
    transition: color 0.3s ease;
  }

  .social-links a:hover {
    color: #ff6f91;
  }

  #blossomCanvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
    pointer-events: none;
  }
</style>

<script>
  const canvas = document.getElementById('blossomCanvas');
  const ctx = canvas.getContext('2d');

  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  const petals = [];
  const petalCount = 50;

  class Petal {
    constructor() {
      this.x = Math.random() * canvas.width;
      this.y = Math.random() * canvas.height * 0.5;
      this.size = Math.random() * 10 + 5;
      this.speedX = Math.random() * 2 - 1;
      this.speedY = Math.random() * 2 + 1;
      this.angle = Math.random() * 360;
    }

    update() {
      this.x += this.speedX;
      this.y += this.speedY;
      this.angle += 0.1;
      if (this.y > canvas.height || this.x < 0 || this.x > canvas.width) {
        this.x = Math.random() * canvas.width;
        this.y = -10;
        this.speedX = Math.random() * 2 - 1;
        this.speedY = Math.random() * 2 + 1;
      }
    }

    draw() {
      ctx.save();
      ctx.translate(this.x, this.y);
      ctx.rotate(this.angle * Math.PI / 180);
      ctx.fillStyle = 'rgba(255, 182, 193, 0.8)';
      ctx.beginPath();
      ctx.ellipse(0, 0, this.size, this.size / 2, 0, 0, Math.PI * 2);
      ctx.fill();
      ctx.restore();
    }
  }

  for (let i = 0; i < petalCount; i++) {
    petals.push(new Petal());
  }

  function animate() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    petals.forEach(petal => {
      petal.update();
      petal.draw();
    });
    requestAnimationFrame(animate);
  }

  animate();

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });
</script>
