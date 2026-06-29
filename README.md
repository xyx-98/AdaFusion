# AdaFusion NC

This workspace contains the AdaFusion / PathoOracle Nature Communications manuscript materials.

## Synchronization Strategy

Use two layers:

- Baidu Sync Disk: large files, PDFs, raw data, generated figures, and temporary outputs.
- Git: lightweight manuscript state, analysis scripts, figure plans, handoff notes, and project documentation.

## Recommended Git-Tracked Files

- `README.md`
- `CODEx_HANDOFF.md`
- `.gitignore`
- `writing/`
- `analysis/`
- `scripts/`
- small result summary tables, if needed

## Files Usually Excluded From Git

- PDFs
- `.xmind` files
- raw data
- model outputs
- temporary folders
- large images and slide files

## Cross-Device Routine

Before switching devices:

```powershell
git status
git add .gitignore README.md CODEx_HANDOFF.md writing analysis scripts
git commit -m "Update project handoff"
git push
```

On the next device:

```powershell
git pull
```

Then ask Codex to read `CODEx_HANDOFF.md` and continue the current task.
