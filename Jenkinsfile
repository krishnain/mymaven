pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload_Master')
        {
            steps
            {
                script
                {
                    try
                    {
                         git 'https://github.com/krishnain/mymaven.git'
                    }
                    catch(Exception e1)
                    {
                        
                        mail bcc: '', body: 'Jenkins is unable to download from the remote github', cc: '', from: '', replyTo: '', subject: 'Download Failed', to: 'git.admin@gmail.com'
                        exit(1)
                    }
                }
               
            }
        }
        stage('ContinuousBuild_Master')
        {
            steps
            {
                script
                {
                    try
                    {
                         sh 'mvn package'
                    }
                    catch(Exception e2)
                    {
                        mail bcc: '', body: 'Jenkins is unable to create an artifact from the downloaded code', cc: '', from: '', replyTo: '', subject: 'Build Failed', to: 'dev.team@gmail.com'
                        exit(1)
                    }
                }
               
            }
        }
   }
}
