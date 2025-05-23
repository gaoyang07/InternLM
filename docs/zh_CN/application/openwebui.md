# 使用 Open WebUI 部署 InternLM

Open WebUI 是一个可扩展、功能丰富且用户友好的自托管 WebUI，专为离线运行而设计。

## 安装

```bash
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

## 配置 InternLM

在 Open WebUI 中配置 InternLM 模型，通过设置页面添加模型端点。
