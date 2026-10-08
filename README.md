# songsee

The [songsee](https://github.com/steipete/songsee) audio-spectrogram CLI for
OpenCharly images.

The `songsee` candy go-installs `github.com/steipete/songsee` into `~/go/bin` (the
GOPATH bin dir, appended to `PATH`). songsee is a kong-based Go binary that
renders an input audio file into a spectral image (spectrogram, mel, chroma).

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `songsee` |
| Binary | `~/go/bin/songsee` |
| Install | `go install github.com/steipete/songsee/cmd/songsee@latest` |
| Requires | [`layer-golang`](https://github.com/opencharly/layer-golang) |
| Env | `GOPATH=~/go`, PATH append `~/go/bin` |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list:

```yaml
my-audio-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-songsee:v2026.243.0410'
```

Then, inside the built image (or on a dev host):

```bash
songsee --help       # the kong CLI surface
songsee --version
```

The candy's `plan:` asserts the binary is installed at `~/go/bin/songsee` and
that `songsee --version` execs the kong CLI and exits 0 — verifiable without an
audio fixture.

## Layout

- `charly.yml` — the `songsee:` candy entity (the `require:`, the
  `env:`/`path_append:`, the `go install` step, and the `check:` probes) and the
  embedded `songsee-skill:` skill entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.
## Related

- Owning skill: `/charly-tools:songsee`
- Dependency: `/charly-coder:golang`
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
