# v1m (`laya-markers-v1`)

**v1m** is an open-source, ultra-low latency System One calibrated decision engine developed by [M4tinBeigi](https://github.com/m4tinbeigi-official), trained specifically for Persian and multilingual intent classification, decision routing, and confidence scoring.

It uses an encoder-based architecture (mmBERT) with specialized sequence markers and an ONNX runtime decision head calibrated at temperature 1.0.

| | `v1m` |
|---|---|
| Upstream | [M4tinBeigi/v1m-persian-decision](https://huggingface.co/M4tinBeigi/v1m-persian-decision) @ `480c0cffba274b39c49a49d95c24d428a161bda2` |
| Source Code | [m4tinbeigi-official/v1m-persian-decision](https://github.com/m4tinbeigi-official/v1m-persian-decision) |
| Architecture | Encoder-based decision head (mmBERT-base, ONNX Runtime) |
| Parameters | 322M (fp32 / fp16) |
| Context length | 1024 tokens |
| Languages | Persian (`fa`), English (`en`), Multilingual |
| License | Apache-2.0 (M4tinBeigi) |
| Layout | `laya-markers-v1` |

## Model Files

| File | Source |
|---|---|
| `model.onnx` (325 MB) | [Hugging Face](https://huggingface.co/M4tinBeigi/v1m-persian-decision/resolve/main/model.onnx) / [v1m.ir](https://v1m.ir/static/models/v1m/model.onnx) |
| `tokenizer.json` (34 MB) | [Hugging Face](https://huggingface.co/M4tinBeigi/v1m-persian-decision/resolve/main/tokenizer.json) / [v1m.ir](https://v1m.ir/static/models/v1m/tokenizer.json) |
| `rl_agent_config.json` | [Hugging Face](https://huggingface.co/M4tinBeigi/v1m-persian-decision/resolve/main/rl_agent_config.json) / [v1m.ir](https://v1m.ir/static/models/v1m/rl_agent_config.json) |

## Usage with Ollaya

```bash
ollaya run v1m
```

Or via the System One decision endpoint:
```bash
curl http://localhost:11435/v1/systemone \
  -H "Content-Type: application/json" \
  -d '{
    "model": "v1m",
    "text": "میخواهم بسته اینترنت همراه بخرم",
    "choice": ["خرید بسته", "پشتیبانی", "پیگیری سفارش"]
  }'
```
