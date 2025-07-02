pipeline {
    agent any

    environment {
        REPO = 'https://github.com/hars-hitha/DevOps_Project.git'
        QA_HOST = '172.31.36.74'          
        QA_USER = 'sree'
        IMAGE = 'myhtmlsite'
        PORT = '8080'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: "${REPO}"
            }
        }

        stage('Install Docker on QA') {
            steps {
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m apt -a 'name=docker.io state=present update_cache=yes' --become
                """
            }
        }

        stage('Copy Project to QA') {
            steps {
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m synchronize -a 'src=./ dest=/home/${QA_USER}/DevOps_Project delete=yes' --become
                """
            }
        }

        stage('Build Docker Image on QA') {
            steps {
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m shell -a 'cd /home/${QA_USER}/DevOps_Project && docker build -t ${IMAGE} .' --become
                """
            }
        }

        stage('Run Docker Container on QA') {
            steps {
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m shell -a 'docker rm -f webapp || true && docker run -d --name webapp -p ${PORT}:80 ${IMAGE}' --become
                """
            }
        }
    }
}
