**Current blocker:** This AWS account currently receives a verification restriction when creating CloudFront distributions. Do not disable S3 public access to work around it.

# Deploy Project 01 through the AWS Console

**Before you start:** You need your own AWS account, access to the S3 and CloudFront consoles, and billing notifications. This repository is source code only; it does not deploy itself.

## Safety first

1. In the AWS Console, open **Billing & Cost Management → Budgets**. Create a small monthly cost budget alert (or zero-spend template where available). Monitor billing yourself: budget alerts are **not hard spending limits**.
2. Check Free Tier credits and pricing for **S3** and **CloudFront**. Don't assume everything is free on your account.
3. Use MFA on your AWS account. Never publish credentials or customer data.

## Step A — Store the site privately in Amazon S3

1. Open **S3 → General purpose buckets → Create bucket**.
2. Choose a globally unique bucket name such as `devonna-cloud-portfolio-<random-suffix>` and your preferred region.
3. **Keep all Block Public Access settings enabled** (the default). Keep ACLs disabled and bucket-owner-enforced ownership.
4. Create bucket and upload **`site/index.html`** to the **bucket root**. (Don't upload the whole `site` folder as a folder.)
5. **Do not enable S3 static website hosting.** CloudFront will use the S3 REST origin and Origin Access Control.

## Step B — Deliver the site through CloudFront

1. Open **CloudFront → Distributions → Create distribution** (the console labels may evolve).
2. For **Origin**, select your S3 bucket from the S3 origin list — **not** an `s3-website` URL.
3. Select **Origin Access Control (OAC)**, creating a new OAC if needed. Choose signed requests as recommended.
4. Configure **Viewer protocol policy: Redirect HTTP to HTTPS**.
5. Set **Default root object: `index.html`**.
6. Skip optional paid add-ons for this small demonstration; check any automatically selected WAF/security options and their prices.
7. Create distribution. The console may prompt you to **copy a suggested S3 bucket policy**. Apply it to the S3 bucket under **Permissions → Bucket policy**. It should grant `cloudfront.amazonaws.com` only `s3:GetObject` for your bucket's objects and restrict `AWS:SourceArn` to your distribution. **Do not disable S3 Block Public Access.**
8. Open the CloudFront `*.cloudfront.net` domain (it must be HTTPS). Confirm the homepage loads.

If it shows **AccessDenied**, revisit OAC/bucket policy, S3 root upload location, and default root object. AWS documentation: https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html

## Step C — Capture evidence

- Screenshot your live HTTPS site (include URL).
- Screenshot CloudFront distribution and OAC configuration.
- Screenshot S3 public access settings (private), without showing private account identifiers.
- Test mobile layout and external profile links.
- Add real screenshots under `assets/` and note the date and result in README.

## Cleanup

CloudFront deployments and S3 usage may incur charges. When you're finished demonstrating:

1. Disable the CloudFront distribution; after the console allows it, delete the distribution.
2. Empty the S3 bucket, then delete the bucket.
3. Review Billing and Cost Explorer for usage. Budget alerts do not automatically cancel charges.

**Official docs:**
- Secure S3 origins with OAC: https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html
- CloudFront getting started: https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html
