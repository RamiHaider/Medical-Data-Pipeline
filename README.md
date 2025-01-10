# Medical-Data-Pipeline

This repo was created in order to develop a pipeline for medical data.

The scenario is that: You are a data engineer at a hospital that aims to understand mental health in children
at a deep level. So, they hook up 3 different devices to children with mental health illness, an example could be, a child with, say, 
paranoid schizophrenia. 

Each session is 1 hour long
1) Device 1, is video recording of the child, taken at 60 frames per session
2) Device 2, is heart rate monitor, taken at 5 hz per second, i.e., 5 data points per second
3) Device 3, is EEG recording, 10 herz, 10 data points per second, but this itself has 4 different channels

As you can imagine, there is a lot of data, and this is going to be multiplied by 10 children per day.

We need a scalable pipeline. Unfortunately, with our current setup, (I am using an M2 Macbook)
It will not handle such data, and this problem is best equipped for data centers that have
tons of storage and computing capacity. 

But, what we can do is to use a single snapchat of a single child in that event for example
and feed it through out pipeline infrastructure, for demonstration, learning, and educative purposes.

This is how our pipeline looks

Everything will be containerized using OrbBlast, which makes Dockers much more Faster and even work with M2 Laptops, so, my current macbook has 8gb of ram, Docker begins at 8gb, funny enough. Orbblast fixes this.

Everything will be managed by Airflow, which makes sense, since in production, the data will need to be
scheduled 

1) Automated Python data generation, that generates random data at a single point in time, (A snapshot),

2) Kafka 

3) Spark for parralel processing of the data

4) Storage in S3

Therapy Room
│
├── Video Camera ─────┐
├── Heart Monitor ────┼──> Kafka ──> Spark ──> S3
└── EEG Machine ─────┘