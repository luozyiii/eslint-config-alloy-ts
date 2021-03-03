# eslint-config-alloy-ts

> node 版本需在 12.0.0 以上

### 安装 ESLint

```
yarn add eslint typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-config-alloy -D
```

### 安装 Prettier

```
yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
```

在你的项目的根目录下创建一个 .eslintrc.js 文件，并将以下内容复制进去：

```
// .eslintrc.js
// extends 这一句很关键 plugin:prettier/recommended
module.exports = {
  extends: ['alloy', 'alloy/typescript', 'plugin:prettier/recommended'],
  env: {
    // 你的环境变量（包含多个预定义的全局变量）
    //
    // browser: true,
    // node: true,
    // mocha: true,
    // jest: true,
    // jquery: true
  },
  globals: {
    // 你的全局变量（设置为 false 表示它不允许被重新赋值）
    //
    // myGlobal: false
  },
  rules: {
    // 自定义你的规则
  }
};

```

在你的项目的根目录下创建一个 .prettierrc.js 文件，并将以下内容复制进去：

```
// .prettierrc.js
module.exports = {
  // 一行最多 120 字符
  printWidth: 120,
  // 使用 2 个空格缩进
  tabWidth: 2,
  // 不使用缩进符，而使用空格
  useTabs: false,
  // 行尾需要有分号
  semi: true,
  // 使用单引号
  singleQuote: true,
  // 对象的 key 仅在必要时用引号
  quoteProps: 'as-needed',
  // jsx 不使用单引号，而使用双引号
  jsxSingleQuote: false,
  // 末尾不需要逗号
  trailingComma: 'none',
  // 大括号内的首尾需要空格
  bracketSpacing: true,
  // jsx 标签的反尖括号需要换行
  jsxBracketSameLine: false,
  // 箭头函数，只有一个参数的时候，也需要括号
  arrowParens: 'always',
  // 每个文件格式化的范围是文件的全部内容
  rangeStart: 0,
  rangeEnd: Infinity,
  // 不需要写文件开头的 @prettier
  requirePragma: false,
  // 不需要自动在文件开头插入 @prettier
  insertPragma: false,
  // 使用默认的折行标准
  proseWrap: 'preserve',
  // 根据显示样式决定 html 要不要折行
  htmlWhitespaceSensitivity: 'css',
  // 换行符使用 lf
  endOfLine: 'lf'
};
```

### vscode setting 配置

```
{
  "files.eol": "\n",
  "editor.tabSize": 2,
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "eslint.validate": ["javascript", "javascriptreact", "vue", "typescript", "typescriptreact"],
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}

```

### 坑点

1.在 create-react-app v2 搭建的项目里，一旦你用了 eslint(.eslintrc.js 配置) + prettier(.prettierrc.js 配置)，加在项目中的 .prettierrc 配置文件就是无效的，不起作用。

解决方案

```
// .eslintrc.js
// extends 这一句很关键 plugin:prettier/recommended

{ extends: ["react-app", "plugin:prettier/recommended"] }


```
并且 vscode 设置 "editor.formatOnSave": false,
