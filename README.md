# 🧩 Match-3 Game (消消乐小游戏)

project内容为一个使用 Java 编写的 Swing 图形界面三消类游戏，支持多种玩法模式与关卡机制。

---

## 🎮 游戏玩法简介

这是一个经典三消游戏：  
玩家通过点击交换两个相邻的棋子，当三个或以上相同的图案横向或纵向连在一起时即可消除并得分。游戏包含多个关卡和挑战目标。

---

## 📁 项目结构
CS109-INTRODUCTION-TO-COMPUTER/
├── controller/
│ └── GameController.java # 控制器类
├── Core/
│ ├── Mode0.java / Mode1.java / Mode2.java # 三种游戏模式
│ ├── threeMatch.java # 核心逻辑
│ ├── circleTranslation.java, CounterApp.java 等实验类
│ └── MusicPlayertrial.java # 音乐播放类
├── Enters/
│ ├── Enterframe.java # 游戏入口和初始界面
│ ├── EnterBackground.png / Enterpicture.png # 启动背景图
├── Filepart/ # 文件读取/写入相关（如记录）
├── listener/
│ └── GameListener.java # 鼠标或按键监听器
├── model/
│ ├── Chessboard.java / Cell.java
│ ├── ChessPiece.java / ChessboardPoint.java
│ ├── Constant.java / Util.java # 工具类与常量
├── MusicController/ # 音效资源与控制
├── RecordingData/ # 存档数据
├── TestCase/ # 单元测试
├── view/
│ └── ChessGameFrame.java / 组件类 # Swing 界面
├── Main.java # 程序主入口（推荐设为此文件）
└── README.md

---

## 🧠 核心功能说明

### 🔁 模式支持

| 模式名 | 类名    | 描述 |
|--------|---------|------|
| Mode0  | `Mode0` | 最基础的三消模式，无特殊元素 |
| Mode1  | `Mode1` | 引入金币（💰）机制，金币掉落收集目标 |
| Mode2  | `Mode2` | 棋盘上添加障碍物（❌）和不可交换的元素 |

### 🎲 棋盘机制

- 棋盘大小固定为 `8x8`（由 `Constant.java` 定义）
- 每个格子用 `Cell` 表示，内含一个 `ChessPiece`
- 棋子字符说明：

| 字符 | 图案 | 含义         |
|------|------|--------------|
| 1    | 💎   | 普通棋子     |
| 2    | ⚪   | 普通棋子     |
| 3    | ▲   | 普通棋子     |
| 4    | 🔶   | 普通棋子     |
| +    | 💰   | 金币         |
| -    | ❌   | 障碍格       |
| a    | all  | 全消技能棋子 |
| k    | knock| 特殊棋子     |
| b    | bomb | 炸弹棋子     |

- 初始棋盘自动避免三连
- 有效交换会触发消除、得分、掉落、新棋子填充等

---

### 👆 操作控制

- 由 `GameController` 控制玩家的点击行为
- 玩家可以选中并交换相邻棋子
- 若交换无效（未消除），则撤销操作
- 若交换有效，则更新棋盘并重新绘制

---

### 🏁 胜利机制

- 每关设置目标分数与步数限制
- 达成目标后弹出对话框提示通关
- 支持进入下一关卡与继续游戏

---

## 🖼️ 图形与资源

- 棋子图案与颜色由 `Constant.java` 中的 `colorMap` 与 `imageMap` 管理
- 图标路径默认为本地路径，发布版本建议改为资源包加载

---

## 🚀 启动方式

### 前提条件

- JDK 8 或以上
- GUI 支持（建议使用 IntelliJ IDEA）

### 编译运行

```bash
javac -d out src/**/*.java
java -cp out MainClassName
