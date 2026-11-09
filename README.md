# conceptmod-converters

Independent CPU tools for converting ordinary PEFT and LoRANetwork adapters
into ComfyUI layouts. This package owns model-specific key mappings, QKV
fusion and conversion sidecars. It does not depend on conceptmod core or any
model-provider product, and it does not load base models or generate samples.

```bash
python -m pip install -e .
conceptmod-convert /path/to/adapter_model.safetensors
conceptmod-convert /path/to/adapters/
```

Original adapter files are preserved. Converted safetensors and a sidecar JSON
are written beside the source. Inspect `conceptmod-convert --help` for model
selection, verification and overwrite options. Nonlinear particle branches
cannot be converted by dropping tensors; those checkpoints are rejected.
Some target mappings are explicitly unverified or unsupported. The converter
retains those distinctions; tensor/key tests do not prove matching generation
behavior. YuE2 details are in [docs/yue2-lora-conversion.md](docs/yue2-lora-conversion.md).

## Validation

```bash
python -m pip install -e '.[dev]'
CUDA_VISIBLE_DEVICES='' python -m pytest -q
python -m build --wheel --no-isolation
```

Unit tests use synthetic adapters and committed key/schema fixtures. Optional
ComfyUI tests require an existing checkout and its dependencies:

```bash
COMFYUI_ROOT=/path/to/ComfyUI python -m pytest -m integration -rs
```

They skip with a concrete dependency reason when ComfyUI is unavailable. Tests
never clone ComfyUI. Hub slider checks additionally require
`CONCEPTMOD_RUN_HUB_TESTS=1`; ordinary unit tests make no network requests.

## Origin

Extracted from [HyperGAN/conceptmod](https://github.com/HyperGAN/conceptmod),
commit `9a8a0c7f85c767a9222114d5d73706d85a2910f5`. Tensor mappings and
conversion computations were retained. The original MIT attribution is in
[LICENSE](LICENSE); transferred sources and fixtures are listed in
[docs/origin.md](docs/origin.md).
