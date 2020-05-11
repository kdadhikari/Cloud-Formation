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
            steps 
            {
                withAWS(credentials: 'ec2', region: 'us-east-1') 
                {
                    sh 'aws ec2 run-instances   --image-id ami-0915e09cc7ceee3ab --key-name kdkey --security-groups default --instance-type t2.micro --placement AvailabilityZone=us-east-1a --block-device-mappings DeviceName=/dev/sdh,Ebs={VolumeSize=100} --count 1'
                }                
            }
        }
    }
}    
