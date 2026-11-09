# Source attribution and extraction

Source: https://github.com/HyperGAN/conceptmod

Commit: `9a8a0c7f85c767a9222114d5d73706d85a2910f5`

Original MIT copyright is preserved in `LICENSE`.

Transferred source files:

- `conceptmod/convert.py`
- `conceptmod/convert_klein.py`
- `conceptmod/convert_yue2.py`
- `tests/test_convert_klein.py`
- `tests/test_convert_yue2.py`
- `tests/test_convert_lora_comfyui.py`
- `tests/test_comfyui_lora_apply.py`
- `tests/fixtures/krea2_turbo_lora_rank_64_bf16.keys.json`
- `scripts/convert_lora_comfyui.py` (replaced by the `conceptmod-convert` entry point)
- `docs/yue2-lora-conversion.md`

`tests/fixtures/krea_loader_suffixes.json` is the `_BLOCK_SUFFIX` mapping
from the source commit's `conceptmod/backends/krea_weights.py`. It keeps
the converter independent from the Krea 2 model provider.
