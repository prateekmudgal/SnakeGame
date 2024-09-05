pipeline { //pipeline as code - Jenkinsfile
    agent{
        label "application"
    }

    stages { //collection of your jobs
        stage('Download the source code') { //stage ~=job
            steps {
               git branch: 'main', url: 'https://github.com/prateekmudgal/SnakeGame.git'
               echo "code downloaded succesfully"
            }
        }
        
        stage("Build Docker Image"){
            steps{
                sh "docker build -t gfgwebimg ."
            }
        }
        stage("Deployment"){
            steps{
                sh "docker rm -f webos"
                sh "docker run -dit --name webos -p 5000:5000 gfgwebimg"
            }
        }
    }
}
