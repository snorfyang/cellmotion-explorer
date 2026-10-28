# SciencePal · CellMotion Explorer

SciencePal turns cell-tracking evidence into an auditable research decision. The demo shows a complete **Audit → Forecast → Critic → Report** workflow, including a 16-frame trajectory-length gate that keeps short records out of the six-setting stability denominator.

## Demo

Enable GitHub Pages from the `docs/` folder on the default branch.

Chinese landing page: `docs/index.zh.html`. The localized landing page translates the interface and evidence summary; linked SciencePal run transcripts remain in their original language for provenance.

The static demo runs without credentials and uses a local evidence preview. The optional live SciencePal proxy is deliberately kept out of this public repository.

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

## Originality and resources

The project-specific workflow, scoring gate, knowledge-base versioning, evidence UI, and decision narrative were built for this submission. Model/API use, source datasets, external reference images, and open-source dependencies should be listed in the hackathon declaration and attribution notes.
