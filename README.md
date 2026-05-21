# One Node · Flux-2 Klein

A ComfyUI custom node that wraps the full Flux 2 Klein workflow into a single self-contained UI widget. No graph to build, no spaghetti wires to connect, just one powerful node with everything inside.

> *One Node to rule them all, One Node to find them,*
> *One Node to bring them all, and in ComfyUI bind them.*
>
> *— J.R.R. Tolkien, probably, if he used ComfyUI*

---

## What it does

The node has 5 modes, switchable with a single click:

**T2I** - standard text to image generation.

**I2I** - good for creating variations or gently nudging an image in a different direction.

**EDIT** - load one or two reference images and describe the change.

**PAINT** - three tools in one:
- Sketch: a full canvas with layers, brushes, shapes and more. Draw something and generate from it.
- Inpaint: paint a mask over the area you want to change, write what should be there instead.
- Outpaint: expand the image in any direction by dragging the edges.

**FACESWAP** - swap a face from a source image onto a target. Requires a Faceswap LoRA.

---

## Installation

Clone this repo into your ComfyUI `custom_nodes` folder:

```
cd ComfyUI/custom_nodes
git clone https://github.com/yanokusnir-ai/one-node-flux-2-klein.git
```

You need one additional custom node for inpaint and outpaint modes:
[ComfyUI-Inpaint-CropAndStitch](https://github.com/lquesada/ComfyUI-Inpaint-CropAndStitch) by lquesada. Just clone it into the same folder:

```
git clone https://github.com/lquesada/ComfyUI-Inpaint-CropAndStitch.git
```

Restart ComfyUI. The node appears as **One Node · Flux-2 Klein**.

---

## Models

This node works with any Flux 2 Klein model officially released by Black Forest Labs. GGUF versions are not currently supported.

You will need a diffusion model, a text encoder, and the VAE. Download links below.

**Diffusion models** (place in `models/diffusion_models/`)
- [flux-2 klein 9b distilled](https://huggingface.co/black-forest-labs/FLUX.2-klein-9B/resolve/main/flux-2-klein-9b.safetensors) - requires access request on HuggingFace
- [flux-2 klein 9b fp8](https://huggingface.co/black-forest-labs/FLUX.2-klein-9b-fp8/resolve/main/flux-2-klein-9b-fp8.safetensors) - requires access request on HuggingFace
- [flux-2 klein 9b kv](https://huggingface.co/black-forest-labs/FLUX.2-klein-9b-kv/resolve/main/flux-2-klein-9b-kv.safetensors) - requires access request on HuggingFace
- [flux-2 klein 9b kv fp8](https://huggingface.co/black-forest-labs/FLUX.2-klein-9b-kv-fp8/resolve/main/flux-2-klein-9b-kv-fp8.safetensors) - requires access request on HuggingFace
- [flux-2 klein 4b distilled](https://huggingface.co/black-forest-labs/FLUX.2-klein-4B/resolve/main/flux-2-klein-4b.safetensors)
- [flux-2 klein 4b fp8](https://huggingface.co/black-forest-labs/FLUX.2-klein-4b-fp8/resolve/main/flux-2-klein-4b-fp8.safetensors)

**Text encoder for 9b models** (place in `models/text_encoders/`)
- [qwen_3_8b_fp8mixed](https://huggingface.co/Comfy-Org/vae-text-encorder-for-flux-klein-9b/resolve/main/split_files/text_encoders/qwen_3_8b_fp8mixed.safetensors)
- [qwen_3_8b_fp4mixed](https://huggingface.co/Comfy-Org/vae-text-encorder-for-flux-klein-9b/resolve/main/split_files/text_encoders/qwen_3_8b_fp4mixed.safetensors)

**Text encoder for 4b model** (place in `models/text_encoders/`)
- [qwen_3_4b](https://huggingface.co/Comfy-Org/vae-text-encorder-for-flux-klein-4b/resolve/main/split_files/text_encoders/qwen_3_4b.safetensors)
- [qwen_3_4b_fp4](https://huggingface.co/Comfy-Org/vae-text-encorder-for-flux-klein-4b/resolve/main/split_files/text_encoders/qwen_3_4b_fp4_flux2.safetensors)

**VAE** (place in `models/vae/`)
- [flux2-vae](https://huggingface.co/Comfy-Org/vae-text-encorder-for-flux-klein-9b/resolve/main/split_files/vae/flux2-vae.safetensors)

**Faceswap LoRA** (place in `models/loras/`)
- [bfs head swap v1 (9b)](https://huggingface.co/Alissonerdx/BFS-Best-Face-Swap/resolve/main/bfs_head_v1_flux-klein_9b_step3500_rank128.safetensors)
- [bfs head swap v1 (4b)](https://huggingface.co/Alissonerdx/BFS-Best-Face-Swap/resolve/main/bfs_head_v1_flux-klein_4b.safetensors)

**Remove Background** (place in `models/background_removal/`)

The node includes a built-in Remove Background tool powered by BiRefNet. To use it, download:
- [birefnet](https://huggingface.co/Comfy-Org/BiRefNet/resolve/main/background_removal/birefnet.safetensors)

---

## License note on Flux 2 Klein 9B

This node works with both the 4B and 9B variants of Flux 2 Klein. The 4B model is released under Apache 2.0 and can be used freely including commercially.

The 9B model is released under the **FLUX Non-Commercial License** by Black Forest Labs. This means you can use it for personal and research purposes, but commercial use is not permitted. If you use the 9B model, you are responsible for complying with that license. You can review it at https://huggingface.co/black-forest-labs/FLUX.2-klein-9B.

This node itself is fully open source with no restrictions.

---

## Support

If you find this useful and want to support further development:

[buymeacoffee.com/yanokusnir](https://buymeacoffee.com/yanokusnir)

Thanks. Now go make something cool. :)
