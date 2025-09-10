# CMS身份验证设置指南

您的Decap CMS已经配置完成，但需要设置身份验证才能正常使用。以下是两种推荐的身份验证方式：

## 方式一：Netlify Identity（推荐）

### 1. 部署到Netlify
1. 将您的博客推送到GitHub仓库
2. 在Netlify上连接您的GitHub仓库
3. 部署网站

### 2. 启用Netlify Identity
1. 在Netlify控制台中，进入您的网站设置
2. 点击 "Identity" 选项卡
3. 点击 "Enable Identity"
4. 在 "Registration preferences" 中选择 "Invite only" 或 "Open"
5. 在 "Git Gateway" 中点击 "Enable Git Gateway"

### 3. 创建用户账户
1. 在Identity选项卡中点击 "Invite users"
2. 输入您的邮箱地址
3. 检查邮箱并完成注册

## 方式二：GitHub OAuth（适合开发者）

### 1. 创建GitHub OAuth应用
1. 访问 GitHub Settings > Developer settings > OAuth Apps
2. 点击 "New OAuth App"
3. 填写应用信息：
   - Application name: 您的博客名称
   - Homepage URL: 您的网站URL
   - Authorization callback URL: `https://api.netlify.com/auth/done`
4. 记录 Client ID 和 Client Secret

### 2. 修改CMS配置
编辑 `static/admin/config.yml`，将backend部分改为：
```yaml
backend:
  name: github
  repo: 您的用户名/仓库名
  branch: main
```

## 本地测试

对于本地开发，您可以使用代理模式：

1. 安装netlify-cms-proxy-server：
```bash
npm install -g netlify-cms-proxy-server
```

2. 在项目根目录运行：
```bash
npx netlify-cms-proxy-server
```

3. 修改 `static/admin/config.yml` 添加：
```yaml
local_backend: true
```

## 访问CMS管理界面

设置完成后，访问 `http://localhost:1313/admin/` 即可进入CMS管理界面。

## 注意事项

- 确保您的网站已部署到可访问的URL
- Netlify Identity需要HTTPS环境
- 本地开发时建议使用proxy-server模式
- 首次使用需要邀请用户或开放注册