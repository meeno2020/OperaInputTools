# Opera Input Tools

<div align="center">

![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey.svg)

**一个功能强大的桌面自动化输入工具，基于 PyAutoGUI 开发**

[功能特性](#-功能特性) • [快速开始](#-快速开始) • [使用指南](#-使用指南) • [常见问题](#-常见问题)

</div>

---

## 📖 项目简介

**Opera Input Tools** 是一款专业的桌面自动化输入工具，专为需要批量处理数据输入任务的用户设计。通过图形化界面，您可以轻松配置自动化流程，实现一键批量输入，大幅提升工作效率。

### ✨ 核心优势

- 🎯 **零代码配置** - 图形化界面，无需编程知识
- 🔄 **批量处理** - 支持 CSV/Excel 数据文件批量输入
- 📍 **智能定位** - 可视化按钮定位，支持截图识别
- ⚙️ **灵活配置** - 拖拽式流程配置，支持保存和复用
- 📊 **实时监控** - 执行进度、日志记录，全程可控
- 🚀 **高效执行** - 支持暂停、继续、重启等操作

---

## 🎯 功能特性

### 1. 按钮定位功能
- ✅ 自定义按钮数量（1-20个）
- ✅ 快捷键 `Shift+W` 快速定位
- ✅ 自动截图保存按钮图像
- ✅ 智能坐标搜索（支持范围搜索）
- ✅ 按钮重命名和配置管理

### 2. 数据文件加载
- ✅ 支持 CSV 和 Excel (.xlsx, .xls) 格式
- ✅ 自动识别列名和数据类型
- ✅ 数据预览功能（前20行）
- ✅ 字段列表自动提取

### 3. 流程配置
- ✅ 图形化流程编辑器
- ✅ 支持多种操作类型：
  - 🔘 **按钮点击** - 从已定位按钮中选择
  - 📝 **字段输入** - 从数据文件列名中选择
  - ⌨️ **键盘操作** - TAB、ENTER、ESC、SPACE、BACKSPACE
  - ⏱️ **延迟控制** - 自定义延迟时间（秒）
- ✅ 拖拽调整步骤顺序
- ✅ 流程保存和加载（JSON 格式）

### 4. 执行控制
- ✅ 标准执行模式（Workflow Execution）
  - 自定义按钮搜索范围
  - 显示点击位置提示
  - 播放完成提示音
  - 指定起始行号
  - 暂停/继续/停止/重启功能
- ✅ V5 高级执行模式
  - 固定流程：字段输入 → 延迟 → Enter → 下箭头
  - 自定义字段间延迟
  - 行完成提示音

### 5. 执行监控
- ✅ 实时进度条显示
- ✅ 详细执行日志
- ✅ 当前状态提示
- ✅ 错误信息记录

---

## 🚀 快速开始

### 环境要求

- **操作系统**: Windows 10/11
- **Python**: 3.7 或更高版本
- **依赖库**: 见 `requirements.txt`

### 安装步骤

1. **克隆仓库**
```bash
git clone https://github.com/yourusername/opera-input-tools.git
cd opera-input-tools
```

2. **安装依赖**
```bash
pip install -r requirements.txt
```

3. **运行程序**
```bash
python main.py
```

---

## 📚 使用指南

### 第一步：按钮定位

1. 打开程序，切换到 **"Button Location"** 标签页
2. 设置需要定位的按钮数量（例如：3个）
3. 点击 **"Start Location"** 开始定位
4. 将鼠标移动到目标按钮位置
5. 按 `Shift+W` 确认当前位置
6. 重复步骤 4-5 直到所有按钮定位完成
7. 点击 **"Stop Location"** 保存坐标

**提示**：
- 定位时会自动截图保存按钮图像
- 可以随时重命名按钮
- 配置会自动保存到 `buttons.json`

### 第二步：加载数据文件

1. 切换到 **"Data File Loading"** 标签页
2. 点击 **"Select File"** 选择数据文件
3. 支持格式：
   - CSV 文件（逗号分隔）
   - Excel 文件（.xlsx, .xls）
4. 查看数据预览和字段列表

**数据文件要求**：
- 第一行必须是列名（字段名）
- CSV 文件使用逗号（`,`）分隔
- Excel 文件第一行为列名

**示例 CSV 文件**：
```csv
姓名,年龄,地址,电话
张三,25,北京市朝阳区,13800138000
李四,30,上海市浦东新区,13900139000
```

### 第三步：配置流程

1. 切换到 **"Workflow Configuration"** 标签页
2. 在左侧选择操作类型：
   - **Buttons**: 从已定位的按钮列表中选择
   - **Fields**: 从数据文件的列名中选择
   - **Keyboard Actions**: 选择键盘操作
   - **Delay**: 输入延迟秒数，点击 "Add Delay"
3. 点击 **"Add Selected"** 添加到流程
4. 在右侧流程列表中：
   - 拖拽调整步骤顺序
   - 使用 "Delete Selected" 删除步骤
   - 使用 "Move Up/Down" 调整顺序
   - 使用 "Clear" 清空所有步骤
5. 点击 **"Save Workflow"** 保存配置

**流程示例**：
```
点击 按钮1 → 输入字段 姓名 → TAB → 输入字段 年龄 → TAB → 延迟 1秒 → 点击 按钮2 → ENTER
```

### 第四步：执行流程

#### 标准执行模式

1. 切换到 **"Execution Control"** 标签页
2. 配置执行参数：
   - **Button Search Range**: 按钮搜索范围（推荐 200-300 像素）
   - **Show Mouse Click Position**: 显示点击位置提示
   - **Play Sound After Each Row**: 每行完成后播放提示音
   - **Start Row**: 起始行号（从第几行开始执行）
3. 点击 **"Start Execution"**
4. 等待 3 秒倒计时（用于定位鼠标）
5. 查看执行进度和日志
6. 可以随时暂停、继续或停止执行

#### V5 执行模式

1. 切换到 **"V5 Execution Control"** 标签页
2. 配置参数：
   - **Delay After Each Field**: 每个字段输入后的延迟（秒）
   - **Start Row**: 起始行号
   - **Play Sound After Each Row**: 每行完成后播放提示音
3. 点击 **"Start"** 开始执行
4. V5 模式固定流程：输入字段 → 延迟 → Enter → 下箭头

---

## 🏗️ 项目结构

```
opera-input-tools/
├── main.py                 # 主程序入口
├── button_locator.py       # 按钮定位模块
├── data_loader.py          # 数据加载模块
├── workflow_config.py      # 流程配置模块
├── workflow_executor.py    # 流程执行模块（标准模式）
├── v5_executor.py          # V5 执行模块（高级模式）
├── advanced_locator.py     # 高级按钮定位（图像识别）
├── resource_path.py        # 资源路径管理
├── requirements.txt        # 依赖包列表
├── buttons.json            # 按钮配置（自动生成）
├── workflow.json           # 流程配置（可选）
└── README.md              # 项目说明文档
```

---

## ⚙️ 配置说明

### 按钮配置文件 (`buttons.json`)

```json
{
  "按钮1": {
    "x": 100,
    "y": 200,
    "image_path": "button_screenshots/按钮1.png"
  },
  "按钮2": {
    "x": 300,
    "y": 200,
    "image_path": "button_screenshots/按钮2.png"
  }
}
```

### 流程配置文件 (`workflow.json`)

```json
{
  "workflow": [
    {"type": "button", "name": "按钮1"},
    {"type": "field", "name": "姓名"},
    {"type": "key", "name": "TAB"},
    {"type": "field", "name": "年龄"},
    {"type": "delay", "seconds": 1.0},
    {"type": "button", "name": "按钮2"},
    {"type": "key", "name": "ENTER"}
  ]
}
```

---

## 🔧 高级功能

### 图像识别定位

程序支持使用截图进行按钮定位，即使按钮位置发生微小变化，也能通过图像识别找到正确位置。

**工作原理**：
1. 定位时自动截图保存按钮图像
2. 执行时在坐标周围搜索范围内进行图像匹配
3. 找到最佳匹配位置后点击

**搜索范围设置**：
- 默认搜索范围：200-300 像素
- 顶部搜索范围自动扩展 2 倍
- 可根据实际情况调整

### 点击位置提示

启用 "Show Mouse Click Position" 后，每次点击按钮时会在屏幕上显示一个黄色提示框，显示：
- 按钮名称
- 点击坐标 (x, y)
- 0.8 秒后自动消失

---

## ❓ 常见问题

### Q1: 快捷键 `Shift+W` 不响应？

**A**: 请确保：
- 程序窗口处于活动状态
- 已点击 "Start Location" 开始定位
- 没有其他程序占用该快捷键

### Q2: 按钮坐标不准确？

**A**: 
- 定位时确保鼠标精确移动到按钮中心位置
- 如果按钮位置经常变化，建议使用图像识别功能（自动截图）
- 可以调整搜索范围以适应按钮位置变化

### Q3: 中文输入不显示？

**A**: 
- PyAutoGUI 对中文支持有限
- 建议使用英文数据或拼音
- 可以考虑使用剪贴板方式输入中文

### Q4: 执行速度太慢？

**A**: 
- 可以减少延迟时间
- 关闭 "Show Mouse Click Position" 选项
- 调整 pyautogui.PAUSE 设置（在代码中）

### Q5: 如何从中间某行开始执行？

**A**: 
- 在 "Start Row" 中输入起始行号（从 1 开始）
- 例如：输入 10 表示从第 10 行数据开始执行

### Q6: 如何暂停和继续执行？

**A**: 
- 点击 "Pause" 暂停执行
- 暂停后按钮变为 "Resume"，点击可继续
- 点击 "Stop" 停止执行
- 点击 "Restart" 重新开始

### Q7: 数据文件格式要求？

**A**: 
- CSV: 第一行为列名，使用逗号分隔
- Excel: 第一行为列名
- 确保字段名与流程配置中的字段名完全匹配

### Q8: 如何保存和加载配置？

**A**: 
- 按钮配置：点击 "Save Button Config" 保存，点击 "Load Button Config" 加载
- 流程配置：点击 "Save Workflow" 保存，点击 "Load Workflow" 加载
- 配置会自动保存为 JSON 格式

---

## 🛠️ 技术栈

- **GUI 框架**: Tkinter
- **自动化**: PyAutoGUI
- **数据处理**: Pandas
- **图像处理**: OpenCV, Pillow
- **键盘监听**: pynput, keyboard
- **Excel 支持**: openpyxl

---

## 📝 开发计划

- [ ] 支持更多键盘快捷键
- [ ] 添加条件判断功能
- [ ] 支持循环和分支流程
- [ ] 添加数据验证功能
- [ ] 支持多显示器环境
- [ ] 添加执行历史记录
- [ ] 支持定时执行
- [ ] 添加更多数据格式支持

---

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

---

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

---

## 👨‍💻 作者

**Opera Input Tools Team**

- 项目主页: [GitHub Repository](https://github.com/yourusername/opera-input-tools)
- 问题反馈: [Issues](https://github.com/yourusername/opera-input-tools/issues)

---

## ⭐ 致谢

感谢所有使用和贡献本项目的用户！

如果这个项目对您有帮助，请给个 ⭐ Star 支持一下！

---

<div align="center">

**Made with ❤️ by Opera Input Tools Team**

[⬆ 回到顶部](#opera-input-tools)

</div>
