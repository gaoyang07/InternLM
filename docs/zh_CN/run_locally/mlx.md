# 使用 MLX 运行 InternLM

MLX 是苹果开发的机器学习框架，专为 Apple Silicon 优化。

## 安装 MLX

```bash
pip install mlx-lm
```

## 运行 InternLM

```bash
python -m mlx_lm.generate --model InternLM/internlm3-8b-instruct --prompt "你好，请介绍一下你自己"
```

## 性能优化

MLX 针对 Apple Silicon（M1、M2、M3 芯片）进行了优化，可以高效利用统一内存架构。

## 注意事项

- 仅适用于搭载 Apple Silicon 的 macOS 系统
- 需要 macOS 13.3 或更高版本
