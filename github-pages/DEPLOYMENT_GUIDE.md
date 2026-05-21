# 沉答Ai小游戏乐园 - 部署指南

## 🚀 快速部署步骤

### 步骤1：准备Git仓库
```bash
# 如果你的GitHub Pages仓库还没有准备好
git clone https://github.com/cdreply/cdreply.github.io
cd cdreply.github.io
```

### 步骤2：复制项目文件
将本目录（`github-pages/`）下的**所有文件和文件夹**复制到你的GitHub Pages仓库根目录。

### 步骤3：提交并推送
```bash
git add .
git commit -m "更新沉答Ai小游戏乐园：添加沉淀方块游戏和优化内容"
git push origin main
```

### 步骤4：启用GitHub Pages
1. 访问 https://github.com/cdreply/cdreply.github.io/settings/pages
2. 确保以下设置：
   - Source: `Deploy from a branch`
   - Branch: `main`  `/ (root)`
   - 主题：无需选择（使用自定义`_layouts/default.html`）
3. 保存设置

### 步骤5：等待部署完成
- 等待约1-2分钟，GitHub会自动构建并部署
- 访问 https://cdreply.github.io 查看效果

## 📁 项目文件说明

### 核心文件
```
├── _config.yml              # 站点配置（已配置为cdreply.github.io）
├── index.md                 # 首页游戏列表卡片
├── DEPLOYMENT_GUIDE.md      # 本部署指南
└── README.md                # 项目说明文档
```

### 布局文件
```
_layouts/
└── default.html             # 自定义Jekyll布局（深色主题）
```

### 游戏文件
```
games/
├── tetris.html              # 沉淀方块游戏（完整功能）
└── snake.html               # 贪吃蛇游戏（适配版）
```

## 🔧 本地测试方法

### 方法1：使用Python（推荐）
```bash
# 进入项目目录
cd github-pages

# 启动本地服务器
python -m http.server 5500

# 在浏览器中访问
# http://localhost:5500/index.html
# http://localhost:5500/games/tetris.html
```

### 方法2：直接打开文件
- 双击 `index.html` 或 `games/tetris.html`
- **注意**：某些功能（如音频）可能需要HTTP服务器环境

## 🎮 游戏功能验证清单

### 沉淀方块游戏（tetris.html）
- [ ] 游戏可以正常开始/暂停/重来
- [ ] 方块可以移动、旋转、加速下落
- [ ] 空格键快速下落功能正常
- [ ] 时间计时每秒自动更新
- [ ] 空格键计数实时更新
- [ ] 炸弹道具可以生成和使用（概率2%-40%）
- [ ] 音效系统工作正常
- [ ] 最高分本地保存功能正常
- [ ] PC端两栏布局显示正常
- [ ] 移动端响应式布局正常

### 贪吃蛇游戏（snake.html）
- [ ] 游戏可以正常开始/结束
- [ ] 道具系统工作正常
- [ ] 移动端手势操作正常
- [ ] 音效系统工作正常

### 网站首页（index.html）
- [ ] 游戏卡片显示正常
- [ ] 所有链接正常工作
- [ ] 响应式布局正常
- [ ] 合作信息显示正常

## 🐛 常见问题排查

### 问题1：GitHub Pages显示空白页面
**原因**：可能缺少`_config.yml`文件或配置错误
**解决**：
1. 确保`_config.yml`文件存在
2. 检查文件内容是否正确：
   ```yaml
   title: 沉答Ai小游戏乐园
   description: 余风清韵与WorkBuddy合作打造的趣味小游戏合集
   url: "https://cdreply.github.io"
   ```

### 问题2：游戏音效无法播放
**原因**：现代浏览器禁止自动播放音频
**解决**：
1. 确保游戏启动后用户有交互操作
2. 游戏第一次需要用户点击开始按钮
3. 音效按钮可以切换静音/取消静音

### 问题3：高分无法保存
**原因**：浏览器localStorage被禁用
**解决**：
1. 检查浏览器是否允许本地存储
2. 游戏会自动适应，无localStorage时仍可正常游戏

### 问题4：移动端布局异常
**原因**：缺少移动端适配
**解决**：
1. 所有游戏已内置响应式设计
2. 确保viewport设置正确：
   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```

## 🔄 更新和维护

### 添加新游戏
1. 在`games/`目录下创建新的HTML游戏文件
2. 在`index.md`中添加游戏卡片
3. 确保游戏遵循以下规范：
   - 单文件HTML（包含所有CSS和JS）
   - 中文界面
   - 响应式设计
   - 触摸和键盘支持
   - Web Audio API音效

### 更新现有游戏
1. 直接在对应的HTML文件中修改
2. 更新后重新测试所有功能
3. 更新`index.md`中的游戏描述和标签

### 部署更新
1. 将修改后的文件推送到GitHub
2. GitHub会自动重新部署
3. 通常1-2分钟内生效

## 📞 技术支持

### 技术问题
- **代码问题**：检查浏览器开发者工具控制台
- **部署问题**：查看GitHub Actions构建日志
- **功能问题**：参考各游戏的代码注释

### 联系方式
- **项目负责人**：余风清韵
- **技术支持**：WorkBuddy
- **项目地址**：https://github.com/cdreply/cdreply.github.io

## 📅 更新历史

| 日期 | 版本 | 更新内容 |
|------|------|----------|
| 2026-04-02 | v1.0 | 初始版本：沉淀方块游戏、贪吃蛇游戏、网站框架 |
| 2026-04-02 | v1.1 | 完善沉淀方块：实时计时器、空格计数器、炸弹系统 |

---

**提示**：首次部署后，建议清除浏览器缓存后访问，确保获取最新版本。