# [llamafile](https://github.com/Mozilla-Ocho/llamafile)

llamafile lets you turn large language model (LLM) weights into executables. It combines [llama.cpp](https://github.com/ggerganov/llama.cpp) with [Cosmopolitan Libc](https://github.com/jart/cosmopolitan).

The best practice of deploying InternLM2, InternLM2.5 or InternLM3 using llamafile is shown as below:

- Convert the model into GGUF model by `llama.cpp`. Suppose we get `internlm3-8b-instruct.gguf` in this step
- Create the llamafile

```shell
wget https://github.com/Mozilla-Ocho/llamafile/releases/download/0.8.6/llamafile-0.8.6.zip
unzip llamafile-0.8.6.zip

cp llamafile-0.8.6/bin/llamafile internlm3.llamafile

echo "-m
internlm3-8b-instruct.gguf
--host
0.0.0.0
-ngl
999
..." > .args

llamafile-0.8.6/bin/zipalign -j0 \
  internlm3.llamafile \
  internlm3-8b-instruct.gguf \
  .args

rm -rf .args
```

- Run the llamafile

```shell
./internlm3.llamafile
```

Your browser should open automatically and display a chat interface. (If it doesn't, just open your browser and point it at http://localhost:8080)
