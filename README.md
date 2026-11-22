> **Deployment status (November 21, 2026):** GitHub Pages-ready website. A private S3 bucket was created and the HTML file uploaded in `us-east-2`. CloudFront deployment is currently **blocked by AWS account verification**; an AWS-hosted website has NOT yet been deployed or tested. GitHub Pages is a temporary publishing route.

# Secure Cloud Portfolio Website — AWS Project 01

**Owner:** Devonna Williams  
**Focus:** AWS S3 · CloudFront · HTTPS · Origin Access Control (OAC) · Static website hosting

## What does this project solve?

A simple, accessible professional portfolio that can be delivered securely through Amazon CloudFront while the HTML file remains in a **private S3 bucket**. The page presents real technical support and QA experience without claiming unearned AWS employment or certification.

![Architecture diagram](assets/architecture.svg)

## What is ready now?

- `index.html` — complete, responsive, standalone webpage (no paid fonts, image files, frameworks, or JavaScript dependencies).
- `assets/architecture.svg` — editable cloud architecture diagram.
- `DEPLOY.md` — console-driven AWS deployment steps and cleanup.
- `assets/local-preview.png` and `assets/mobile-preview.png` — screenshots of the **local preview**, not proof of an AWS deployment.

## How to see it on your computer (no AWS account needed)

Double-click `index.html` to open it in your browser. On Windows, choose Open With > Chrome/Edge if necessary.

## Architecture

Visitor → HTTPS → CloudFront distribution with OAC → private Amazon S3 bucket → `index.html`

## What to test after deploying

| Test | Expected result | Record your evidence |
|---|---|---|
| Open CloudFront distribution URL | Page loads over HTTPS | Screenshot of address bar + site |
| Open GitHub link | Correct GitHub profile opens | Confirmed link |
| Open LinkedIn link | Correct LinkedIn profile opens | Confirmed link |
| Test narrow/mobile browser window | Content resizes without horizontal overflow | Mobile screenshot |
| Inspect S3 block-public-access | All public-access block settings remain ON | S3 settings screenshot |
| Inspect CloudFront OAC | CloudFront uses an OAC for S3 origin | CloudFront origin screenshot |

**Do not claim these tests passed until you actually run them in your AWS account.**

## Recruiter explanation

**Before AWS deployment:**

> I built a responsive portfolio website, prepared an AWS architecture using private S3 storage and CloudFront Origin Access Control, and documented the steps and security decisions for deployment.

**Only after successful AWS deployment and tests:**

> I deployed a responsive portfolio to a private Amazon S3 bucket and delivered it through CloudFront over HTTPS with Origin Access Control. I tested the live site, links, and public-access settings and documented the results.

## Privacy and costs

No contact form, user data collection, credentials, or third-party tracking. Do not upload AWS access keys to this repository. AWS usage can cost money; see `DEPLOY.md` and review your Billing dashboard before provisioning resources. A budget email alert is **not** a spending cap.

## Publish the temporary GitHub Pages version

1. Create a public GitHub repository named `devonna-cloud-portfolio`.
2. Upload the **contents** of this extracted folder, with `index.html` in the repository root.
3. Open repository **Settings → Pages**. Under **Build and deployment**, set **Deploy from a branch**, branch **main**, folder **/(root)**, then save.
4. Wait until GitHub Pages indicates deployment complete; visit `https://Devonnajw-ai.github.io/devonna-cloud-portfolio/`.
5. When AWS verifies CloudFront, finish the AWS deployment and update the README with verified screenshots.

GitHub Pages is public web hosting. Do not upload private records, API credentials, or personal contact information you don't want public.
