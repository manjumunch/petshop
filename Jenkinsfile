pipeline {
    agent { label "slave1"}
    
    triggers { 
        pollSCM('* * * * *')
    }    

    stages {
        stage('Clone the project ') {
            steps {
                echo 'clone the project'
                git branch: 'main', url: 'https://github.com/manjumunch/jewelshop.git'
                
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
                 sh 'scp -i /home/ec2-user/key.pem -r /var/jenkins/workspace/goldshop/* ec2-user@13.233.113.143:/var/www/html'
                
            }
        }
        stage('Stage4_dummy') {
            steps {
                echo 'check the deploy'
            }
        }    
    }
}
