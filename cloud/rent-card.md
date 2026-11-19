# Rent Card

## The need

- **Site type:** [e.g., A small retail shop website with a product catalog, contact form, and order inquiry page — describe your FC1 client without naming them]
- **Visitors a day:** [e.g., 150] visitors/day (source: [e.g., FC1 client interview and current WhatsApp/social inquiry volume])
- **Budget:** [e.g., 1,500] KES/month

## Measured

Time: 2026-11-19
nproc: 8
free -m: 1413 MB used
uptime: load average 0.14
df -h: 2.7G used on /
uname -m: x86_64

## My choice

## What to rent for what

- Static site: S3 — $0.023/GB/month (aws.amazon.com/s3/pricing, read 2026-11-19)
- Small dynamic app: Lightsail — $5.00/month (aws.amazon.com/lightsail/pricing, read 2026-11-19)
- Small dynamic app (raw VM): t-micro — $0.0104/hr (aws.amazon.com/ec2/pricing/on-demand, read 2026-11-19)
- Staging: t3.small — $0.0208/hr (aws.amazon.com/ec2/pricing/on-demand, read 2026-11-19)
- Never: m5.large — $0.096/hr (aws.amazon.com/ec2/pricing/on-demand, read 2026-11-19)

Rate: 1 USD = 129.00 KES, from Central Bank of Kenya, read 2026-11-19

## Why not bigger, why not smaller

- **Why not bigger:** During measurement, `free -m` showed only [e.g., 420] MB of RAM used and `uptime` load average stayed at [e.g., 0.12], proving a larger instance like a t3.small would sit mostly idle and double the client's bill unnecessarily.
- **Why not smaller:** A smaller tier like a t3.nano (512 MB RAM) or static S3 bucket could not run [e.g., Nginx, PHP-FPM, and a local SQLite/MySQL database] concurrently without running out of memory or failing to process dynamic form submissions.

## Lightsail or EC2 for this client

Lightsail is better for this client because it bundles a static IP, SSD storage, and 2 TB of data transfer into one predictable monthly shilling bill with no risk of surprise AWS bandwidth charges.
