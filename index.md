---
layout: default
title: 🎮 沉答Ai小游戏乐园
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
    padding: 60px 20px 20px;
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

  /* ===== 分类导航标签 ===== */
  .category-nav {
    display: flex;
    justify-content: center;
    gap: 12px;
    padding: 20px 20px 10px;
    position: relative;
    z-index: 1;
    flex-wrap: wrap;
  }

  .category-tag {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 8px 20px;
    border-radius: 24px;
    font-size: 14px;
    font-weight: 600;
    text-decoration: none;
    transition: transform 0.2s, box-shadow 0.2s;
    letter-spacing: 0.5px;
  }

  .category-tag:hover {
    transform: translateY(-2px);
  }

  .category-tag.primary {
    background: linear-gradient(135deg, rgba(125,249,255,0.15), rgba(167,139,250,0.15));
    border: 1px solid rgba(125,249,255,0.3);
    color: #7DF9FF;
  }
  .category-tag.primary:hover { box-shadow: 0 4px 20px rgba(125,249,255,0.2); }

  .category-tag.tool {
    background: rgba(74,222,128,0.1);
    border: 1px solid rgba(74,222,128,0.25);
    color: #4ADE80;
  }
  .category-tag.tool:hover { box-shadow: 0 4px 20px rgba(74,222,128,0.15); }

  .category-tag.misc {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.1);
    color: rgba(255,255,255,0.4);
    font-size: 12px;
    padding: 6px 14px;
  }
  .category-tag.misc:hover { color: rgba(255,255,255,0.6); border-color: rgba(255,255,255,0.2); }

  /* ===== 分区标题 ===== */
  .section-label {
    max-width: 1100px;
    margin: 30px auto 16px;
    padding: 0 24px;
    position: relative;
    z-index: 1;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-label .label-text {
    font-size: 13px;
    font-weight: 700;
    color: rgba(255,255,255,0.3);
    text-transform: uppercase;
    letter-spacing: 3px;
    white-space: nowrap;
  }

  .section-label .label-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, rgba(255,255,255,0.08), transparent);
  }

  /* ===== 游戏网格 ===== */
  .games-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 24px;
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 24px 40px;
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
  <h1 class="site-title">🎮 沉答Ai小游戏乐园</h1>
  <p class="site-subtitle">余风清韵 & WorkBuddy 共同努力打造</p>
</header>

<nav class="category-nav">
  <a class="category-tag primary" href="#games">🎮 小游戏</a>
  <a class="category-tag tool" href="XGJ/index.html">🔧 小工具</a>
  <a class="category-tag misc" href="JDSH/index.html">夹带私货</a>
</nav>

<div class="section-label"><span class="label-text">🎮 小游戏</span><span class="label-line"></span></div>

