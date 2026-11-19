Measured baseline CPU, memory, load, disk, and architecture to ground sizing decisions in real numbers.
Translated the client's daily visitor count and software needs into the five tiers on the rent card sheet.
Looked up live On-Demand prices directly on the official AWS pricing pages for our sandbox region.
Converted all USD figures into Kenyan Shillings using today's exchange rate so the client sees real costs.
Cross-checked AI-generated instance recommendations and pricing math against AWS documentation before deciding.
Verified that Lightsail fits the client's monthly budget better than an unmanaged EC2 instance.
What I might be wrong about, and how I would find out: I might be underestimating peak memory consumption during sudden traffic bursts; I would find out by running an HTTP load test while monitoring RAM with free -m.
