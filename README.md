

## Setup

### 1. In your Git Account:
1. Create a new repository. 
2. Create a Personal Access Token  
   Settings > Developer settings > Personal access tokens  
   Generate the token and copy it.  

### 2. In your AWS Account:  
1. Create the Setup Stack using setup.yaml template.  
   Inform your Personal Access Token as MyGitToken parameter  
2. Create the Pipeline Stack using TemplatePipeline.yaml template  
   Note: Use Setup parameter = true  
3. Upload the TemplatePipeline.yaml file to S3 Bucket.  
   You can get the BucketName in the Output section for Setup Stack.   

### 3. Back to your Git Account:  
1. In your repository console create the Webhook:  
   Go to: Settings > Webhooks > Add webhook.  
   Payload URL: Insert the Endpoint Parameter shown in the Output section for Setup Stack.   
   Content Type: application/json. 
   Which events would you like to trigger this webhook? Click Let me select individual events.”  
   Select:   
    - Branch or tag creation. 
    - Branch or tag deletion. 
   Remove:  
    - Pushes. 
   Click Add Webhooks. 


### 4. How to test. 
1. Validate if the pipeline for the master branch runs successfully. 
2. In your GitHub repo, create a new branch called “develop” and check if a new CloudFormation stack is created.  
   This new CloudFormation Stack contains the pipeline for develop branch.  
   Check if this new pipeline runs successfully.   
3. In your Git repo, delete the develop branch  and check if that CloudFormation stack is deleted.  
        
