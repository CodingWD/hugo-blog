# Netlify 部署指南

## 🚀 快速部署步骤

### 1. 推送代码到 GitHub
```powershell
# 添加所有文件
git add .

# 提交更改
git commit -m "配置Netlify部署设置"

# 推送到GitHub
git push origin main
```

### 2. 连接 Netlify 到 GitHub
1. 访问 [Netlify](https://netlify.com) 并登录
2. 点击 "New site from Git"
3. 选择 "GitHub" 并授权访问
4. 选择你的博客仓库
5. 配置构建设置：
   - **Branch to deploy**: `main`
   - **Build command**: `hugo --gc --minify`
   - **Publish directory**: `public`

### 3. 配置自定义域名
1. 在 Netlify 项目设置中，找到 "Domain settings"
2. 点击 "Add custom domain"
3. 输入: `blog.yxipc.com`
4. 按照提示配置 DNS 记录

### 4. 启用 Netlify Identity（用于 CMS 登录）
1. 在项目设置中找到 "Identity"
2. 点击 "Enable Identity"
3. 在 "Registration preferences" 中选择 "Invite only"
4. 在 "Git Gateway" 中点击 "Enable Git Gateway"

### 5. 创建 CMS 管理员账户
1. 在 Identity 设置中点击 "Invite users"
2. 输入你的邮箱地址
3. 检查邮件并设置密码
4. 访问 `https://blog.yxipc.com/admin/` 登录 CMS

## 🔧 DNS 配置

### 如果使用 Netlify DNS
1. 在域名注册商处，将 NS 记录指向 Netlify 的 DNS 服务器
2. Netlify 会自动配置所有必要的记录

### 如果使用自己的 DNS
添加以下记录到你的 DNS 提供商：
```
# A 记录
blog.yxipc.com  A  75.2.60.5

# 或者 CNAME 记录（推荐）
blog.yxipc.com  CNAME  your-site-name.netlify.app
```

## 📝 环境变量配置

在 Netlify 项目设置的 "Environment variables" 中添加：
```
HUGO_VERSION=0.121.0
HUGO_ENV=production
HUGO_ENABLEGITINFO=true
```

## 🔍 故障排除

### 构建失败
1. 检查 Hugo 版本是否正确
2. 确认 `netlify.toml` 文件存在
3. 查看构建日志中的具体错误信息

### CMS 无法登录
1. 确认 Netlify Identity 已启用
2. 检查 Git Gateway 是否已启用
3. 确认用户已被邀请并激活

### 域名无法访问
1. 检查 DNS 记录是否正确配置
2. 等待 DNS 传播（可能需要 24-48 小时）
3. 确认 SSL 证书已自动生成

## 🎯 部署后检查清单

- [ ] 网站可以正常访问
- [ ] HTTPS 证书已生成
- [ ] CMS 管理界面可以登录
- [ ] 可以通过 CMS 创建和编辑文章
- [ ] 图片上传功能正常
- [ ] 自动部署功能正常（推送代码后自动更新）

## 📚 有用链接

- [Netlify 文档](https://docs.netlify.com/)
- [Hugo 部署指南](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/)
- [Decap CMS 文档](https://decapcms.org/docs/)

---

**注意**: 完成这些步骤后，你的博客将完全托管在 Netlify 上，并具备现代化的内容管理系统。GitHub Pages 的部署可以停用。