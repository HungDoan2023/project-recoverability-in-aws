# Project: Recoverability In AWS
## Initial Steps
I. Download and Run Vpc.yaml file in CloudFormation
[Download and Run VPC yaml file](https://github.com/udacity/nd063-c2-design-for-availability-resilience-reliability-replacement-project-starter-template/blob/master/cloudformation/vpc.yaml)

II. For building the VPC. Do some the following steps:
1. Services -> CloudFormation
2. Create stack “With new resources (standard)”
3. Template is ready
4. Upload a template file
5. Click “Choose file” button
6. Select provided YAML file
7. Next <br>
![Cloudformation Create](./screenshots/cloudformationcreate.png)
<br>
8. Fill in Stack name
9. Name the VPC
10. Update the CIDR blocks
11. Click Next
12. Click Next again
13. Click Create stack
14. Wait for the stack to build out. Refresh until status becomes “CREATE_COMPLETE”
15. Observe the “Outputs” tab for the created IDs. These will be used later.
<br>
![Cloudformation Output](./screenshots/cloudformationoutputs.png)
<br>

## Part 1 Data Durability And Recovery
#### Highly durable RDS Database
1. Primary VPC<br>
![Primary VPC](./screenshots/part1/primary_Vpc.PNG)<br>

2. Secondary VPC<br>
![Secondary VPC](./screenshots/part1/secondary_Vpc.PNG)<br>

3. Primary DB Config<br>
![Primary DB Config](./screenshots/part1/primaryDB_config.PNG)<br>

4. Secondary DB Config<br>
![Secondary DB Config](./screenshots/part1/secondaryDB_config.PNG)<br>

5. Primary DB SubnetsGroup<br>
![Primary DB SubnetsGroup](./screenshots/part1/primaryDB_subnetgroup.PNG)<br>

6. Secondary DB SubnetsGroup<br>
![Secondary DB SubnetsGroup](./screenshots/part1/secondaryDB_subnetgroup.PNG)<br>

7. Primary VPC Subnets<br>
![Primary VPC Subnets](./screenshots/part1/primaryVpc_subnets.PNG)<br>

8. Secondary VPC Subnets<br>
![Secondary VPC Subnets](./screenshots/part1/secondaryVpc_subnets.PNG)<br>

9. Primary Subnet Routing<br>
![Primary Subnet Routing](./screenshots/part1/primary_subnet_routing.PNG)<br>

10. Secondary Subnet Routing<br>
![Secondary Subnet Routing](./screenshots/part1/secondary_subnet_routing.PNG)<br>

#### Availability Estimate<br>
[See more detail at estimation link](./estimates.txt)<br>

#### Demonstrate normal usage<br>
[See more detail at log primary link](./logs/log_primary.txt)<br>

![Log primary](./screenshots/part1/log_primary.PNG)<br>

#### Monitor database<br>
1. Create an EC2 keypair in the region
2. Launch an Amazon Linux EC2 instance in the standby region. Configure the instance to use the VPC's public subnet and security group ("UDARR-Application").
3. SSH to the instance and connect to the read replica database.
4. Verify if you are not able to insert data into the database but are able to read from the database.
5. You have now demonstrated that you can only read from the read replica database.

Monitoring Connections<br>
![Monitoring Connections](./screenshots/part1/monitoring_connections.PNG)<br>

Monitoring Replication<br>
![Monitoring Replication](./screenshots/part1/monitoring_replication.PNG)<br>

## Part 2: Failover And Recovery
#### Failover And Recovery
![Log before promotion](./screenshots/part2/log_rr_before_promotion.PNG)<br>
![Screenshot before promotion](./screenshots/part2/rr_before_promotion.PNG)<br>


6. Promote the read replica
7. Verify that if you are able to insert data into and read from the read replica database.
8. You have now demonstrated that you can read and write the promoted database in the standby region.

![Log after promotion](./screenshots/part2/log_rr_after_promotion.PNG)<br>
![Screenshot after promotion](./screenshots/part2/rr_after_promotion.PNG)<br>

## Part 3: Web Resiliency
#### Website Resiliency

S3 Bucket<br>
![S3 Bucket](./screenshots/part3/s3_bucket.PNG)<br>

S3 Original<br>
![S3 Original](./screenshots/part3/s3_original.PNG)<br>

S3 Season<br>
![S3 Season](./screenshots/part3/s3_season.PNG)<br>

S3 Season Revert<br>
![S3 Season Revert](./screenshots/part3/s3_season_revert.PNG)<br>


S3 Delete Marker<br>
![S3 Marker](./screenshots/part3/s3_delete_marker.PNG)<br>

S3 Deletion<br>
![S3 Deletion](./screenshots/part3/s3_deletion.PNG)<br>


S3 Delete Revert<br>
![S3 Delete Revert](./screenshots/part3/s3_delete_revert.PNG)<br>