# v1m (`laya-markers-v1`)

**v1m** is an open-source, ultra-low latency System One calibrated decision engine developed by [M4tinBeigi](https://github.com/m4tinbeigi-official), trained specifically for Persian and multilingual intent classification, decision routing, and confidence scoring.

It uses an encoder-based architecture (mmBERT) with specialized sequence markers and an ONNX runtime decision head calibrated at temperature 1.0.

| | `v1m` |
|---|---|
| Upstream | [M4tinBeigi/v1m-persian-decision](https://huggingface.co/M4tinBeigi/v1m-persian-decision) @ `d3b2a3d7bb6df023993d6a4e9ada07cde36da3a6` |
| Source Code | [m4tinbeigi-official/v1m-persian-decision](https://github.com/m4tinbeigi-official/v1m-persian-decision) |
| Architecture | Encoder-based decision head (mmBERT-base, Laya family) |
| Parameters | 322M (fp32 / fp16) |
| Context length | 1024 tokens |
| Languages | Persian (`fa`), English (`en`), Multilingual |
| License | Apache-2.0 (M4tinBeigi) |
| Layout | `laya-markers-v1` |

## Model Files

| File | Source |
|---|---|
| `multilingual/model.safetensors` | Upstream PyTorch weights @ commit `d3b2a3d7` |
| `multilingual/encoder/config.json` | ModernBERT/mmBERT encoder config |
| `multilingual/tokenizer/tokenizer.json` | Upstream multilingual tokenizer |
| `multilingual/rl_agent_config.json` | Calibrated RL agent config with temperature vector |

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
