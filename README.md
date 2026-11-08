# PROBES RSS feed (unofficial)

This project builds an RSS 2.0 podcast feed from Ràdio Web MACBA's public PROBES archive. It is intended to include the historical archive (the archive page currently reports 104 podcasts) and refresh weekly for new entries.

## Setup

1. Create a **public** GitHub repository named `probes-rss`. Leave “Add a README” unchecked.
2. Unzip this project on your computer.
3. In the new repository, choose **Add file → Upload files**.
4. Upload the *contents* of the unzipped folder, including the hidden `.github` directory. The workflow must be at `.github/workflows/update-feed.yml`. If your browser hides `.github`, use GitHub Desktop or Git's web editor.
5. Commit to the `main` branch.
6. Open **Settings → Pages**. Set **Build and deployment → Source** to **GitHub Actions**.
7. Open **Actions**, choose **Build PROBES RSS**, and click **Run workflow**.
8. After the run succeeds, the feed URL is:

   `https://YOUR-GITHUB-USERNAME.github.io/probes-rss/feed.xml`

   Replace `YOUR-GITHUB-USERNAME` with your GitHub username. Add that URL to your podcast app using “Add by URL” / “Add RSS feed”.

## What it does

The Python script follows pagination on MACBA's PROBES archive, visits episode pages, extracts direct audio URLs and metadata, and writes `docs/feed.xml`. GitHub Actions publishes it with GitHub Pages and rebuilds it every Monday.

## Notes

- This is an unofficial feed. It does not copy or host audio; enclosure URLs point to MACBA's own audio files.
- MACBA may change its page markup. If the scraper breaks, the workflow log will show the error.
- `docs/build-report.txt` records how many archive pages and episode links were found, how many feed items were written, and any pages where audio URLs could not be detected. Compare the feed count with MACBA's stated 104; the count can be lower if some entries lack a discoverable direct audio URL.
- GitHub Pages on a free account generally requires a public repository.
