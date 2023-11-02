pipeline {
    agent { label "slave1"}
    
    triggers { 
        pollSCM('* * * * *')
    }    

    stages {
        stage('Clone the project ') {
            steps {
                echo 'clone the project'
                git branch: 'main', url: 'https://github.com/manjumunch/petshop.git'
                
            }
        }
        stage('Coping the project') {
            steps {
                echo 'verify the file where it is cloned'
                sh '''pwd'''
                sh '''ls'''
            }
        }
        stage('Deploy to httpd server') {
            steps {
                echo 'coping the file '
                 sh 'scp -i /home/ec2-user/key.pem -r /var/jenkins/workspace/petshop/* ec2-user@43.205.233.196:/var/www/html'
                
            }
        }
        stage('Done and Dusted ') {
            steps {
                echo 'check the deploy'
            }
        }    
    }
}
