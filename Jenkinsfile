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
                message 'please provide stack name'
                parameters {string(name:'stackname', defaultValue: 'stack', description: 'stack name for EC2 instance')}
            }
            steps 
            {
                withAWS(credentials: 'ec2', region: 'us-east-1') 
                {
                    sh "aws cloudformation create-stack --stack-name EC2-instance --template-body file://ec2_inst.json --region 'us-east-1'"
		            }                
            }
        }
    }
}    
