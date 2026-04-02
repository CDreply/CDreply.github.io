---
layout: default
title: 🎮 小游戏乐园
---

<style>
  /* ===== 全局重置 ===== */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: #0a0a1a;
    color: #e0e0e0;
    font-family: 'Segoe UI', 'Microsoft YaHei', 'PingFang SC', sans-serif;
    min-height: 100vh;
  }

  /* ===== 页头 ===== */
  .site-header {
    text-align: center;
    padding: 60px 20px 40px;
    position: relative;
  }

  .site-header::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse at 20% 20%, rgba(120,40,200,0.12) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 80%, rgba(40,100,255,0.08) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
  }

  .site-title {
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 900;
    background: linear-gradient(135deg, #7DF9FF, #A78BFA, #FF6B9D);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    position: relative;
    z-index: 1;
    line-height: 1.2;
    margin-bottom: 12px;
  }

  .site-subtitle {
    font-size: 1rem;
    color: rgba(255,255,255,0.4);
    position: relative;
    z-index: 1;
    letter-spacing: 2px;
  }

  /* ===== 游戏网格 ===== */
  .games-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 24px;
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* ===== 游戏卡片 ===== */
  .game-card {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 20px;
    overflow: hidden;
    transition: transform 0.25s ease, box-shadow 0.25s ease, border-color 0.25s ease;
    text-decoration: none;
    display: flex;
    flex-direction: column;
  }

  .game-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 16px 48px rgba(125,249,255,0.15);
    border-color: rgba(125,249,255,0.3);
  }

  /* 卡片封面区域 */
  .card-cover {
    height: 160px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 72px;
    position: relative;
    overflow: hidden;
  }

  .card-cover::after {
    content: '';
    position: absolute;
    inset: 0;
    background: inherit;
    filter: blur(30px) opacity(0.4);
    transform: scale(1.5);
  }

  .card-cover-emoji {
    position: relative;
    z-index: 1;
    filter: drop-shadow(0 0 20px currentColor);
    animation: float 3s ease-in-out infinite;
  }

  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50%       { transform: translateY(-8px); }
  }

  /* 卡片内容 */
  .card-body {
    padding: 20px;
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .card-title {
    font-size: 1.2rem;
    font-weight: 700;
    color: #fff;
  }

  .card-desc {
    font-size: 0.85rem;
    color: rgba(255,255,255,0.5);
    line-height: 1.6;
    flex: 1;
  }

  .card-tags {
    display: flex;
    gap: 6px;
    flex-wrap: wrap;
    margin-top: 4px;
  }

  .tag {
    font-size: 11px;
    padding: 2px 10px;
    border-radius: 20px;
    font-weight: 600;
    letter-spacing: 0.5px;
  }

  /* 卡片底部按钮 */
  .card-footer {
    padding: 0 20px 20px;
  }

  .play-btn {
    display: block;
    width: 100%;
    text-align: center;
    padding: 10px;
    border-radius: 12px;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 1px;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.15s;
  }

  .play-btn:hover { opacity: 0.85; transform: scale(1.02); }
  .play-btn:active { transform: scale(0.97); }

  /* ===== 占位卡片（coming soon）===== */
  .game-card.coming-soon {
    opacity: 0.45;
    cursor: not-allowed;
    pointer-events: none;
  }

  .game-card.coming-soon .card-cover-emoji {
    animation: none;
    filter: grayscale(1);
  }

  /* ===== 页脚 ===== */
  .site-footer {
    text-align: center;
    padding: 30px;
    color: rgba(255,255,255,0.2);
    font-size: 13px;
    border-top: 1px solid rgba(255,255,255,0.05);
    position: relative;
    z-index: 1;
  }

  /* ===== 响应式 ===== */
  @media (max-width: 480px) {
    .games-grid { grid-template-columns: 1fr; gap: 16px; padding: 0 16px 60px; }
    .site-header { padding: 40px 16px 30px; }
  }
</style>

<header class="site-header">
  <h1 class="site-title">🎮 小游戏乐园</h1>
  <p class="site-subtitle">休闲 · 益智 · 好玩</p>
</header>

<main class="games-grid">

  <!-- ===== 贪吃蛇 ===== -->
  <a class="game-card" href="games/snake.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #0d0d1f, #1a2a4a);">
      <span class="card-cover-emoji">🐍</span>
    </div>
    <div class="card-body">
      <div class="card-title">贪吃蛇</div>
      <div class="card-desc">经典贪吃蛇升级版！收集道具触发特效，越吃越长越难控制，挑战你的最高分！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(125,249,255,0.15);color:#7DF9FF;">益智</span>
        <span class="tag" style="background:rgba(167,139,250,0.15);color:#A78BFA;">道具</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">单人</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#7DF9FF,#3B5BDB);color:#0a0a1a;">▶ 开始游戏</span>
    </div>
  </a>

  <!-- ===== 占位：更多游戏即将到来 ===== -->
  <div class="game-card coming-soon">
    <div class="card-cover" style="background: linear-gradient(135deg, #1a1a1a, #2a2a2a);">
      <span class="card-cover-emoji">🧩</span>
    </div>
    <div class="card-body">
      <div class="card-title">俄罗斯方块</div>
      <div class="card-desc">敬请期待……</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(255,255,255,0.05);color:rgba(255,255,255,0.3);">即将上线</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:rgba(255,255,255,0.05);color:rgba(255,255,255,0.3);">🔒 敬请期待</span>
    </div>
  </div>

  <div class="game-card coming-soon">
    <div class="card-cover" style="background: linear-gradient(135deg, #1a1a1a, #2a2a2a);">
      <span class="card-cover-emoji">💣</span>
    </div>
    <div class="card-body">
      <div class="card-title">扫雷</div>
      <div class="card-desc">敬请期待……</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(255,255,255,0.05);color:rgba(255,255,255,0.3);">即将上线</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:rgba(255,255,255,0.05);color:rgba(255,255,255,0.3);">🔒 敬请期待</span>
    </div>
  </div>

</main>

<footer class="site-footer">
  Made with ❤️ · Powered by GitHub Pages
</footer>
