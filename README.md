# SyncRig-weights

Public mirror of model weights for [SyncRig](https://github.com/ryoyaks/SyncRig).

Weights are distributed as GitHub Release assets so users can install
SyncRig providers without HuggingFace accounts, tokens, or gated-repo
acceptance flows. Each release tag corresponds to one provider's weight
set; the SyncRig engine resolves the right release at install / first-run.

## Releases

| Tag | Provider | Upstream | License |
|---|---|---|---|
| `sam3d-v1.0` | `sam3d` (SyncRig in-tree) | [facebook/sam-3d-body-dinov3](https://huggingface.co/facebook/sam-3d-body-dinov3) + [-vith](https://huggingface.co/facebook/sam-3d-body-vith) | Meta SAM License (redistribution permitted with attribution + LICENSE pass-through) |

## How weights are fetched

`syncrig_engine.providers.sam3d_provider._download_gh_release()` streams
each asset to the local cache at `<SyncRig>/models/sam3d/<variant>/`,
matching the on-disk layout the upstream loader expects.

If the GH mirror is unreachable, the engine falls back to HuggingFace
(legacy path; requires user to have accepted the gated-repo terms and
configured an HF token).

## License pass-through

Each weight release ships the upstream model license alongside the
weights themselves (e.g. `LICENSE-SAM3D.txt` for SAM 3D Body). Re-use of
the weights is governed by the upstream license.

This mirror repo itself contains only metadata and is published under
Apache 2.0; the licenses of the mirrored weights are unchanged.
