pipeline
{
    agent any
    stages
    {
        stage ('scm checkout')
        {
            steps 
            {
                git branch: 'master', url: 'https://github.com/kdadhikari/Cloud-Formation'
            }
        }
        stage ('create working dir')
        {
            input
            {
                meaasge 'please provide stack name'
                parameters {string(name:'stackname', defaultValue: 'stack name', description: 'stack name for EC2 instance')}
            }
            steps 
            {
                withAWS(credentials: 'ec2', region: 'us-east-1') 
                {
                    sh "aws cloudformation create-stack --stack-name ${stackname} --template-body file://ec2_inst.json --region 'us-east-1'"
		            }                
            }
        }
    }
}    
