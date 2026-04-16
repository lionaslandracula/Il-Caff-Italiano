# Il Mondo del Caffè · 咖啡世界 PWA

一个意大利语 + 中文的咖啡知识学习 App（渐进式 Web 应用）。

## 📁 文件结构

```
caffe-app/
├── index.html        ← 主 App（所有逻辑都在这里）
├── manifest.json     ← PWA 清单文件
├── sw.js             ← Service Worker（离线缓存）
├── icon.svg          ← App 图标
└── README.md         ← 本说明
```

## 🚀 部署到 GitHub Pages（最简单）

1. 在 GitHub 新建一个仓库，例如叫 `il-caffe` 或 `caffe-app`
2. 把 `caffe-app` 文件夹里**所有 4 个文件**（index.html, manifest.json, sw.js, icon.svg）直接上传到仓库根目录
3. 在仓库 Settings → Pages，选 `main` 分支 `/ (root)`，保存
4. 等几分钟，访问 `https://你的用户名.github.io/il-caffe/` 就能用了

**⚠️ 重要**：4 个文件必须在**同一目录**，并且 `sw.js`、`manifest.json`、`icon.svg` 必须放在 `index.html` **旁边**（不能嵌套子目录），否则 PWA 和离线功能会失效。

## 📱 在手机上"安装"成 App

部署后用手机浏览器打开链接：

- **iPhone (Safari)**：点分享按钮 → "添加到主屏幕"
- **Android (Chrome)**：会自动弹出"安装 App"提示，或点右上角菜单 → "安装应用"

安装后会变成一个独立的 App 图标，打开是全屏无浏览器栏的体验，也可以离线使用。

## ✨ 功能

- 📖 **浏览模式**：原有的 17 页幻灯片，可分类浏览（起源/转化/冲煮/饮品）
- 🎴 **闪卡模式**：意大利语→中文翻转记忆卡，打乱顺序
- 🔊 **意大利语发音**：用浏览器内置 TTS（无需 API key）
- ⭐ **收藏功能**：对重要词汇标星，单独查看
- ✓ **已学标记**：追踪学习进度
- 📊 **统计面板**：显示总课程 / 已学 / 收藏数量
- 💾 **本地存储**：进度永久保存在浏览器
- 📴 **离线可用**：装过一次后完全不需要网络

## 🔧 本地测试

如果想在本地测试 PWA 功能（Service Worker 需要 http 协议不能用 file://），可以在 caffe-app 文件夹里跑：

```bash
# 用 Python
python3 -m http.server 8000

# 或用 Node
npx http-server
```

然后浏览器访问 `http://localhost:8000`。

## 🎨 修改内容

所有课程数据都在 `index.html` 最下面的 `<script>` 里，一个 `LESSONS` 数组。要加新课就往数组里 push 新对象，格式：

```js
{
  id: 'unique-id',
  category: 'Bevande',  // 分类（四选一）
  category_zh: '饮品',
  it: "Caffè Corretto",       // 意大利语
  zh: "添酒咖啡",              // 中文
  foot_it: "Espresso con una goccia di grappa",  // 底部描述（意）
  foot_zh: "浓缩加一滴格拉帕酒",                  // 底部描述（中）
  tts: "Caffè corretto: espresso con grappa.",   // TTS 朗读文本
  body: `<svg>...</svg>`  // 中间展示的 SVG 内容
}
```

---

Buon studio! 学习愉快 ☕
