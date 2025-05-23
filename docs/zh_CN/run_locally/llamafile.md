# 使用 llamafile 运行 InternLM

llamafile 是一个将大语言模型分发为单个可执行文件的解决方案。

## 下载 InternLM llamafile

您可以从发布页面下载预构建的 InternLM llamafile。

## 运行模型

下载完成后，直接运行可执行文件：

```bash
./internlm3-8b-instruct.llamafile
```

## 访问 Web 界面

模型启动后，在浏览器中访问 `http://localhost:8080` 来使用 Web 界面与模型交互。

## 命令行选项

```bash
# 指定端口
./internlm3-8b-instruct.llamafile --port 8081

# 指定主机
./internlm3-8b-instruct.llamafile --host 0.0.0.0

# 查看所有选项
./internlm3-8b-instruct.llamafile --help
```

## 优势

- 单文件分发，无需复杂的依赖管理
- 跨平台兼容性
- 内置 Web 界面
- 易于部署和分享
