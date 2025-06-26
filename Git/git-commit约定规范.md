### Git Commit 约定规范

为提升代码提交的可读性、可维护性和自动化效率，制定以下约定。基于 [Conventional Commits](https://www.conventionalcommits.org/) 规范，结合常见实践优化。

------

### 一、Commit Message 格式

每一条提交信息必须包含 **Header**，可选包含 **Body** 和 **Footer**，格式如下：

```bash
<类型>(<作用域>): <主题>
<空行>
[正文]
<空行>
[脚注]
```

------

### 二、Header 规范

**1. 类型（Type）**

| 类型       | 说明                        | 示例                                  |
| :--------- | :-------------------------- | :------------------------------------ |
| `feat`     | 新增功能                    | `feat(user): 添加登录功能`            |
| `fix`      | 修复缺陷                    | `fix(api): 解决跨域问题`              |
| `docs`     | 文档更新                    | `docs(README): 更新安装步骤`          |
| `style`    | 代码格式调整（不改变逻辑）  | `style: 统一缩进为2空格`              |
| `refactor` | 代码重构（非功能/缺陷修改） | `refactor(auth): 提取验证逻辑`        |
| `perf`     | 性能优化                    | `perf: 减少数据库查询次数`            |
| `test`     | 测试相关                    | `test(service): 添加用户模块单元测试` |
| `chore`    | 构建/工具/配置变更          | `chore: 更新webpack配置`              |
| `revert`   | 回滚提交                    | `revert: 撤销某次错误提交`            |

**2. 作用域（Scope）**

- 描述影响范围（如模块、文件），**可选**
- 括号内使用名词（小写）
- 示例：`fix(login)`, `refactor(api-service)`

**3. 主题（Subject）**

- **简短描述**（50字内），使用**祈使语气**（如“添加”而非“添加了”）
- **首字母小写**，**结尾无标点**
- ❌ 错误示例：`Update the login page`
- ✅ 正确示例：`update login page validation`

------

### 三、Body（可选）

- **详细说明变更原因和方案**
- 每行不超过 72 字符
- 使用**祈使语气**

```bash
feat(payment): 接入支付宝支付

添加支付宝SDK依赖，实现支付回调处理。
移除旧的支付接口兼容代码，因安全策略变更。
```

------

### 四、Footer（可选）

**1. 关联 Issue**

- 关闭 Issue：`Closes #123`, `Fixes #45`
- 关联多个：`Related to #78, #79`

```bash
Closes #123  
Related to #456  
```

**2. 破坏性变更（BREAKING CHANGE）**

- 标明不兼容旧版本的修改，以 `BREAKING CHANGE:` 开头
- 必须提供**迁移说明**

```bash
refactor(config): 重命名环境变量  

BREAKING CHANGE:  
原环境变量 `DB_URL` 已弃用，请改用 `DATABASE_URL`。
```

------

### 五、示例

#### 简单提交

```bash
fix(auth): 处理空密码导致的崩溃  
```

#### 完整提交

```bash
feat(order): 支持优惠券系统  

添加优惠券校验接口，订单服务集成折扣计算逻辑  
更新数据库结构，新增coupons表  

Closes #112  
Related to #98  
```

#### 破坏性变更

```bash
chore(deps): 升级Vue至3.x  

BREAKING CHANGE:  
项目依赖的Vue版本升级到3.0，需重写所有使用`Vue.extend`的组件。
```

------

> **重要原则**
>
> - ✨ 每次提交聚焦**一个逻辑变更**
> - 🔍 主题清晰表达“做了什么”
> - 📖 复杂变更通过 Body/Footer 解释“为什么做”和“影响范围”

通过规范提交，可自动生成 [CHANGELOG](https://github.com/conventional-changelog/conventional-changelog)，提升协作效率！