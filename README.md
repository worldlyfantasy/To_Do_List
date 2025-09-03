# Vue Todo App (TypeScript)

一个使用Vue 3 + TypeScript构建的待办事项应用，具有玻璃质感设计。

## 功能特性

- ✅ 添加待办事项
- ✅ 删除待办事项（带删除线效果）
- ✅ 玻璃质感UI设计
- ✅ 响应式数据绑定
- ✅ 现代化Vue 3 Composition API
- ✅ 完整的TypeScript类型支持

## 技术栈

- Vue 3
- TypeScript
- Vite
- CSS3 (Glassmorphism)

## 安装和运行

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

4. 类型检查：
```bash
npm run type-check
```

## 项目结构

```
frontendpractice/
├── index.html              # Vue应用入口
├── package.json            # 项目配置
├── tsconfig.json           # TypeScript配置
├── vite.config.js          # Vite配置
├── env.d.ts                # 环境类型声明
├── src/
│   ├── main.ts             # Vue应用入口（TypeScript）
│   └── App.vue             # 主组件（TypeScript）
└── README.md               # 项目说明
```

## 使用说明

1. 在输入框中输入待办事项内容
2. 点击"Add Todo"按钮或按回车键添加
3. 点击"删除"按钮删除待办事项
4. 删除后会显示删除线效果，3秒后自动移除

## TypeScript特性

- 完整的类型定义
- 接口定义（Todo接口）
- 函数返回类型声明
- 严格的类型检查
- 更好的IDE支持和代码提示
