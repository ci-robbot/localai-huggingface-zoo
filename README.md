# localai-huggingface-zoo

[LocalAI](https://github.com/go-skynet/LocalAI) model zoo

you can try this repository out by passing this environment variable (master builds only):
```
  GALLERIES=[{"url": "github:ci-robbot/localai-huggingface-zoo/index.yaml","name":"huggingface"}]
  # Preload models
  # PRELOAD_MODELS=[{"id":"huggingface@thebloke__open-llama-7b-open-instruct-ggml__open-llama-7b-open-instruct.ggmlv3.q4_0.bin"}]
```

you should be able to see then the huggingface models with:
```
  curl http://localhost:8080/models/available | jq
```

and install is something like:
```
  curl http://localhost:8080/models/apply -H "Content-Type: application/json" -d '{ "id": "hugghingface@thebloke__open-llama-7b-open-instruct-ggml__open-llama-7b-open-instruct.ggmlv3.q4_0.bin" }'
```

To search something, you can use `jq`:
```
  curl http://localhost:8080/models/list | jq '.[] | select(.name | contains("open-llama"))'
```

and try it out with:
```
  curl http://localhost:8080/v1/chat/completions -H "Content-Type: application/json" -d '{                                                                                                         
     "model": "thebloke__open-llama-7b-open-instruct-ggml__open-llama-7b-open-instruct.ggmlv3.q4_0.bin",
     "messages": [{"role": "user", "content": "How are you?"}],
     "temperature": 0.1
   }'
```
