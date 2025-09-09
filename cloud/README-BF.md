

# MentraOS Cloud本地开发环境配置

## 主要项目

- API：MentraOS/cloud/
- Developer-Portal: MentraOS/cloud/developer-portal/
- AppStore: MentraOS/cloud/store/web/

## 常见的问题

1. 创建一个.env文件给本地开发用的
#1.1 安装mongoDB community版
（mongod --version ，sc query MongoDB， net start MongoDB ）

```ini
SUPABASE_SERVICE_KEY
MONGO_URL (本地需要安装mongoDB)
AZURE_SPEECH_REGION
AZURE_SPEECH_KEY
SUPABASE_JWT_SECRET
AUGMENTOS_AUTH_JWT_SECRET

CLOUD_PUBLIC_HOST_NAME=47.115.138.199:8002
# CLOUD_PUBLIC_HOST_NAME=host.docker.internal:8002
CLOUD_LOCAL_HOST_NAME=localhost:10011
APP_AUTH_JWT_PRIVATE_KEY=Z4vN6rL2xW9bM8sQ1tJ5kC7yA0uE3hD5oR6pX3iT7gF1nV2qK8zW0lY9mB4cJ7dS
RESEND_API_KEY=Z4vN6rL2xW9bM8sQ1tJ5kC7yA0uE3hD5oR6pX3iT7gF1nV2qK8zW0lY9mB4cJ7dS
APP_STORE_URL=http://47.115.138.199:5175

# Alibaba Cloud Speech (NLS)
ALIBABA_NLS_URL=wss://nls-gateway.cn-shanghai.aliyuncs.com/ws/v1
ALIBABA_NLS_APPKEY=jJYGgIZ9OXLtsLDs
ALIYUN_AK_ID=LTAI5tGFrhYfA47W2AUvht8c
ALIYUN_AK_SECRET=***
```

2. 如果跑bun run dev出现docker镜像下载问题，可以尝试给docker for windows配置docker engine，增加国内镜像资源：

```json
{  
  "registry-mirrors": [
    "https://ccr.ccs.tencentyun.com",
    "https://docker.rainbond.cc",
    "https://elastic.m.daocloud.io",
    "https://elastic.m.daocloud.io",
    "https://docker.m.daocloud.io",
    "https://gcr.m.daocloud.io",
    "https://ghcr.m.daocloud.io",
    "https://k8s-gcr.m.daocloud.io",
    "https://k8s.m.daocloud.io",
    "https://mcr.m.daocloud.io",
    "https://nvcr.m.daocloud.io",
    "https://quay.m.daocloud.io"
  ]
}
```

3. 运行后报mongodb相关配置的错误
    - MONGO_URL=mongodb://host.docker.internal:27017
    - 修改mongod.cfg配置文件，bindIp: 0.0.0.0  # 原为127.0.0.1，修改后保存

4. 每个项目下都有对于的.env文件需要根据不同环境配置。

