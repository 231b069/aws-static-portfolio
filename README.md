# aws-static-portfolio

# AWS Cloud & DevOps Task: Secure Static Website Hosting

## 📌 Project Overview
This repository contains a responsive, single-page professional portfolio website deployed on AWS infrastructure. The project demonstrates core cloud engineering concepts including object storage, secure content delivery (CDN), SSL/TLS termination, and infrastructure access management (IAM).

## 🚀 Live Demo & Repository
- **CloudFront Live URL:** [INSERT_YOUR_CLOUDFRONT_URL_HERE] (e.g., https://d12345.cloudfront.net)
- **GitHub Repository:** [INSERT_YOUR_GITHUB_REPO_URL_HERE]

---

## 🛠️ Architecture & Tech Stack

### Frontend Components
- **HTML5 & CSS3:** Structured with semantic elements, styled using modern layout paradigms (CSS Grid/Flexbox), and managed via CSS custom variables (`:root`).
- **Typography & Icons:** Integrated via Google Fonts ('Inter') and structured into responsive layouts with clean Call-to-Action (CTA) elements.
- **Multi-Page/Component Setup:** Includes `index.html` (Main Portfolio landing page) along with secondary project showcases (`project2.html`) and their respective stylesheets.

### AWS Infrastructure
- **Amazon S3:** Configured as the origin source utilizing the Static Website Hosting feature.
- **Amazon CloudFront:** Implemented as a globally distributed Content Delivery Network (CDN) acting as the secure proxy layer for edge caching.
- **Security Protocols:** Enforced HTTPS redirection (SSL/TLS) via CloudFront Viewer Protocol Policies and custom IAM Bucket Policies.

---

## 🔧 Step-by-Step Implementation Details

### Step 1: Directory Setup & Version Control
1. Organized code assets cleanly within a local workspace root.
2. Initialized version tracking with Git and mapped to the remote GitHub repository: `aws-static-portfolio`.
3. Standardized the core landing page asset to `index.html` to align with web server standards.

### Step 2: Object Storage Configuration (Amazon S3)
1. Provisioned a unique, globally isolated S3 bucket configured for the closest geographic latency.
2. Disabled the default *Block Public Access* wrapper to accommodate public read-access requirements for static asset streaming.
3. Enabled **Static Website Hosting** under the Bucket Properties, setting the index mapping to point directly to `index.html`.
4. Applied a JSON **Bucket Policy** to allow granular public read access to explicit objects within the resource scope.

### Step 3: Global Edge Routing Setup (Amazon CloudFront)
1. Provisioned a global CloudFront distribution mapping its primary origin to the AWS S3 website endpoint.
2. Modified the default caching headers and protocol parameters, setting the policy behavior to **"Redirect HTTP to HTTPS"**.
3. Deployed the distribution across global edge locations, fetching a unique subdomain hash (`*.cloudfront.net`) bound to a managed SSL certificate.

---

## 📄 S3 Public Read Bucket Policy Applied

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR-S3-BUCKET-NAME/*"
        }
    ]
}
