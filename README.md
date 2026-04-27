# tsxvideosLibrary

> Centralized cloud storage and CDN for programmatically generated MP4 videos.

---

## Overview

**tsxvideosLibrary** is a dedicated GitHub repository that acts as a lightweight, free-tier cloud storage and content delivery layer for MP4 assets produced by the [Video Studio](https://github.com/ismailmuhammad15g-code) application — a Next.js + [Remotion](https://www.remotion.dev/) pipeline for generating videos programmatically.

Instead of relying on paid object-storage services, this repository leverages GitHub's raw file serving and CDN infrastructure to host rendered video files, making them publicly accessible via stable URLs at zero cost.

---

## Purpose

| Concern | Solution |
|---|---|
| **Storage** | MP4 files are committed directly to this repository, keeping them versioned and auditable. |
| **Delivery** | Files are served through GitHub's CDN via `raw.githubusercontent.com`, providing globally distributed access with no extra infrastructure. |
| **Cost** | Entirely free — no S3 buckets, no Cloudinary plans, no egress fees for typical developer workloads. |
| **Integration** | Video Studio writes the public raw URL back to the application after each successful render, so assets are immediately consumable by front-end clients. |

---

## How it Works

> ⚙️ *Detailed walkthrough coming soon.*

<!-- TODO: Add step-by-step explanation of the render → commit → serve pipeline -->

1. **Render** — Video Studio triggers a Remotion render job from a Next.js API route.
2. **Upload** — The rendered `.mp4` is pushed to this repository via the GitHub API (or a CI step).
3. **Resolve** — The raw CDN URL is returned to the caller and stored for playback or download.

---

## Repository Structure

```
tsxvideosLibrary/
└── <video-assets>/     # MP4 files organized by project or timestamp
```

---

## Usage

Reference any video asset using the following URL pattern:

```
https://raw.githubusercontent.com/ismailmuhammad15g-code/tsxvideosLibrary/main/<path-to-file>.mp4
```

---

## Related Projects

- **Video Studio** — Next.js application that renders videos using Remotion and uploads them here.

---

## License

Assets in this repository are intended for personal and developer use. See individual project licenses for details.
