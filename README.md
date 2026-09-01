# Transpoze-weights

Model weights for **Transpoze**, mirrored as GitHub Release assets.

This repo holds no code. It exists so that a first run of Transpoze can
fetch its weights with a plain HTTP GET — no Hugging Face account, no
token, and no gated-repo acceptance flow standing between someone and a
working install.

Transpoze itself is a private repo, so there is no link to follow here.
If you came looking for the product rather than its weights, this is the
wrong place.

## Releases

| Tag | Provider | Upstream | License |
|---|---|---|---|
| `sam3d-v1.0` | `sam3d` — the default provider | [facebook/sam-3d-body-dinov3](https://huggingface.co/facebook/sam-3d-body-dinov3) + [-vith](https://huggingface.co/facebook/sam-3d-body-vith) | Meta SAM License |

## How the engine fetches them

`transpoze_engine.providers.sam3d_provider._download_gh_release()` streams
each asset into `<Transpoze>/models/sam3d/<variant>/`, which is the layout
the upstream loader expects.

If this mirror is unreachable the engine falls back to Hugging Face —
the legacy path, which does require the user to have accepted the gated
terms and configured a token.

## License

The weights are Meta's and they stay under the Meta SAM License. That
license grants the right to redistribute them (§ 1a — "use, reproduce,
distribute, copy") on the condition that the agreement travels with
them, so every release ships the upstream license beside the weights it
covers: `LICENSE-SAM3D.txt` for SAM 3D Body.

Using the weights means accepting that license. Mirroring them here
changes nothing about it.
