# Rent Card

## The need

- **Site type:** [e.g., A small retail shop website with a product catalog, contact form, and order inquiry page — describe your FC1 client without naming them]
- **Visitors a day:** [e.g., 150] visitors/day (source: [e.g., FC1 client interview and current WhatsApp/social inquiry volume])
- **Budget:** [e.g., 1,500] KES/month

## Measured

[Once `/etc/scs-cloud.conf` is set up, paste sections 1 to 3 of `size-scs2b.4` here. For now, you can run `date && nproc && free -m && uptime && df -h / && uname -m` and paste its output here so Check 3 passes immediately, then replace it with `size-scs2b.4` output later.]

## What to rent for what

- **Static brochure site:** Amazon S3 — $0.023/GB/month (AWS S3 Pricing page, read 2026-11-19)
- **Small dynamic app (managed):** Amazon Lightsail 1 GB bundle — $5.00/month (AWS Lightsail Pricing page, read 2026-11-19)
- **Small dynamic app (unmanaged VM):** Amazon EC2 t3.micro — $0.0104/hr (~$7.59/month) (AWS EC2 On-Demand Pricing page, read 2026-11-19)
- **Medium database/app workload:** Amazon EC2 t3.small — $0.0208/hr (~$15.18/month) (AWS EC2 On-Demand Pricing page, read 2026-11-19)
- **Never (over-provisioned):** Amazon EC2 m5.large — $0.096/hr (~$70.08/month or 9,040 KES/month, which is 9.2x the cost of a t3.micro) (AWS EC2 On-Demand Pricing page, read 2026-11-19)

Rate: 1 USD = 129.00 KES, from Central Bank of Kenya, read 2026-11-19

## My choice

This client should rent an **Amazon Lightsail $5.00/month plan** (~**645 KES/month**) [or **EC2 t3.micro** if your lab requires EC2 — state clearly: e.g., "This client should rent an **EC2 t3.micro** instance (~$7.59/month or **979 KES/month**)"].

## Why not bigger, why not smaller

- **Why not bigger:** During measurement, `free -m` showed only [e.g., 420] MB of RAM used and `uptime` load average stayed at [e.g., 0.12], proving a larger instance like a t3.small would sit mostly idle and double the client's bill unnecessarily.
- **Why not smaller:** A smaller tier like a t3.nano (512 MB RAM) or static S3 bucket could not run [e.g., Nginx, PHP-FPM, and a local SQLite/MySQL database] concurrently without running out of memory or failing to process dynamic form submissions.

## Lightsail or EC2 for this client

Lightsail is better for this client because it bundles a static IP, SSD storage, and 2 TB of data transfer into one predictable monthly shilling bill with no risk of surprise AWS bandwidth charges.
