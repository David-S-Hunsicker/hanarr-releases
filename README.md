# Hanarr

**A private, local-first career companion for your personal job search.** Hanarr helps you find relevant openings, keep your application pipeline organized, and prepare for interviews. You decide which opportunities to pursue and what to send; Hanarr keeps the research and bookkeeping in one place on your computer.

> This repository is the public download page. It contains Windows installers, checksums, release metadata, and release notes — **not the application source code**.

## Download Hanarr for Windows

Go to the [latest release](https://github.com/David-S-Hunsicker/hanarr-releases/releases/latest) and download both:

- `Hanarr-Setup-X.Y.Z.exe` — the Windows installer.
- `Hanarr-Setup-X.Y.Z.sha256` — its SHA-256 checksum.

Replace `X.Y.Z` below with the version you downloaded, then verify the installer in PowerShell before running it:

```powershell
$installer = ".\Hanarr-Setup-X.Y.Z.exe"
$checksumFile = ".\Hanarr-Setup-X.Y.Z.sha256"
$expected = (Get-Content $checksumFile -Raw).Trim().Split(' ')[0].ToLowerInvariant()
$actual = (Get-FileHash $installer -Algorithm SHA256).Hash.ToLowerInvariant()
if ($actual -ne $expected) { throw "Checksum mismatch — do not run this installer." }
"SHA-256 verified"
```

The installer is currently **unsigned**. Windows may show an unknown-publisher or SmartScreen warning. The checksum lets you check that the downloaded file matches the checksum published alongside it; it does not independently verify who published the file. Only download releases from this repository.

Run the installer and launch Hanarr from the Start Menu. The installer does not install Ollama or send your resume anywhere. On first launch, the setup checklist guides you through configuration. Hanarr runs its dashboard locally on your computer.

## What Hanarr does

- **Finds jobs:** searches public job APIs you choose, including Greenhouse, Lever, Ashby, Workday, RemoteOK, Arbeitnow, Recruitee, Workable, and USAJOBS. It does not scrape sites whose terms prohibit automated access.
- **Helps you assess fit:** compares job postings with your resume and preferences, applies explicit dealbreakers, and explains match scores. You review every result.
- **Tracks applications:** organize jobs through your pipeline and get follow-up reminders.
- **Supports your preparation:** manage resume versions and proposals, collect evidence for skills, work through coaching projects, and practice interview questions and STAR stories.
- **Keeps you in control:** searches can run on your schedule or on demand; Hanarr does not submit job applications for you.

The dashboard includes Jobs, Coaching, Resume, Skills, Applications, Prep, Coach, and Settings. Coach is grounded in your saved resume, jobs, and projects; proposed actions require your confirmation before they run.

## AI setup and updates

Hanarr can use **Ollama** for local resume parsing and job-fit analysis. You install Ollama and a model separately; Hanarr's installer does not install either. An optional Anthropic provider is available if you choose a hosted model and configure your own API key. With Anthropic selected, resume text and job descriptions used for analysis are sent to Anthropic. You can also disable LLM use and use rule-based scoring.

Update checks are enabled by default. Hanarr checks this public repository for the latest release and presents updates in the app; automatic installation follows a visible, cancellable prompt and waits for a running search to finish. You can change update behavior in Settings.

## Your data and privacy

Hanarr is designed to run as a local application, not a hosted account service. Your resume, preferences, job records, and applications are stored on your computer. The Windows installer keeps application data under `%LOCALAPPDATA%\Hanarr`, and uninstalling the app preserves that data.

Network requests go only to the job-source APIs you enable and, if you select Anthropic, to its API for analysis. Keep the dashboard on its default local-only address; exposing it to a network without an authentication boundary is not supported.

## Releases

Every release includes the installer, a SHA-256 sidecar, and `release-metadata.json`. Read the release notes for changes and any version-specific information.

- [Download the latest release](https://github.com/David-S-Hunsicker/hanarr-releases/releases/latest)
- [Browse all releases](https://github.com/David-S-Hunsicker/hanarr-releases/releases)

## License and permitted use

Hanarr is licensed for **unmodified use in your own personal job search** — for example, finding postings, tracking your own applications, and preparing your own application materials. Other uses, including organizational or commercial use, modification, and redistribution, require the copyright holder's express prior permission. This is a summary, not the complete license terms.