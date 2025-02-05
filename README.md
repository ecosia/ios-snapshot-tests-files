# 📸 Snapshot Tests Files of the Ecosia Browser App 🌳

This repository serves as a Git submodule for storing snapshot test artifacts for the iOS project. It ensures that large snapshot files are managed efficiently using Git LFS while keeping the main repository clean and lightweight.

## Repository Structure

This repo contains only the `__Snapshots__` directories from the main iOS repository, maintaining their parent directory structure under `SnapshotArtifacts`.

```
SnapshotArtifacts/
  ├── [ComponentX]/
  │   ├── __Snapshots__/
  │   │   ├── snapshot1.png
  │   │   ├── snapshot2.png
  ├── [ComponentY]/
  │   ├── __Snapshots__/
  │   │   ├── snapshotA.png
  │   │   ├── snapshotB.png
```

## Setup & Usage

### Cloning the Repository with Submodules
If you are working in the main iOS repo and need to initialize this submodule, use:
```sh
git submodule update --init --recursive
```
If cloning the entire project, use:
```sh
git clone --recurse-submodules <main-repo-url>
```

### Pushing Updates to the Submodule
When updating snapshot files, commit and push them directly within this repository:
```sh
cd firefox-ios/EcosiaTests/SnapshotTests/SnapshotArtifacts
# Add and commit your changes
git add .
git commit -m "Update snapshot artifacts"
git push origin main
```
Then, in the main repo:
```sh
git add firefox-ios/EcosiaTests/SnapshotTests/SnapshotArtifacts
git commit -m "Update submodule reference"
git push origin main
```

## Git LFS Integration
Since this repository handles large snapshot files, Git LFS must be installed:
```sh
git lfs install
```
To ensure new files are tracked:
```sh
git lfs track "*.png"
git add .gitattributes
```

## Troubleshooting
If you encounter issues with missing submodules, ensure you have:
```sh
git submodule sync
```
If the submodule appears as an empty directory, run:
```sh
git submodule update --init --recursive
```
