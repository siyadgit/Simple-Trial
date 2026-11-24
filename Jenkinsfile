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
                git clone https://github.com/Jibin-G-Jiji/portfolio-git.git
                ls -la
                '''
                stash name:'webpage', includes:'portfolio-git/**'
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
                sudo cp -r portfolio-git/* /var/www/html/
                ls -la /var/www/html/
                '''
            }
        }
    }
}
