# Definistion & Keywords

## Pub/Sub

Pub/Sub is a fully-managed real-time messaging service that allows you to send and receive messages between independent applications.

- queue

## BigQuery

BigQuery is Google Cloud's fully managed, petabyte-scale, and cost-effective analytics data warehouse that lets you run analytics over vast amounts of data in near real time. With BigQuery, there's no infrastructure to set up or manage, letting you focus on finding meaningful insights using GoogleSQL and taking advantage of flexible pricing models across on-demand and flat-rate options.

- data warehouse, SQL tools, analytical applications

## Cloud SQL

> Cloud SQL offers a fully-managed database service for MySQL, PostgreSQL, and SQL Server
reducing your overall cost of operations and freeing up teams to focus on innovation.

- mid-size, region, transaction processing, relational database

## Spanner

> Spanner is an always-on, globally consistent database with virtually unlimited scale
Build intelligent applications with a single database that brings together relational, graph, key-value, and search functionalities.
The elimination of maintenance windows ensures uninterrupted service for mission-critical applications.

- transaction processing, global, multiple regions

## Bigtable

> Bigtable is a fully managed, wide-column NoSQL database that offers low latency and replication for high availability.
To use Bigtable, create an instance and then set up your development environment to access Bigtable so that you can add data and monitor performance.

- Iot application, write large volumes, low latency, HBase

## Memorystore

> Memorystore for Redis Cluster is a fully-managed, horizontally scalable Redis Cluster service for workloads that demand the lowest possible latencies. Create an instance and connect using an open-source Redis cluster client library.

## Cloud RUN

> A service exposes a unique endpoint and automatically scales the underlying infrastructure to handle incoming requests.
Deploy a container image, source code or a function to create a service.
Develop and deploy highly scalable containerized applications on a fully managed serverless platform

## Cloud build

> Cloud Build, Google Cloud’s continuous integration (CI) and continuous delivery (CD) platform, lets you build software quickly across all languages.Get complete control over defining custom workflows for building, testing, and deploying across multiple environments such as VMs, serverless, Kubernetes, or Firebase.

## Cloud functions

Event-driven serverless functions
Run your code with zero server management using scalable pay-as-you-go functions as a service (FaaS)

> fast quality checks

## Datastore/Firestore

> Firestore is a NoSQL document database built for automatic scaling, high performance, and ease of application development.
To use Firestore, create one or more databases. Firestore databases come in two modes: Native mode and Datastore mode.

## App Engine

Managed app platform
Build and deploy apps on a fully managed, highly scalable platform without having to manage underlying infrastructure

## Load Balancer

![Load Balancer](/images/lb-product-tree.svg)

## Cloud Data Fsuion

## VPC

- VPC accross multiple organistations => Network peering

## Shield VM

- rootkit, kernel level malware

## Sole-tenant

Only VMs from the same project will run on the node

## GKE

- ClusterIP,

## Cloud CDN

The Google Cloud Content Delivery Network uses Google's global edge network to serve content closer to users, which accelerates your websites and applications.

## Cloud monitoring

## Cloud Dataproc

## Image families

Public image families
Compute Engine provides image families to help you ensure that your automation systems can reference the latest images. As an administrator, you can group a set of images as an image family. Then users of the images only have to keep track of the image-family name, rather than an exact image name. Because image names must be unique, image-build pipelines often create image names with information encoded in them, such as the application name, date, and version, for example, my-application-v3-20210101. In automation tools, you can reference the image family name instead of having to update the image name at intervals. Using image families ensures that you always access the latest image in the family, for example, my-application.

Custom image families
You can create custom image families for your custom images. The image family points to the most recent image that you used to create the image family. To roll an image family back to a previous image version, you can deprecate the most recent image in that family (as long as the previous image is not deprecated).