<main class="games-grid" id="games">

  <!-- ===== 贪吃蛇 ===== -->
  <a class="game-card" href="games/snake.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #0d0d1f, #1a2a4a);">
      <span class="card-cover-emoji">🐍</span>
    </div>
    <div class="card-body">
      <div class="card-title">贪吃蛇</div>
      <div class="card-desc">全新双人模式上线！支持道具特效、多人对战，越吃越长越难控制，挑战你的最高分！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(125,249,255,0.15);color:#7DF9FF;">益智</span>
        <span class="tag" style="background:rgba(167,139,250,0.15);color:#A78BFA;">道具</span>
        <span class="tag" style="background:rgba(0,170,255,0.15);color:#0af;">双人对战</span>
        <span class="tag" style="background:rgba(255,107,157,0.15);color:#FF6B9D;">版本1.2</span>
        <span class="tag" style="background:rgba(34,211,238,0.12);color:#22d3ee;">📱 移动适配</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#7DF9FF,#3B5BDB);color:#0a0a1a;">▶ 开始游戏 (v1.2)</span>
    </div>
  </a>

  <!-- ===== 沉淀方块 ===== -->
  <a class="game-card" href="games/tetris_v1.1.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #1a0d2a, #2d1b4a);">
      <span class="card-cover-emoji">🧩</span>
    </div>
    <div class="card-body">
      <div class="card-title">沉淀方块</div>
      <div class="card-desc">经典方块沉淀游戏！炸弹道具、时间计时、操作统计，PC两栏新布局，体验全面升级！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(255,107,157,0.15);color:#FF6B9D;">益智</span>
        <span class="tag" style="background:rgba(167,139,250,0.15);color:#A78BFA;">策略</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">单人</span>
        <span class="tag" style="background:rgba(255,159,28,0.15);color:#FF9F1C;">道具</span>
        <span class="tag" style="background:rgba(255,107,157,0.15);color:#FF6B9D;">v1.1</span>
        <span class="tag" style="background:rgba(34,211,238,0.12);color:#22d3ee;">📱 移动适配</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#FF6B9D,#C62A88);color:#fff;">▶ 开始游戏 (v1.1)</span>
    </div>
  </a>

  <!-- ===== 沉哒乒乓 ===== -->
  <a class="game-card" href="games/PPQ2.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #001a2a, #0d2240);">
      <span class="card-cover-emoji">🏓</span>
    </div>
    <div class="card-body">
      <div class="card-title">沉哒乒乓</div>
      <div class="card-desc">新增双人PvP模式！挑战AI或与朋友本地对战，连击系统、连胜记录，v2.1全新体验！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(0,170,255,0.15);color:#0af;">竞技</span>
        <span class="tag" style="background:rgba(170,85,255,0.15);color:#a5f;">双人对战</span>
        <span class="tag" style="background:rgba(255,187,0,0.15);color:#fb0;">连击系统</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">AI可选</span>
        <span class="tag" style="background:rgba(34,211,238,0.12);color:#22d3ee;">📱 移动适配</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#0af,#06c);color:#fff;">▶ 开始游戏 (v2.1)</span>
    </div>
  </a>

  <!-- ===== 赛博五子棋 ===== -->
  <a class="game-card" href="games/cyberpunk-gomoku-v1.2.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #0a0a1f, #1a1a3a);">
      <span class="card-cover-emoji">⚡</span>
    </div>
    <div class="card-body">
      <div class="card-title">赛博五子棋</div>
      <div class="card-desc">赛博朋克风格五子棋！人机对战/双人对战自由切换，霓虹灯效、电子音效，全新视觉体验！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(0,255,255,0.15);color:#0ff;">赛博朋克</span>
        <span class="tag" style="background:rgba(255,0,255,0.15);color:#f0f;">电子音效</span>
        <span class="tag" style="background:rgba(255,187,0,0.15);color:#fb0;">人机对战</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">双人</span>
        <span class="tag" style="background:rgba(34,211,238,0.12);color:#22d3ee;">📱 移动适配</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#0ff,#0aa);color:#0a0a1a;">▶ 开始游戏 (v1.2)</span>
    </div>
  </a>

  <!-- ===== 简约围棋 ===== -->
  <a class="game-card" href="games/plain-go-v1.2.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #2a241a, #3a2a1a);">
      <span class="card-cover-emoji">🎴</span>
    </div>
    <div class="card-body">
      <div class="card-title">简约围棋</div>
      <div class="card-desc">经典黑白对弈，人机/双人模式可选！AI执白、温润落子音效、虚着悔棋，适合新老棋手！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(0,0,0,0.15);color:#222;">围棋</span>
        <span class="tag" style="background:rgba(255,255,255,0.15);color:#fff;">策略</span>
        <span class="tag" style="background:rgba(255,187,0,0.15);color:#fb0;">人机对战</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">双人</span>
        <span class="tag" style="background:rgba(255,107,157,0.12);color:#FF6B9D;">v1.2</span>
        <span class="tag" style="background:rgba(34,211,238,0.12);color:#22d3ee;">📱 移动适配</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#222,#000);color:#fff;">▶ 开始游戏 (v1.2)</span>
    </div>
  </a>

  <!-- ===== 几何空战 ===== -->
  <a class="game-card" href="games/JHKZ_v2.2.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #0a0a0f, #0f0f2a);">
      <span class="card-cover-emoji">✈️</span>
    </div>
    <div class="card-body">
      <div class="card-title">几何空战</div>
      <div class="card-desc">科幻空战射击！多种模式可选，炫酷粒子特效，触屏操控，v2.2 全新升级！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(0,255,255,0.15);color:#0ff;">射击</span>
        <span class="tag" style="background:rgba(255,0,255,0.15);color:#f0f;">科幻</span>
        <span class="tag" style="background:rgba(255,170,0,0.15);color:#fa0;">触屏</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">v2.2</span>
        <span class="tag" style="background:rgba(34,211,238,0.12);color:#22d3ee;">📱 移动适配</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#0ff,#f0f);color:#0a0a1a;">▶ 开始游戏 (v2.2)</span>
    </div>
  </a>

  <!-- ===== 战术突击 ===== -->
  <a class="game-card" href="games/cs2_action_v1.8.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #0a0a0a, #1a1a1a);">
      <span class="card-cover-emoji">🔫</span>
    </div>
    <div class="card-body">
      <div class="card-title">战术突击</div>
      <div class="card-desc">CS2风格FPS射击！多种武器切换、HUD血量弹药、小地图、波次防守，v1.8爽快射击体验！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(255,80,60,0.15);color:#ff503c;">射击</span>
        <span class="tag" style="background:rgba(241,196,15,0.15);color:#f1c40f;">FPS</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">v1.8</span>
        <span class="tag" style="background:rgba(255,255,255,0.06);color:rgba(255,255,255,0.35);">💻 桌面端</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#ff503c,#c0392b);color:#fff;">▶ 开始游戏 (v1.8)</span>
    </div>
  </a>

  <!-- ===== 3D 战术突击 ===== -->
  <a class="game-card" href="games/cs3d_v1.7.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #0a0e14, #142234);">
      <span class="card-cover-emoji">🎯</span>
    </div>
    <div class="card-body">
      <div class="card-title">3D 战术突击</div>
      <div class="card-desc">3D第一人称射击！迷彩风格开始界面、多武器系统、血量弹药HUD、开镜瞄准，沉浸式战术体验！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">射击</span>
        <span class="tag" style="background:rgba(0,100,255,0.15);color:#06f;">3D</span>
        <span class="tag" style="background:rgba(255,170,0,0.15);color:#fa0;">战术</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">v1.7</span>
        <span class="tag" style="background:rgba(255,255,255,0.06);color:rgba(255,255,255,0.35);">💻 桌面端</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#4ADE80,#22c55e);color:#0a0a1a;">▶ 开始游戏 (v1.7)</span>
    </div>
  </a>

  <!-- ===== 台球大师 ===== -->
  <a class="game-card" href="games/%E5%8F%B0%E7%90%83%E5%A4%A7%E5%B8%88%20v4.html">
    <div class="card-cover" style="background: linear-gradient(135deg, #0d1117, #1c2733);">
      <span class="card-cover-emoji">🎱</span>
    </div>
    <div class="card-body">
      <div class="card-title">台球大师</div>
      <div class="card-desc">双人对战台球模拟！击球力度控制、计分系统、犯规检测、回合日志，v4版精美物理引擎！</div>
      <div class="card-tags">
        <span class="tag" style="background:rgba(47,129,247,0.15);color:#2f81f7;">体育</span>
        <span class="tag" style="background:rgba(255,255,255,0.15);color:#fff;">双人对战</span>
        <span class="tag" style="background:rgba(74,222,128,0.15);color:#4ADE80;">v4</span>
        <span class="tag" style="background:rgba(255,255,255,0.06);color:rgba(255,255,255,0.35);">💻 桌面端</span>
      </div>
    </div>
    <div class="card-footer">
      <span class="play-btn" style="background:linear-gradient(135deg,#2f81f7,#1a5cb5);color:#fff;">▶ 开始游戏 (v4)</span>
    </div>
  </a>

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
  🛠️ 合作打造：余风清韵 · WorkBuddy · GitHub Pages<br>
  <small style="opacity:0.4;">访问 <a href="https://cdreply.github.io" style="color:rgba(125,249,255,0.6);text-decoration:none;">cdreply.github.io</a> 获取最新内容</small>
</footer>
