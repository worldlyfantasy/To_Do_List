# Vue Todo App

一个使用Vue 3构建的待办事项应用，具有玻璃质感设计。

## 功能特性

- ✅ 添加待办事项
- ✅ 删除待办事项（带删除线效果）
- ✅ 玻璃质感UI设计
- ✅ 响应式数据绑定
- ✅ 现代化Vue 3 Composition API

## 技术栈

- Vue 3
- Vite
- CSS3 (Glassmorphism)

## 安装和运行

### 方式一：Vue开发服务器（推荐）
1. 安装依赖：
```bash
npm install
```

2. 启动开发服务器：
```bash
npm run dev
```

3. 构建生产版本：
```bash
npm run build
```

### 方式二：Live Server预览
直接用Live Server打开 `simple-version.html` 文件即可预览。

## 项目结构

```
frontendpractice/
├── index.html              # Vue应用入口
├── package.json            # 项目配置
├── vite.config.js          # Vite配置
├── src/
│   ├── main.js             # Vue应用入口
│   └── App.vue             # 主组件（包含所有样式和逻辑）
└── README.md               # 项目说明
```

## 使用说明

1. 在输入框中输入待办事项内容
2. 点击"Add Todo"按钮或按回车键添加
3. 点击"删除"按钮删除待办事项
4. 删除后会显示删除线效果，3秒后自动移除

## 文件说明

- `App.vue`: 包含所有Vue组件逻辑和样式
- `simple-version.html`: 纯HTML版本，可直接用Live Server预览
- `index.html`: Vue应用的入口文件
