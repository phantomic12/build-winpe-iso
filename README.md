# WinPE ISO Builder

This repository contains a GitHub Actions workflow that automatically builds a bootable Windows PE (WinPE) ISO image.

## How it Works

The workflow runs on a `windows-latest` runner and performs the following steps:

1.  **Installs Dependencies**: Uses Chocolatey to install the **Windows Assessment and Deployment Kit (ADK)** and the **WinPE Add-on**.
2.  **Prepares Environment**: Sets up the WinPE build environment using `copype`.
3.  **Builds ISO**: Generates a bootable `.iso` file using `MakeWinPEMedia`.
4.  **Uploads Artifact**: Uploads the resulting ISO to GitHub Actions artifacts for download.

## Usage

### Method 1: Automatic
The workflow will run automatically on any `push` to the `main` branch.

### Method 2: Manual Trigger
You can manually trigger a build without pushing code:
1.  Go to the **Actions** tab in this repository.
2.  Select **Build WinPE ISO** from the left sidebar.
3.  Click the **Run workflow** button.

## Downloading the ISO

Once the build is complete:
1.  Navigate to the **Actions** tab.
2.  Click on the completed workflow run.
3.  Scroll down to the **Artifacts** section.
4.  Click **WinPE-ISO** to download the zip file containing your ISO.

## Requirements

* No local software is required; everything runs in GitHub Actions.
* The resulting ISO is 64-bit (`amd64`).

## Customization

To modify the ISO (e.g., add drivers, scripts, or change the background), edit the `run` steps in `.github/workflows/winpe-build.yml` before the `MakeWinPEMedia` command is executed.
