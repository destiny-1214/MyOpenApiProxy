# MyOpenApiProxy

这是一个简单的 Cloudflare Worker 项目，用于代理 OpenAI API 请求，解决跨域问题和区域限制。

## 功能

- 将请求转发到 OpenAI API
- 自动处理跨域请求（CORS）
- 保留原始请求的所有头信息和请求体

## 部署方法

### 前提条件

- [Node.js](https://nodejs.org/) 安装
- [Wrangler CLI](https://developers.cloudflare.com/workers/wrangler/install-and-update/) 安装
- Cloudflare 账户

### 部署步骤

1. 克隆此仓库
   ```bash
   git clone <repository-url>
   cd buy-agent
   ```

2. 安装依赖
   ```bash
   npm install -g wrangler
   ```

3. 登录到 Cloudflare
   ```bash
   wrangler login
   ```

4. 创建 wrangler.toml 配置文件
   ```bash
   wrangler init
   ```

5. 部署 Worker
   ```bash
   wrangler publish
   ```

## 使用方法

部署完成后，您可以通过以下方式使用此代理：

```bash
curl -X POST "https://your-worker-domain.com/v1/chat/completions" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer your-api-key" \
  -d '{
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

将 `your-worker-domain.com` 替换为您的 Cloudflare Worker 域名，`your-api-key` 替换为您的 OpenAI API 密钥。
