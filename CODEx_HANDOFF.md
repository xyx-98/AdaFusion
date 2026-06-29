# Codex Handoff

Last updated: 2026-06-29

## Current Objective

Prepare and develop the AdaFusion / PathoOracle Nature Communications manuscript workflow across two devices.

## Project State

- Main project folder: `D:\BaiduSyncdisk\[paper-work]\AdaFusion NC`
- Project files are synchronized through Baidu Sync Disk.
- Git is intended to track lightweight project state: writing notes, analysis scripts, figure plans, README files, and this handoff file.
- Large source files, PDFs, raw data, temporary outputs, and heavy image/model files should stay on the sync disk and should not be committed to Git.

## Manuscript Direction

Working title:
PathoOracle: Interpretable Orchestration of Foundation Model Combinations in Computational Pathology

Core argument:
Pathology foundation models encode complementary and spatially structured tissue preferences. AdaFusion / PathoOracle uses compact adaptive gating to orchestrate multiple PFMs, improving downstream performance while exposing phenotype- and microenvironment-level model specialization that can guide efficient model routing.

## Key Files

- `writing/nc_figure_plan.md`: current main figure plan and manuscript logic.
- `writing/nc_story_brief.md`: earlier story brief; currently appears to have encoding issues on this device.
- `conf1.pdf` and `conf2.pdf`: conference-version AdaFusion material.
- `nc-framework.pdf` locally named in Chinese: NC manuscript framework.
- `experiment-settings.pdf` locally named in Chinese: experiment setting notes.
- `mccv_10folds_0.7train0.3val/`: MCCV results for 12 datasets.
- `PFM-statistics/` locally named in Chinese: PFM statistics PDFs.

## Current Figure Plan

- Fig. 1: Framework and motivation.
- Fig. 2: Performance, compactness, and representation granularity.
- Fig. 3: Spatial PFM contribution maps.
- Fig. 4: Quantified phenotype and clinical-label preference profiles.
- Fig. 5: Microenvironment graph and nuclear-feature association.
- Fig. 6: Similarity, complementarity, and efficient PFM routing.

## Next Recommended Tasks

1. Install Git for Windows on this device if it is not already available.
2. Initialize a Git repository in this project folder.
3. Commit lightweight files: `.gitignore`, `README.md`, `CODEx_HANDOFF.md`, and `writing/`.
4. Create a private remote repository on GitHub, Gitee, GitLab, or a lab server.
5. Push the initial commit.
6. On the second device, clone or connect to the same remote repository, then use the sync disk for large files.

## Suggested Device-Switch Routine

Before leaving a device:

```powershell
git status
git add .gitignore README.md CODEx_HANDOFF.md writing analysis scripts
git commit -m "Update handoff and manuscript notes"
git push
```

After moving to another device:

```powershell
git pull
```

Then ask Codex:

```text
Please read CODEx_HANDOFF.md and writing/nc_figure_plan.md, then continue from the previous task.
```

## Notes For Codex

- Do not overwrite user edits without checking the current file content first.
- Treat synchronized PDFs and large outputs as source material, not Git-tracked code.
- Keep this handoff file updated at the end of substantial work sessions.
