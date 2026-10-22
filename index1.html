<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Crystal Defender & Collector</title>
  <!-- Подключаем p5.js -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/p5.min.js"></script>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #0b0e14;
      color: #ffffff;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      overflow: hidden;
    }
    #game-container {
      box-shadow: 0 0 30px rgba(0, 240, 255, 0.3);
      border-radius: 12px;
      overflow: hidden;
      border: 2px solid #1a233a;
    }
    .instructions {
      margin-top: 15px;
      font-size: 14px;
      color: #8a99ad;
      text-align: center;
    }
  </style>
</head>
<body>

<div id="game-container"></div>
<div class="instructions">Управление: <b>Стрелки / WASD</b> для движения | <b>Пробел</b> для выстрела | <b>Мышка</b> для перезапуска</div>

<script>
let player;
let crystals = [];
let enemies = [];
let bullets = [];
let particles = [];
let score = 0;
let level = 1;
let gameOver = false;

function setup() {
  let canvas = createCanvas(800, 500);
  canvas.parent('game-container');
  player = new Player();
  
  // Создаём начальные кристаллы
  for (let i = 0; i < 5; i++) {
    crystals.push(new Crystal());
  }
}

function draw() {
  background(11, 14, 20);

  // Сетка на фоне
  stroke(20, 30, 50);
  strokeWeight(1);
  for (let x = 0; x < width; x += 40) line(x, 0, x, height);
  for (let y = 0; y < height; y += 40) line(0, y, width, y);

  if (!gameOver) {
    // Спавн врагов
    if (frameCount % max(30, 100 - level * 10) === 0) {
      enemies.push(new Enemy());
    }

    // Игрок
    player.update();
    player.display();

    // Выстрелы
    for (let i = bullets.length - 1; i >= 0; i--) {
      bullets[i].update();
      bullets[i].display();
      
      // Попадание во врагов
      for (let j = enemies.length - 1; j >= 0; j--) {
        if (bullets[i] && bullets[i].hits(enemies[j])) {
          createExplosion(enemies[j].x, enemies[j].y, color(255, 50, 100));
          enemies.splice(j, 1);
          bullets.splice(i, 1);
          score += 15;
          break;
        }
      }
      
      if (bullets[i] && bullets[i].offscreen()) {
        bullets.splice(i, 1);
      }
    }

    // Кристаллы
    for (let i = crystals.length - 1; i >= 0; i--) {
      crystals[i].display();
      if (player.collects(crystals[i])) {
        createExplosion(crystals[i].x, crystals[i].y, color(0, 255, 200));
        crystals.splice(i, 1);
        crystals.push(new Crystal());
        score += 10;
        if (score % 50 === 0) level++;
      }
    }

    // Враги
    for (let i = enemies.length - 1; i >= 0; i--) {
      enemies[i].update();
      enemies[i].display();

      if (player.hits(enemies[i])) {
        createExplosion(player.x, player.y, color(255, 200, 0));
        gameOver = true;
      }
    }

    // Частицы
    for (let i = particles.length - 1; i >= 0; i--) {
      particles[i].update();
      particles[i].display();
      if (particles[i].isFinished()) {
        particles.splice(i, 1);
      }
    }

    // Текст счёта
    fill(255);
    noStroke();
    textSize(18);
    textAlign(LEFT, TOP);
    text(`Счёт: ${score}`, 20, 20);
    text(`Уровень: ${level}`, 20, 45);
  } else {
    // Экран Game Over
    textAlign(CENTER, CENTER);
    fill(255, 50, 100);
    textSize(36);
    text("GAME OVER", width / 2, height / 2 - 20);
    fill(255);
    textSize(18);
    text(`Итоговый счёт: ${score}`, width / 2, height / 2 + 20);
    textSize(14);
    fill(150);
    text("Kликните мышкой, чтобы играть снова", width / 2, height / 2 + 60);
  }
}

function keyPressed() {
  if (key === ' ' && !gameOver) {
    bullets.push(new Bullet(player.x, player.y));
  }
}

