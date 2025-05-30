# VRAG

## Solution Overview:

## Architecture:
![Architecture Diagram](assets/architecture.png "Architecture Diagram")
### Deployment steps:
1. Enable [nova reels](https://us-east-1.console.aws.amazon.com/bedrock/home?region=us-east-1#/modelaccess) model via the console. Follow this [link](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access-modify.html) for more info.
2. Deploy solution via CloudFormation template by clicking one of the buttons below: 

| Region                | Launch Template|
|-----------------------|-------------------|
 | US East (N. Virginia) | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=my-stack&templateURL=...)|
Note: Nova Reels is only supported in us-east-1
3. Select the stack in [CloudFormation](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks?filteringText=&filteringStatus=active&viewNested=true). Go to the `Outputs` tab and click on the link next to `NotebookInstanceUrl`. 


### Network Infrastructure
- VPC with public and private subnets
- NAT Gateway for outbound internet access from private subnets
- Internet Gateway for public subnet
- VPC Flow Logs for network monitoring

### Compute Resources
- SageMaker Notebook Instance in a private subnet
- Custom lifecycle configuration for notebook setup
- Security groups with restricted access

### Storage
- S3 bucket for data storage with versioning enabled
- Separate logging bucket for access logs
- Server-side encryption (AES-256)
- Bucket policies for secure access

### Search Infrastructure
- OpenSearch Serverless collection optimized for vector search
- Security policies for encryption and network access
- Access policies for fine-grained control

### Security
- KMS key for notebook encryption
- IAM roles with least privilege access
- VPC endpoint for secure OpenSearch access
- Private subnet placement for notebook instance

## Project Structure
```
.
├── README.md
├── assets
│   ├── architecture.png                                      # Architecture diagram
│   ├── model_access.png
│   └── select_nova_reel.png
├── _00_image_processing.ipynb                            # Jupyter Notebooks
├── _01_oss_ingestion.ipynb
├── _02_video_gen_text_only.ipynb
├── _03_video_gen_text_image.ipynb
├── _04_video_gen_multi.ipynb
├── _05_inpainting.ipynb
├── _06_video_gen_inpainting.ipynb
├── cft-video-generation-blog.yml                         # Cloudformation template
├── images/                                               # Sample images for demo purposes 
└── requirements.txt                                      # Dependencies
```




## Authors and Reviewers
 * Nick Biso, Machine Learning Engineer - Amazon Web Services Inc.
 * Vishwa Gupta, Senior Data Architect  - Amazon Web Services Inc.
 * Madhunika Reddy Mikkili, Data & ML Engineer - Amazon Web Services Inc.
 * Seif Elharaki, Machine Learning Engineer - Amazon Web Services Inc.
 * Shuai Cao, Data Science Manager - Amazon Web Services Inc.
