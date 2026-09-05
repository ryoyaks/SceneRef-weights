# SceneRef-weights

Model weights for **SceneRef**, mirrored as GitHub Release assets.

This repo holds no code. It exists so that a first run of SceneRef can
fetch its weights with a plain HTTP GET — no Hugging Face account, no
token, and no gated-repo acceptance flow standing between someone and a
working install.

SceneRef itself is a private repo, so there is no link to follow here.
If you came looking for the product rather than its weights, this is the
wrong place.

## Releases

| Tag | Provider | Upstream | License |
|---|---|---|---|
| `sam3d-v1.0` | `sam3d` — the default provider | [facebook/sam-3d-body-dinov3](https://huggingface.co/facebook/sam-3d-body-dinov3) + [-vith](https://huggingface.co/facebook/sam-3d-body-vith) | Meta SAM License |

The product ships and loads the **ViT-H** variant. The dinov3 assets stay
in the release for anyone who wants them, but SceneRef no longer offers
that checkpoint: its backbone is fetched separately at runtime under a
Meta licence distinct from the SAM one.

## How the engine fetches them

`sceneref_engine.providers.sam3d_provider._download_gh_release()` streams
each asset into `<SceneRef>/models/sam3d/<variant>/`, which is the layout
the upstream loader expects.

If this mirror is unreachable the engine falls back to Hugging Face —
the legacy path, which does require the user to have accepted the gated
terms and configured a token.

## License

The weights are Meta's and they stay under the Meta SAM License. That
license grants the right to redistribute them (§ 1.a — "use, reproduce,
distribute, copy") on the condition that the agreement travels with
them, so every release ships the upstream license beside the weights it
covers: `LICENSE-SAM3D.txt` for SAM 3D Body.

Using the weights means accepting that license. Mirroring them here
changes nothing about it. In particular, § 1.b.v forbids military or
warfare use, nuclear applications, espionage, and the development or use
of guns or illegal weapons; § 1.b.iii requires compliance with trade
controls; and § 1.b.iv forbids reverse engineering them. Read
`LICENSE-SAM3D.txt` in the release — the text governs, not this summary.

---

*Named Transpoze until 2026-09-03. The product is SceneRef; the old name
appears only in history.*