function mousePressed() {
  if (gameOver) {
    score = 0;
    level = 1;
    enemies = [];
    bullets = [];
    crystals = [];
    for (let i = 0; i < 5; i++) crystals.push(new Crystal());
    player = new Player();
    gameOver = false;
  }
}

class Player {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
    this.size = 24;
    this.speed = 4;
  }

  update() {
    if (keyIsDown(LEFT_ARROW) || keyIsDown(65)) this.x -= this.speed;
    if (keyIsDown(RIGHT_ARROW) || keyIsDown(68)) this.x += this.speed;
    if (keyIsDown(UP_ARROW) || keyIsDown(87)) this.y -= this.speed;
    if (keyIsDown(DOWN_ARROW) || keyIsDown(83)) this.y += this.speed;

    this.x = constrain(this.x, this.size, width - this.size);
    this.y = constrain(this.y, this.size, height - this.size);
  }

  display() {
    fill(0, 240, 255);
    stroke(255);
    strokeWeight(2);
    ellipse(this.x, this.y, this.size);
  }

  collects(crystal) {
    let d = dist(this.x, this.y, crystal.x, crystal.y);
    return d < this.size / 2 + crystal.size / 2;
  }

  hits(enemy) {
    let d = dist(this.x, this.y, enemy.x, enemy.y);
    return d < this.size / 2 + enemy.size / 2;
  }
}

class Crystal {
  constructor() {
    this.x = random(40, width - 40);
    this.y = random(40, height - 40);
    this.size = 16;
  }

  display() {
    fill(0, 255, 150);
    stroke(255);
    strokeWeight(1);
    push();
    translate(this.x, this.y);
    rotate(frameCount * 0.05);
    rectMode(CENTER);
    rect(0, 0, this.size, this.size);
    pop();
  }
}

class Enemy {
  constructor() {
    if (random(1) < 0.5) {
      this.x = random(1) < 0.5 ? 0 : width;
      this.y = random(height);
    } else {
      this.x = random(width);
      this.y = random(1) < 0.5 ? 0 : height;
    }
    this.size = 20;
    this.speed = random(1.5, 2.5) + level * 0.2;
  }

  update() {
    let angle = atan2(player.y - this.y, player.x - this.x);
    this.x += cos(angle) * this.speed;
    this.y += sin(angle) * this.speed;
  }

  display() {
    fill(255, 50, 100);
    stroke(255);
    strokeWeight(1.5);
    ellipse(this.x, this.y, this.size);
  }
}

class Bullet {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.size = 8;
    this.speed = 7;
    // Направление полёта к курсору мыши
    let angle = atan2(mouseY - y, mouseX - x);
    this.vx = cos(angle) * this.speed;
    this.vy = sin(angle) * this.speed;
  }

  update() {
    this.x += this.vx;
    this.y += this.vy;
  }

  display() {
    fill(255, 255, 0);
    noStroke();
    ellipse(this.x, this.y, this.size);
  }

  hits(enemy) {
    let d = dist(this.x, this.y, enemy.x, enemy.y);
    return d < this.size / 2 + enemy.size / 2;
  }

  offscreen() {
    return this.x < 0 || this.x > width || this.y < 0 || this.y > height;
  }
}

class Particle {
  constructor(x, y, col) {
    this.x = x;
    this.y = y;
    this.col = col;
    this.vx = random(-3, 3);
    this.vy = random(-3, 3);
    this.alpha = 255;
  }

  update() {
    this.x += this.vx;
    this.y += this.vy;
    this.alpha -= 8;
  }

  display() {
    noStroke();
    fill(red(this.col), green(this.col), blue(this.col), this.alpha);
    ellipse(this.x, this.y, 6);
  }

  isFinished() {
    return this.alpha < 0;
  }
}

function createExplosion(x, y, col) {
  for (let i = 0; i < 15; i++) {
    particles.push(new Particle(x, y, col));
  }
}
</script>

</body>
</html>
