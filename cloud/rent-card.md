# Rent Card

## The need
* **Site:** A local retail shop website with a product catalog and contact form (FC1 client, not named)
* **Visitors:** 150 visitors/day (source: FC1 client interview)
* **Budget:** 1,500 KES/month

## Measured
Time: 2026-11-19T22:36:10+03:00
nproc: 8
free -m: 1413 MB used out of 7833 MB
uptime: load average 0.14
df -h: 2.7G used on /
uname -m: x86_64

## What to rent for what
* **No-server (static):** Amazon S3 — $0.023/GB/month (aws.amazon.com/s3/pricing, read 2026-11-19)
* **Lightsail:** Amazon Lightsail 1 GB plan — $5.00/month (aws.amazon.com/lightsail/pricing, read 2026-11-19)
* **t-micro:** Amazon EC2 t3.micro — $0.0104/hr (aws.amazon.com/ec2/pricing/on-demand, read 2026-11-19)
* **Staging:** Amazon EC2 t3.small — $0.0208/hr (aws.amazon.com/ec2/pricing/on-demand, read 2026-11-19)
* **Never:** Amazon EC2 m5.large — $0.096/hr, ~12,384 KES/month which is 9.2x the cost of a t3.micro (aws.amazon.com/ec2/pricing/on-demand, read 2026-11-19)

Rate: 1 USD = 129.00 KES, from Central Bank of Kenya, read 2026-11-19

## My choice
This client should rent an **Amazon Lightsail 1 GB plan** (645 KES/month).

## Why not bigger, why not smaller
* **Why not bigger:** During measurement, `free -m` showed only 1413 MB used and `uptime` load average stayed at 0.14, so a larger instance wastes budget on idle capacity.
* **Why not smaller:** A smaller tier like a 512 MB t3.nano or static S3 bucket could not run Nginx, PHP-FPM, and a dynamic database concurrently without running out of memory.

## Lightsail or EC2 for this client
Lightsail is better for this client because it bundles a static IP, SSD storage, and 2 TB of data transfer into one predictable monthly shilling bill without surprise bandwidth fees.
