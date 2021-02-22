####################################################################


ASSIGNMENT SOLUTION

1. BASIC CODE FROM THE REPO 

Code is pulled and pushed on my repo which will be used by pipeline for all the automation

Its stored in repo https://github.com/etivvenkata/etivvenkata.github.io


2. Circle CI pipeline is created with the following stages, config.yml file is also attached. 

 -- Download C code
 -- Compile the code
 -- Create Debian Package
 -- Execute and push the output to index.html
 -- Host the output on web url

3. Website is hosted on https://etivvenkata.github.io/  (link for static page)

4. Typical CI/CD flows look like as below:


 -- Developer commits the code on GIT repo https://github.com/etivvenkata/etivvenkata.github.io

 -- Circle CI pipeline created on https://app.circleci.com/pipelines/github/etivvenkata/etivvenkata.github.io will be triggered.

 -- It will download the code, compile, create package, push to index and host on url https://etivvenkata.github.io/

##############################################################################################


8. Scanning Vulnerabilites 

 -- For the C code, CircleCI pipeline will be integrated with tools like CODESONAR which will scan the code for vulnerabilites

 So there will be separate pipeline for the code quality scanning and testing as we need to ensure only high quality code is getting committed.


  Developer --->  Create new branch ---- > Commit code on new branch ----> Raise PR to merge with main--->Webhook integration will trigger CircleCI/Jenkins

pipeline --- > Circle CI gives success --- > PR request approved --- > Deployment pipeline (mentioned on above will be triggered)


 Testing pipeline will have following stages

 -- Download the C code on workspace
 -- Scann the code with CODESONAR or any other tool
 -- Compile and create deb package
 -- Analyze and scan the deb package with tools like Debian CVE Scanner 


######################################################################################################

9. Data transfer security 

  -- For deployment we can use the AWS services like Ec2 
  -- Will enabled encryption at rest, so all the volumes will be be fully encrypted. 

  -- SSL will be enabled with AWS KMS service (can use CMK - Customer Managed Key) as well for enhanced security. 

  -- We can enabled SSL at all stages like data getting downloaded, pushed to artifactory, can even go for mutual SSL.
 
  -- We can consider AWS Codepipeline and CodeCommit which is secured as per the design
 --  No ports will be opened for end user, rather pipeline will only be able to access repository, EC2, end user will get the url directly.
 -- Service accounts will be used in entire process with complex, random password, managed by AWS Secret manager, or Cyberark or any password solution.

 -- No individual will hold the password, it will be retrieved by pipeline at run time dynamically, auto rotation will also be enabled.


