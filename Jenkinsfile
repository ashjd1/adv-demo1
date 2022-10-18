pipeline 
{
    agent any
    pipeline {
    agent any
    stages {
        stage('only') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'docker-login', 
                        usernameVariable: 'ashjd', 
                        passwordVariable: 'dckr_pat_Bd34xMJ2z1I24rgENk3kqOV3mDo'
                        )]) {
                    sh '''
                        echo "The username is: ${ashjd}"
                        echo "The password is : ${dckr_pat_Bd34xMJ2z1I24rgENk3kqOV3mDo}"
                    '''
                }
            }
        }
    }
}
    stages
    {
        stage('Build Docker Image')
        {
           steps
           {
                script
                {
                    sh 'docker build -t ashjd/ashu-jenkins1 .'
                }
            }
        }
         stage('docker login1')
        {
            steps
            {     
                sh 'docker login -u $secret_USR -p $secret_PSW'
                sh 'echo $secret_PSW | docker login -u $secret_USR --password-stdin'
             }
        }
        stage('Push image to Hub')
        {
            steps
            {     
                sh 'docker push ashjd/ashu-jenkins1'
            }          
        }
        stage('Pull image from hub')
        {
            steps
            {
                script
                {
     
                    sh 'docker pull ashjd/ashu-jenkins1'
                }
            }
        }
        
        stage('start container')
        {
            steps
            {
                script
                {
                   sh 'docker run -p 8082:80 --name jenkins1 ashjd/ashu-jenkins1'
                    sh 'docker rm jenkins1'
                }
            }
        }
    }
}
