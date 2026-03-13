# ♟️ JavaScript 中国象棋程序

> 从零开始，用 JavaScript 编写一个完整的中国象棋 AI 程序。

[![Stars](https://img.shields.io/github/stars/Royhoo/write-a-chinesechess-program?style=flat-square)](https://github.com/Royhoo/write-a-chinesechess-program/stargazers)
[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](LICENSE)
![Language](https://img.shields.io/badge/language-JavaScript-yellow?style=flat-square)

---

## 📖 项目简介

本项目是一套完整的**中国象棋 AI 程序**教程与实现，使用纯 JavaScript 编写，从界面设计到 AI 博弈算法，逐步实现一个可以与人对弈的象棋程序。

适合以下人群阅读：
- 对**博弈树搜索算法**（Minimax、Alpha-Beta 剪枝）感兴趣的开发者
- 想学习**棋类游戏 AI**实现原理的同学
- 希望用 JavaScript 实现完整游戏项目的前端开发者

🎮 **在线体验：** [点击这里试玩](https://write-a-chinesechess-program.royhooroyhoo.repl.co/)

---

## 🗂️ 教程目录

本系列共 **9 篇文章**，循序渐进地实现中国象棋程序：

| 章节 | 主题 | 核心内容 |
|------|------|----------|
| [第 0 章](http://www.cnblogs.com/royhoo/p/6426394.html) | 前言 | 项目介绍、整体架构规划 |
| [第 1 章](http://www.cnblogs.com/royhoo/p/6424395.html) | 界面设计 | 棋盘渲染、棋子绘制、Canvas 基础 |
| [第 2 章](http://www.cnblogs.com/royhoo/p/6424840.html) | 校验棋子走法 | 各棋子移动规则实现（车马炮象士卒） |
| [第 3 章](http://www.cnblogs.com/royhoo/p/6425387.html) | 电脑自动走棋 | 随机走棋、基础 AI 框架 |
| [第 4 章](http://www.cnblogs.com/royhoo/p/6425658.html) | 极大极小搜索算法 | Minimax 算法原理与实现 |
| [第 5 章](http://www.cnblogs.com/royhoo/p/6425761.html) | Alpha-Beta 搜索 | Alpha-Beta 剪枝优化，大幅提升搜索效率 |
| [第 6 章](http://www.cnblogs.com/royhoo/p/6425817.html) | 克服水平线效应、检查重复局面 | 静态搜索、重复局面检测 |
| [第 7 章](http://www.cnblogs.com/royhoo/p/6425858.html) | 置换表 | Zobrist 哈希、置换表缓存加速 |
| [第 8 章](http://www.cnblogs.com/royhoo/p/6425912.html) | 进一步优化 | 历史启发、杀手着法等高级优化 |

---

## 🧠 核心算法介绍

### Minimax 极大极小搜索
博弈树搜索的基础算法。AI 扮演 MAX 方（最大化自身优势），对手扮演 MIN 方（最小化 AI 优势），通过递归搜索所有可能的走法，选出最优一步。

```
MAX 层：AI 选择得分最高的走法
MIN 层：对手选择让 AI 得分最低的走法
```

### Alpha-Beta 剪枝
在 Minimax 基础上，通过维护 α（当前最大下界）和 β（当前最小上界）两个值，裁剪掉不可能影响最终结果的分支，大幅减少搜索节点数。

理论上可将搜索节点从 **O(b^d)** 降低到 **O(b^(d/2))**，即相同时间内搜索深度翻倍。

### 置换表（Transposition Table）
使用 **Zobrist 哈希**将已搜索过的局面缓存起来。当搜索树中出现相同局面时，直接读取缓存值，避免重复计算，是象棋 AI 的重要优化手段。

---

## 🚀 快速开始

### 直接运行（无需安装）

将仓库克隆到本地，直接用浏览器打开 `index.html` 即可：

```bash
git clone https://github.com/Royhoo/write-a-chinesechess-program.git
cd write-a-chinesechess-program
# 用浏览器打开 index.html
open index.html         # macOS
start index.html        # Windows
xdg-open index.html     # Linux
```

### 本地开发服务器（推荐）

```bash
# 使用 Python
python3 -m http.server 8080

# 或使用 Node.js
npx serve .

# 然后访问 http://localhost:8080
```

---

## 🏗️ 项目结构

```
write-a-chinesechess-program/
├── index.html          # 入口文件，棋盘界面
├── js/
│   ├── board.js        # 棋盘逻辑、棋子走法校验
│   ├── ai.js           # AI 核心：Minimax + Alpha-Beta
│   ├── search.js       # 搜索算法、置换表
│   └── evaluate.js     # 局面评估函数
├── css/
│   └── style.css       # 样式文件
└── assets/
    └── pieces/         # 棋子图片资源
```

---

## 🎯 棋子走法规则

| 棋子 | 走法说明 |
|------|----------|
| 车（車） | 横竖方向任意格，不可越子 |
| 马（馬） | 走"日"字，蹩马腿限制 |
| 炮（砲） | 移动同车，吃子需隔一子（炮架） |
| 象（相/象） | 走"田"字，不可过河，塞象眼限制 |
| 士（仕/士） | 在九宫内斜走一格 |
| 将（将/帅） | 在九宫内横竖走一格，将帅不可照面 |
| 兵（兵/卒） | 未过河只能前进，过河后可横走 |

---

## 📚 相关资源

- [中国象棋编程（CCCP）](https://www.xqbase.com/computer.htm) — 国内最权威的象棋编程资料
- [Wikipedia: Alpha-Beta Pruning](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning)
- [Wikipedia: Minimax](https://en.wikipedia.org/wiki/Minimax)
- [Zobrist Hashing](https://en.wikipedia.org/wiki/Zobrist_hashing)

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！详情请查看 [CONTRIBUTING.md](CONTRIBUTING.md)。

---

## 📄 License

[MIT](LICENSE) © Royhoo
