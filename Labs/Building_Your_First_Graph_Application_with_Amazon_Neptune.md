## Prerequisites

We will be using Amazon SageMaker and AWS CloudFormation to set up infrastructure required for this tutorial. Additionally as part of the setup we will be using IAM to make sure Neptune has appropriate permissions.  

## Setup Instructions

*   Log-in to your AWS account  

*   Launch this cloud formation [stack](https://github.com/wrbaldwin/db-week/blob/master/Labs/neptune-sagemaker-base-stack.json) 

    
## After stack creation

*   Once the stack is created. Go to AWS Console > SageMaker  

*   Open notebook instances from the navigation.  

*   You would notice that a new notebook with name Neptune has been created. Open the Jupyter notebook.  

*   Navigate to neptune > notebooks  

*   Start with 01-Setup

**Note**: Make sure to delete the cloud formation stack after the workshop to delete all associated resources. Go to AWS Console > Cloud Formation in the same region that you created the stack in and delete the stack.


## Web Application (Optional)

We have put together following sample web application that demonstrates how to setup to Neptune, issue gremlin queries and build your application. Please refer to the README for further instructions to setup the application: [neptune-workshop-ui](https://github.com/triggan/neptune-workshop-ui)
