# ♟️ JavaScript 中国象棋程序

> 从零开始，用 JavaScript 编写一个完整的中国象棋 AI 程序。

[![Stars](https://img.shields.io/github/stars/Royhoo/write-a-chinesechess-program?style=flat-square)](https://github.com/Royhoo/write-a-chinesechess-program/stargazers)
[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](LICENSE)
![Language](https://img.shields.io/badge/language-JavaScript-yellow?style=flat-square)

🎮 **在线体验：** [点击这里试玩](https://royhoo.github.io/write-a-chinesechess-program/)

---

## 📖 项目简介

本项目是一套完整的**中国象棋 AI 程序**教程与实现，使用纯 JavaScript 编写，无任何外部依赖。从棋盘界面搭建，到实现具备置换表、开局库的完整博弈 AI，共分 9 章循序渐进。

适合以下人群阅读：
- 对**博弈树搜索算法**（Minimax、Alpha-Beta 剪枝）感兴趣的开发者
- 想学习**棋类游戏 AI**实现原理的同学
- 希望用 JavaScript 实现完整游戏项目的前端开发者

---

## 🗂️ 教程目录

每个章节对应一个独立分支，可单独查看该阶段的完整代码：

| 章节 | 分支 | 主题 | 核心技术 |
|------|------|------|----------|
| [第 0 章](http://www.cnblogs.com/royhoo/p/6426394.html) | — | 前言 | 项目介绍、整体架构规划 |
| [第 1 章](http://www.cnblogs.com/royhoo/p/6424395.html) | [step-1](../../tree/step-1) | 界面设计 | Canvas 渲染、FEN 串、虚拟棋盘坐标系 |
| [第 2 章](http://www.cnblogs.com/royhoo/p/6424840.html) | [step-2](../../tree/step-2) | 校验棋子走法 | 各棋子规则、走法生成、makeMove/undoMakeMove |
| [第 3 章](http://www.cnblogs.com/royhoo/p/6425387.html) | [step-3](../../tree/step-3) | 电脑自动走棋 | Search 框架、随机走棋、局面评估函数 |
| [第 4 章](http://www.cnblogs.com/royhoo/p/6425658.html) | [step-4](../../tree/step-4) | 极大极小搜索 | Minimax 算法、博弈树、位置价值表 |
| [第 5 章](http://www.cnblogs.com/royhoo/p/6425761.html) | [step-5](../../tree/step-5) | Alpha-Beta 搜索 | Alpha-Beta 剪枝、迭代加深、历史启发、走法排序 |
| [第 6 章](http://www.cnblogs.com/royhoo/p/6425817.html) | [step-6](../../tree/step-6) | 水平线效应与重复局面 | 静态搜索、重复局面检测、空步裁剪 |
| [第 7 章](http://www.cnblogs.com/royhoo/p/6425858.html) | [step-7](../../tree/step-7) | 置换表 | Zobrist 哈希、置换表、杀手走法启发 |
| [第 8 章](http://www.cnblogs.com/royhoo/p/6425912.html) | [step-8](../../tree/step-8) | 进一步优化（最终版） | 开局库、渴望搜索窗口 |

---

## 🧠 核心算法演进

```
随机走棋（step-3）
    ↓
Minimax 极大极小搜索（step-4）
    ↓
Alpha-Beta 剪枝 + 迭代加深 + 历史启发（step-5）
    ↓
静态搜索 + 重复局面检测 + 空步裁剪（step-6）
    ↓
Zobrist 哈希 + 置换表 + 杀手走法（step-7）
    ↓
开局库 + 渴望搜索窗口（step-8 · 最终版）
```

### Minimax 极大极小搜索
AI 扮演 MAX 方（最大化自身优势），对手扮演 MIN 方（最小化 AI 优势），通过递归遍历所有可能走法，选出最优一步。时间复杂度 O(b^d)，其中 b ≈ 40（平均分支数），d 为搜索深度。

### Alpha-Beta 剪枝
维护 α（最大下界）和 β（最小上界），当 α ≥ β 时剪掉无用分支。理论上将节点数从 O(b^d) 降至 O(b^(d/2))，**相同时间内搜索深度翻倍**。

### 静态搜索（Quiescence Search）
到达搜索"水平线"后，继续搜索所有吃子走法，直到局面稳定，消除**水平线效应**。

### 置换表（Transposition Table）
用 **Zobrist 哈希**为每个局面生成唯一 ID，将搜索结果缓存在哈希表中。不同路径到达相同局面时直接查表，避免重复计算，实际搜索速度提升 **2~4 倍**。

### 开局库（Opening Book）
收录数千个标准开局变化，AI 在开局阶段直接查表而非计算，覆盖顺炮、当头炮、飞相等主流开局。

---

## 🚀 快速开始

无需安装任何依赖，直接用浏览器打开即可：

```bash
git clone https://github.com/Royhoo/write-a-chinesechess-program.git
cd write-a-chinesechess-program

# 切换到最终版分支
git checkout step-8

# 用浏览器打开
open index.html         # macOS
start index.html        # Windows
xdg-open index.html     # Linux
```

或使用本地服务器（推荐，避免部分浏览器的跨域限制）：

```bash
python3 -m http.server 8080
# 访问 http://localhost:8080
```

---

## 🏗️ 最终版项目结构（step-8）

```
write-a-chinesechess-program/  (step-8 分支)
├── index.html      # 入口页面，棋盘界面 + 游戏控制
├── board.js        # Board 对象：棋盘渲染、交互逻辑
├── position.js     # Position 对象：棋局状态、走法校验、Zobrist 哈希
├── search.js       # Search 对象：Alpha-Beta、置换表、开局库接入
├── book.js         # 开局库数据（~300KB，来自 xqbase.com）
└── images/         # 棋盘 + 棋子图片资源
```

---

## 🎯 棋子走法速查

| 棋子 | 走法 | 限制 |
|------|------|------|
| 车（車） | 横竖任意格 | 不可越子 |
| 马（馬） | 走"日"字 | 蹩马腿限制 |
| 炮（砲） | 移动同车 | 吃子须隔一子（炮架） |
| 象（相/象） | 走"田"字 | 不可过河，塞象眼限制 |
| 士（仕/士） | 九宫内斜走一格 | 不可出九宫 |
| 将（将/帅） | 九宫内横竖一格 | 将帅不可照面 |
| 兵（兵/卒） | 前进一格 | 过河后可横走，不可后退 |

---

## 📚 相关资源

- [中国象棋编程（xqbase.com）](http://www.xqbase.com) — 本项目开局库来源，国内最权威的象棋编程资料
- [Wikipedia: Alpha-Beta Pruning](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning)
- [Wikipedia: Minimax](https://en.wikipedia.org/wiki/Minimax)
- [Wikipedia: Zobrist Hashing](https://en.wikipedia.org/wiki/Zobrist_hashing)
- [Quiescence Search](https://www.chessprogramming.org/Quiescence_Search)

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！详情请查看 [CONTRIBUTING.md](CONTRIBUTING.md)。

---

## 📄 License

[MIT](LICENSE) © Royhoo
