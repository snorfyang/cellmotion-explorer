# SciencePal · CellMotion Explorer

SciencePal turns cell-tracking evidence into an auditable research decision. The demo shows a complete **Audit → Forecast → Critic → Report** workflow, including a 16-frame trajectory-length gate that keeps short records out of the six-setting stability denominator.

## Demo

Open the public demo: <https://snorfyang.github.io/cellmotion-explorer/index.zh.html>

The English landing page is <https://snorfyang.github.io/cellmotion-explorer/index.html>.

If you deploy a fork, enable GitHub Pages from the `docs/` folder on the default branch.

Chinese landing page: `docs/index.zh.html`. The localized landing page translates the interface and evidence summary; linked SciencePal run transcripts remain in their original language for provenance.

The static demo runs without credentials and uses a local evidence preview. The optional live SciencePal proxy is deliberately kept out of this public repository.


## Submission links

- Public repository: https://github.com/snorfyang/cellmotion-explorer
- Public demo: https://snorfyang.github.io/cellmotion-explorer/index.zh.html

The repository is public so reviewers can inspect the implementation and the GitHub Pages demo. The static demo runs without credentials and includes a local evidence preview.

## Run locally

### Static demo

```bash
git clone https://github.com/snorfyang/cellmotion-explorer.git
cd cellmotion-explorer
python3 -m http.server 8000 --directory docs
```

Open <http://127.0.0.1:8000/index.html>. GitHub Pages uses the same `docs/` directory from the `main` branch, so no build step is required for the public demo.

### Live SciencePal connection

The optional live mode keeps the API key in a local proxy. It is never placed in the static page or committed to GitHub. From the project root:

```bash
python3 -m venv .venv-sciencepal
.venv-sciencepal/bin/pip install flask sciencepal
.venv-sciencepal/bin/python sciencepal_proxy.py
```

Create a local `.env` file with the following settings, replacing the API key with your own value:

```env
SCIENCEPAL_API_KEY=your_key_here
SCIENCEPAL_AGENT_ID=e08c07dc-9e14-4ab7-83cf-cb78fe99f8d5
SCIENCEPAL_MODEL=platform::deepseek-v4-flash
SCIENCEPAL_PROXY_PORT=8780
```

Then serve `docs/` as above and open the page through `http://127.0.0.1:8000`. The live proxy uploads the v4 `knowledge_base.json` snapshot and the supporting tracking evidence for each run.

## Recommended walkthrough

1. Start on the Chinese landing page and select **完整案例**.
2. Follow the four evidence stages: **Audit** checks input quality, **Forecast** compares geometry-only and history-aware features, **Critic** reviews failures and limits, and **Report** gives the next experiment.
3. Open **Knowledge base** to inspect the v4 rule and the v1–v4 snapshots. The public Pages version is read-only.
4. Use the English switch in the header when you want the English interface. Raw SciencePal transcripts stay in their original language so the provenance is preserved.

## What the demo shows

- 255 tracking records across MCF10A and MDA-MB-231.
- Composite `(cell_type, record)` identity and record-level evidence.
- v4 stability rule: at least 16 frames, then positive history-aware gain in at least 3 of 6 settings.
- 15 short MDA-MB-231 records labeled `insufficient_trajectory_length`.
- Gated result: 163/240 eligible records stable (MCF10A 63/73; MDA-MB-231 100/167).
- Knowledge-base snapshots v1–v4 and read-only provenance in the local project.

## Local live run (optional)

The live proxy and API key are intentionally excluded from this repository. To run the live connection, keep the private proxy and `.env` outside the public checkout, then start the proxy locally and open `cellmotion_demo/output/index.html`.

Never place API keys, private handoff text, run transcripts, or local credentials in GitHub.

## Attribution and resources

The workflow, scoring gate, knowledge-base versioning, evidence UI, and decision narrative are maintained in this repository. Model/API use, source datasets, external reference images, and open-source dependencies should be listed in the relevant attribution notes.
