# [TGI](https://github.com/huggingface/text-generation-inference)

TGI is a toolkit for deploying and serving Large Language Models (LLMs). The easiest way of deploying a LLM is using the official Docker container:

```shell
model="internlm/internlm2_5-chat-7b"
volume=$PWD/data # share a volume with the Docker container to avoid downloading weights every run

docker run --gpus all --shm-size 1g -p 8080:80 -v $volume:/data ghcr.io/huggingface/text-generation-inference:2.0 --model-id $model
```

And then you can make requests like

```shell
curl 127.0.0.1:8080/generate_stream \
    -X POST \
    -d '{"inputs":"What is Deep Learning?","parameters":{"max_new_tokens":20}}' \
    -H 'Content-Type: application/json'
```
