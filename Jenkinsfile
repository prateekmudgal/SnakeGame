pipeline { 
    agent { 
        label 'application' 
    }

    stages { 
        stage('Download the source code') { 
            steps { 
                git branch: 'main', url: 'https://github.com/prateekmudgal/SnakeGame.git'
                echo 'Code downloaded successfully'
            } 
        }

        stage('Build Docker Image') { 
            steps { 
                sh 'docker build -t snakegame .' 
            } 
        }

        stage('Deployment') { 
            steps { 
                sh 'docker rm -f oriserve || true' // Added '|| true' to prevent failure if container doesn't exist
                sh 'docker run -dit --name oriserve -p 5000:5000 snakegame' 
            } 
        }
    }
}
