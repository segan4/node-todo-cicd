pipeline {
    agent none // This means that the pipeline will not run on any agent by default
    stages {
        stage('Clone') {
            agent { label 'Agent-1' } // This means that this stage will run on an agent with the label 'agent'
            steps {
                echo "cloning the repository"
                git 'https://github.com/segan4/node-todo-cicd.git' // This will clone the GitHub repository to the agent's workspace
            }
        }
        stage('Build') {
            agent { label 'Agent-1' }
            steps {
                echo "Building the image"
                sh 'docker build -t todo-app .'
            }
        }
        stage('Deploy') {
            steps {
                agent { label 'Agent-1' } 
                echo "Deploying todo app"
                sh 'docker-compose down'
                sh 'docker-compose up -d'
            }
        }
    }
}
