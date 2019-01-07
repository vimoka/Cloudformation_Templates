# Cloudformation_Templates : Template for configuring and hosting a sample Wordpress Website 
The template includes the following sections:

PARAMETER SECTION - TO dynamically pass values to provision resources to help build infrastructure:
#below are the parameter sections implemented:
1. Environment size -  (small, medium, large)
2. Database Name
3. DataBase User
4. DataBase Password

MAPPINGS SECTION - Mappings are kind of hashmaps that are used to provision the desired infrastructure based on the key-value pairs we provide
#below are the mappings implemented:
1. Region Selection - referring to the key, which is region name and mapping it with the value we provide to provision AMI-ID 
2. Environment size of the server - for the type of instance to be selected based on environment size parameter 
3. Database instance class - the type of the DBInstance Class to be selected based on the environment size

RESOURCES SECTION - To provision the required resources 
EC2 - server for hosting the wordpress website
DataBase - Backend database for the wordpress website that is being hosted 
S3 -To store the Cloudformation template

USERDATA PROPERTY - Base64 encoded script to configure the ec2 instance
METADATA PROPERTY - Script that contain the following:
1. configsets  - to install and configure the wordpress website 
2. hup and hooks config files - which helps handle any updates in the instance configuration
3. parameter injection - to inject the database name, user and password 

RESOURCE SIGNAL - this helper script signals cloudformation when the EC2 instance have been successfully created or updated
