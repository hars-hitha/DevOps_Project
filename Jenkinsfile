pipeline {
    agent any
    stages {
        stage('Cloning Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/hars-hitha/DevOps_Project.git'
            }
        }
        stage('Echo') {
            steps {
                echo 'Pipeline is working!'
            }
        }
    }
}
