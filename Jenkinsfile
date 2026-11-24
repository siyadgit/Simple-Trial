pipeline{
    agent none
    stages{
        stage('build'){
            agent{
                label 'build'
            }
            steps{
                deleteDir()
                sh '''
                git clone https://github.com/siyadgit/Simple-Trial.git
                ls -la
                '''
                stash name:'webpage', includes:'Simple-Trial/**'
            }
        }
        stage('deploy'){
            agent{
                label 'deploynode'
            }
            steps{
                deleteDir()
                unstash 'webpage'
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r Simple-Trial/* /var/www/html/
                ls -la /var/www/html/
                '''
            }
        }
    }
}
