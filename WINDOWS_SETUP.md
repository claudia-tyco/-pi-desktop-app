# Windows 快速启动指南

## 前置要求

在您的 Windows 电脑上安装以下软件：

1. **Node.js** (推荐 v18+)
   - 下载地址: https://nodejs.org/
   - 安装时选择 "Add to PATH"
   - 验证安装: 打开命令提示符，输入 `node -v` 和 `npm -v`

## 快速启动步骤

### 1. 解压项目文件

将项目文件夹解压到任意位置，例如 `C:\PI-Management-System\`

### 2. 打开命令提示符

- 按 `Win + R`
- 输入 `cmd` 并按 Enter
- 或在项目文件夹中，按 Shift + 右键，选择 "在此处打开 PowerShell 窗口"

### 3. 安装依赖

```bash
cd C:\PI-Management-System
npm install
```

等待安装完成（首次安装可能需要 5-10 分钟）

### 4. 生成 Windows 安装包

```bash
npm run dist:win
```

安装包会生成在 `dist\` 文件夹中：
- `PI-Management-System-1.0.0.exe` - 安装程序
- `PI-Management-System-1.0.0.exe` (便携版) - 无需安装的版本

### 5. 安装应用

双击 `PI-Management-System-1.0.0.exe` 进行安装

## 开发模式（可选）

如果您想在开发模式下运行应用（用于测试或修改）：

```bash
npm run dev
```

这会启动开发服务器，您可以在浏览器中查看应用。

## 常见问题

### Q: npm 命令找不到？
A: 
1. 检查 Node.js 是否正确安装
2. 重启命令提示符
3. 确保 Node.js 已添加到系统 PATH

### Q: 安装依赖时出错？
A:
1. 删除 `node_modules` 文件夹和 `package-lock.json` 文件
2. 运行 `npm cache clean --force`
3. 重新运行 `npm install`

### Q: 生成安装包时出错？
A:
1. 确保已安装所有依赖：`npm install`
2. 检查是否有足够的磁盘空间
3. 尝试以管理员身份运行命令提示符

### Q: 如何卸载应用？
A: 在 Windows 设置中的"应用和功能"中找到 "PI Management System" 并卸载

## 项目结构

```
pi-desktop-app/
├── src/
│   ├── main/           # Electron 主进程（后端）
│   ├── db/             # SQLite 数据库
│   └── renderer/       # React 前端
├── public/             # 静态资源
├── dist/               # 构建输出
├── package.json        # 项目配置
└── README.md           # 项目说明
```

## 技术栈

- **框架**: Electron 41
- **前端**: React 19 + TypeScript
- **数据库**: SQLite3
- **构建工具**: Vite + electron-builder

## 默认登录账户

| 角色 | 用户名 | 密码 |
|------|--------|------|
| 管理员 | admin | Admin@123 |
| 销售员工 | sales01 | Sales@123 |
| 销售员工 | sales02 | Sales@123 |
| ... | sales03-sales10 | Sales@123 |

## 数据存储位置

所有数据保存在：
```
C:\Users\[您的用户名]\AppData\Local\PI Management System\pi_management.db
```

## 获取帮助

如遇到问题，请检查：
1. Node.js 版本是否为 v16 或更高
2. 磁盘空间是否充足
3. 防火墙是否阻止了应用
4. 查看项目中的 README.md 文件

## 下一步

1. 生成安装包后，您可以将 `.exe` 文件分发给其他用户
2. 其他用户可以直接运行 `.exe` 文件，无需 Node.js
3. 所有数据都保存在本地，无需云服务

祝您使用愉快！🎉
