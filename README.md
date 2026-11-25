# app-brain-extraction-v2

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Skull-strips a T1-weighted image with FSL BET and outputs the brain-extracted T1w volume.**

Wraps FSL's bet with a configurable fractional intensity threshold and optional robust centre estimation (-R) or bias field and neck cleanup (-B). Use it for quick brain extraction of a T1w image. Note that the generated wrapper passes the config values directly into a command template, so it may fail as committed (see problems).

| | |
|---|---|
| 📥 **Inputs** | `neuro/anat/t1w` |
| 📤 **Outputs** | `neuro/anat/t1w` |
| 🐳 **Container** | `brainlife/fsl:latest` |
| ⚙️ **Resources** | 4 GB memory · 1 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.986](https://doi.org/10.25663/brainlife.app.986) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `t1` | `neuro/anat/t1w` | yes | T1-weighted NIfTI image to skull-strip. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `brain` | `neuro/anat/t1w` | Brain-extracted T1w volume |

<details>
<summary><b>⚙️ Parameters</b> (3)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `frac` | number | `0.5` | BET fractional intensity threshold (0-1) |
| `robust` | boolean | `false` | Use BET's robust brain center estimation (-R) |
| `bias_neck_cleanup` | boolean | `false` | Bias field + neck cleanup (-B) |

</details>

<!-- brainlife-app:end -->

Skull-strip a T1w volume with FSL's bet.

## Inputs

- `t1` (neuro/t1)

## Outputs

- `brain` (neuro/t1) -- Brain-extracted T1w volume

## Usage

Brainlife.io: run via `braise-app-run`/`braise-app-pipeline` (once registered
with `braise-app-create`), or the web UI.

Locally (outside brainlife): copy `config.json.example` to `config.json`,
fill in real file paths, then run `./main` from this directory. `main` pulls
its own container (`singularity exec docker://...`) -- no local install of
the underlying tool needed, only Singularity itself.

Entrypoint: `brain_extract.py`

## Authors

- Gabriele Amorosino <g.amorosino@gmail.com>

## License

MIT, see `LICENSE`.
